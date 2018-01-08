---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# カスタム分類器の作成

『入門のチュートリアル』で画像を分類した後は、カスタム分類器 (または、モデル) をトレーニングして作成する準備が整っています。カスタム分類器を使用すると、{{site.data.keyword.visualrecognitionshort}} サービスをトレーニングして、ビジネス・ニーズに適合するように画像を分類できます。
{: shortdesc}

## ステップ 1: 資格情報をコピーする
{: #copy-credentials}

『入門のチュートリアル』でコピーした資格情報を使用します。サービス・インスタンスを作成していない場合は、『[始めに](/docs/services/visual-recognition/getting-started.html#prerequisites)』セクションの手順を実行してください。

## ステップ 2: カスタム分類器を作成する
{: #create}

{{site.data.keyword.visualrecognitionshort}} では、ユーザーがアップロードしたサンプル画像から学習して、新しい多面的な分類器を作成できます。各サンプル・ファイルは、その呼び出しに含まれる他のファイルに突き合わせてトレーニングされ、正例がクラスとして保管されます。これらのクラスがグループ化されて、単一の分類器を定義し、それぞれ独自のスコアを返します。負例のファイルはクラスとして保管されません。

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a>、および <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> の各サンプル・トレーニング・ファイルをダウンロードします。
1.  以下のコマンドを使用して、`POST /v3/classifiers` メソッドを呼び出します。このコマンドは、トレーニング・データをアップロードし、`dogs` 分類器を作成します。
    - `{api-key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。
    - `{class}_positive_examples` のロケーションを変更して、.zip ファイルを保存した場所を指すようにします。

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    正例のファイル名には、サフィックス `_positive_examples` が必要です。この例では、ファイル名は `beagle_positive_examples`、`goldenretriever_positive_examples`、および `husky_positive_examples` です。プレフィックス (beagle、goldenretriever、および husky) は、クラスの名前として返されます。  {:tip }

    応答には新しい分類器 ID と状況が含まれています。以下に例を示します。

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

1.  状況が `ready` と表示されるまで、トレーニングの状況を定期的に確認します。トレーニングは即時に開始され、これが終了してからでないと、分類器を照会することはできません。`{api  key}` と `{classifier_id}` を、ご使用の情報に置き換えてください。

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## ステップ 3: 既存のカスタム分類器を更新する

無料の API キーを使用して、カスタム分類器を更新することはできません。無料のキーをお持ちの場合は、標準プランにアップグレードできます。詳しくは、[プランの変更](https://console.bluemix.net/docs/pricing/changing_plan.html)を参照してください。
{: tip}

分類器にクラスを追加するか、既存のクラスに画像を追加することで、カスタム分類器を更新できます。ここでは、分類できる犬のタイプに *Dalmatian* クラスを追加することにより、ステップ 2 で作成した分類器を改善します。「dogs」分類器に設定された負例に、猫の画像を追加することもできます。

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> および <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> の各サンプル・トレーニング・ファイルをダウンロードします。
1.  以下の cURL コマンドを使用して、`POST /v3/classifiers/{classifier_id}` メソッドを呼び出します。このコマンドは、トレーニング・データをアップロードして、分類器「dogs\_1941945966」を更新します。
    - `{api-key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。
    - `{classifier_id}` を、更新する分類器の ID に置き換えます。
    - `{class}_positive_examples` のロケーションを変更して、.zip ファイルを保存した場所を指すようにします。

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    既存の「dogs」分類器は、同じ classifier_id を持つリトレーニング分類器によって置き換えられます。応答には、新しいクラスのセットと現在の状況がリストされます。以下に例を示します。

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    トレーニングは即時に開始されます。新しい分類器が使用可能になると、状況は `ready` に変更されます。

現在の状況が `ready` 状態になるまでは、別のリトレーニング要求を出さないでください。特定の分類器をリトレーニングするために要求を複数回出しても、有効になるリトレーニングは 1 つのみです。`retrained` と呼ばれるタイム・スタンプに、分類器のリトレーニングが完了した最新時刻が表示されます。分類器のリトレーニング中に `/classify` メソッドを呼び出すと、その分類器の古い定義が使用されます。{: tip}
1.  状況が `ready` と表示されるまで、トレーニングの状況を定期的に確認します。`{api  key}` と `{classifier_id}` を、ご使用の情報に置き換えてください。

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## ステップ 4: カスタム分類器を使用して画像を分類する
{: #classify}

新しい分類器が作動可能になったら、それを呼び出して、パフォーマンスを確認します。

1.  `myparams.json` と呼ばれる JSON ファイルを作成します。このファイルには、新しい分類器と一般モデル分類器 (`default` classifier_id を使用) の両方の `classifier_id` など、呼び出しのパラメーターを含めます。サンプル JSON ファイルは、以下のようになります。

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> をダウンロードします。
1.  `POST /v3/classify` メソッドを使用して、カスタム分類器をテストします。以下の例は、`dogs.jpg` 画像を「dogs\_1941945966」分類器に突き合わせて分類します。
    - `{api-key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    組み込みの一般モデルにのみ突き合わせて分類するには、`parameters` パラメーターを省略します。
    {: tip}

    応答には、分類器、そのクラス、および各クラスのスコアが含まれます。スコアは 0 から 1 までの範囲で、スコアが高いほど相関性が大きいことを示します。`/v3/classify` 呼び出しは、デフォルトでは、高いスコアのクラスが識別された場合、低いスコアのクラスを省略します。呼び出しの `threshold` パラメーターに浮動小数点値を指定することにより、表示する最小スコアを設定できます。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  結果を確認します。

これで完了です。{{site.data.keyword.visualrecognitionshort}} を使用して、カスタム分類器の作成、トレーニング、および照会を行いました。

### カスタム分類器を削除する

クリーンなインスタンスを使用してアプリケーションの開発を始めるために、カスタム分類器を削除することができます。

分類器を削除するには、`DELETE /v3/classifiers/{classifier_id}` メソッドを呼び出します。`{api_key)` と `classifier_id` を、ご使用の情報に置き換えてください。

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## 次のステップ

カスタム分類器の使用法を基本的に理解できましたので、さらに詳しく検討することができます。

- [Best practices for custom classifiers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window} の詳細を学習します
- [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} で、API に関する説明を読みます

### 帰属
{: #attributions}

このページで使用された画像はすべて Flikr から提供されたもので、[Creative Commons Attribution 2.0 ライセンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} に基づいて使用されています。これらの画像に変更は加えられていません。

