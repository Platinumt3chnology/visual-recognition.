---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# カスタム・モデルの作成
{: #tutorial-custom-classifier}

『入門チュートリアル』で画像を分析した後は、カスタム・モデルをトレーニングして作成する準備が整っています。カスタム・モデルを使用すると、{{site.data.keyword.visualrecognitionshort}} サービスをトレーニングして、ビジネス・ニーズに適合するように画像を分類できます。
{: shortdesc}

## ステップ 1: 資格情報をコピーする
{: #copy-credentials}

『入門のチュートリアル』でコピーした資格情報を使用します。 サービス・インスタンスを作成していない場合は、『[始めに](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites)』セクションの手順を実行してください。

## ステップ 2: カスタム・モデルを作成する
{: #create}

{{site.data.keyword.visualrecognitionshort}} では、ユーザーがアップロードしたサンプル画像から学習して、新しい多面的なモデルを作成できます。 各サンプル・ファイルは、その呼び出しに含まれる他のファイルに突き合わせてトレーニングされ、正例がクラスとして保管されます。 これらのクラスがグループ化されて、単一のモデルを定義し、それぞれ独自のスコアを返します。 負例のファイルはクラスとして保管されません。

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a>、および <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> の各サンプル・トレーニング・ファイルをダウンロードします。
1.  以下のコマンドを使用して、`POST /v3/classifiers` メソッドを呼び出します。このコマンドは、トレーニング・データをアップロードし、`dogs` カスタム・モデルを作成します。
    - `{your_api_key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。
    - `{class}_positive_examples` のロケーションを変更して、.zip ファイルを保存した場所を指すようにします。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    正例のファイル名には、サフィックス `_positive_examples` が必要です。 この例では、ファイル名は `beagle_positive_examples`、`goldenretriever_positive_examples`、および `husky_positive_examples` です。 プレフィックス (beagle、goldenretriever、および husky) は、クラスの名前として返されます。
    {:tip }

    応答には新しい分類器 ID と状況が含まれています。以下に例を示します。

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
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
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  状況が `ready` と表示されるまで、トレーニングの状況を定期的に確認します。 トレーニングは即時に開始され、これが終了してからでないと、モデルを照会することはできません。 `{your_api_key}` と `{classifier_id}` を、ご使用の情報に置き換えてください。

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## ステップ 3: 既存のカスタム・モデルを更新する
{: #tutorial-custom-classifier-update}

モデルにクラスを追加するか、既存のクラスに画像を追加することで、カスタム・モデルを更新できます。 ここでは、分類できる犬のタイプに *Dalmatian* クラスを追加することにより、ステップ 2 で作成したモデルを改善します。 「dogs」カスタム・モデルに設定された負例に、猫の画像を追加することもできます。

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> および <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> の各サンプル・トレーニング・ファイルをダウンロードします。
1.  以下の cURL コマンドを使用して、`POST /v3/classifiers/{classifier_id}` メソッドを呼び出します。このコマンドは、トレーニング・データをアップロードして、カスタム・モデル「dogs\_1941945966」を更新します。
    - `{your_api_key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。
    - `{classifier_id}` を、更新するカスタム・モデルの ID に置き換えます。
    - `{class}_positive_examples` のロケーションを変更して、.zip ファイルを保存した場所を指すようにします。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    既存の「dogs」カスタム・モデルは、同じ classifier_id を持つリトレーニング分類器によって置き換えられます。 応答には、新しいクラスのセットと現在の状況がリストされます。 以下に例を示します。

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    トレーニングは即時に開始されます。 新しい分類器が使用可能になると、状況は `ready` に変更されます。

    現在の状況が `ready` 状態になるまでは、別のリトレーニング要求を出さないでください。 特定のモデルをリトレーニングするために要求を複数回出しても、有効になるリトレーニングは 1 つのみです。 `updated` というタイム・スタンプに、モデルの最終更新日時が示されます。モデルのリトレーニング中に `/classify` メソッドを呼び出すと、そのモデルの古い定義が使用されます。
    {: tip}
1.  状況が `ready` と表示されるまで、トレーニングの状況を定期的に確認します。 `{your_api_key}` と `{classifier_id}` を、ご使用の情報に置き換えてください。

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## ステップ 4: カスタム・モデルを使用して画像を分類する
{: #tutorial-custom-classifier-classify}

新しいモデルが作動可能になったら、それを呼び出して、パフォーマンスを確認します。

1.  <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> をダウンロードします。
1.  `POST /v3/classify` メソッドを使用して、カスタム・モデルをテストします。 以下の例では、`dogs.jpg` 画像を「dogs\_1941945966」カスタム・モデルおよび組み込みの `default` 一般モデルの両方に突き合わせて分類します。
    - `{your_api_key}` を、最初のステップでコピーしたサービス資格情報に置き換えます。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    組み込みの一般モデルにのみ突き合わせて分類するには、`classifier_ids` パラメーターを省略します。
    {: tip}

    応答には、分類器 (モデル)、そのクラス、および各クラスのスコアが含まれます。 スコアは 0 から 1 までの範囲で、スコアが高いほど相関性が大きいことを示します。 `/v3/classify` 呼び出しは、デフォルトでは、高いスコアのクラスが識別された場合、低いスコアのクラスを省略します。 呼び出しの `threshold` パラメーターに浮動小数点値を指定することにより、表示する最小スコアを設定できます。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  結果を確認します。

これで完了です。 {{site.data.keyword.visualrecognitionshort}} を使用して、カスタム・モデルの作成、トレーニング、および照会を行いました。

### カスタム・モデルを削除する
{: #tutorial-custom-classifier-delete}

クリーンなインスタンスを使用してアプリケーションの開発を始めるために、カスタム・モデルを削除することができます。

モデルを削除するには、`DELETE /v3/classifiers/{classifier_id}` メソッドを呼び出します。 `{your_api_key)` と `classifier_id` を、ご使用の情報に置き換えてください。

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## 次のステップ
{: #tutorial-custom-classifier-next-steps}

カスタム・モデルの使用法を基本的に理解できましたので、さらに詳しく検討することができます。

- [Best practices for custom classifiers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window} の詳細を学習します
- API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition){: new_window} を参照してください。

### 帰属
{: #tutorial-custom-classifier-attributions}

このページで使用された画像はすべて Flikr から提供されたもので、[Creative Commons Attribution 2.0 ライセンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} に基づいて使用されています。 これらの画像に変更は加えられていません。
