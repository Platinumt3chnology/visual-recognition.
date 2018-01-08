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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 入門チュートリアル

このチュートリアルでは、{{site.data.keyword.visualrecognitionfull}} でいくつかの組み込み分類器を使用してイメージを分類し、次にイメージ内の顔を検出する方法についてご案内します。
{: shortdesc}

## 始めに
{: #prerequisites}

- 以下のようにして、サービスのインスタンスを作成します。
    - {: download} これが表示されている場合、サービス・インスタンスは作成されました。次に、資格情報を取得します。
    - 以下のようにして、サービスからプロジェクトを作成します。
        1.  {{site.data.keyword.watson}} Developer Console の『[サービス (Services) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/developer/watson/services){: new_window}』ページにアクセスします。
        1.  {{site.data.keyword.visualrecognitionshort}} を選択し、**「サービスの追加」**をクリックし、無料の {{site.data.keyword.Bluemix_notm}} アカウントに登録するか、ログインします。
        1.  プロジェクト名として `vision-tutorial` を入力し、**「プロジェクトの作成 (Create Project)」**をクリックします。
- 以下のようにして、サービス・インスタンスに認証する資格情報をコピーします。
    - {: download} (今表示している) サービス・ダッシュボードから、以下のようにします。
        1.  **「サービス資格情報」**タブをクリックします。
        1.  **「アクション」**の下の**「資格情報の表示」**をクリックします。
        1.  api-key 値をコピーします。
        {: download}
    - Developer Console の**「vision-tutorial」**プロジェクトから、`"visual_recognition"` の `api-key` 値を、**「資格情報」**セクションからコピーします。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}} を使用している場合は、カタログの『[{{site.data.keyword.visualrecognitionshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window}』ページからサービス・インスタンスを作成します。サービス資格情報の検出方法について詳しくは、『[Service credentials for Watson services![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}』を参照してください。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## ステップ 1: イメージの分類
{: #classify}

1.  サンプルの <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> イメージをダウンロードします。
1.  以下のコマンドを実行して、イメージをアップロードし、それをすべての組み込み分類器で分類します。
    - `{api-key}` を、前にコピーしたサービス資格情報に置き換えます。
    - images\_file ロケーションを変更して、画像を保存した場所を指すようにします。

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    {{site.data.keyword.Bluemix_notm}} Dedicated を使用している場合、ここに指定されている `gateway-a.watsonplatform.net` エンドポイントは、ご使用のサービス・エンドポイントでない可能性があります。サービス・ダッシュボードの**「サービス資格情報」**ページで `url` を確認してください。
    {: tip}

    応答には、一般モデル、つまり一般分類器 (`default` の classifier_id を使用する)、イメージ内で識別されたクラス、および各クラスのスコアが含まれます。

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    信頼性スコアは、0 から 1 の範囲になります。スコアが高いほど、相関性が高いことを示しています。デフォルトで、`/v3/classify` 呼び出しには、`0.5` より低いスコアのクラスは含まれません。

## ステップ 2: イメージ内の顔の検出
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} は、イメージ内で顔を検出できます。応答は、イメージ内での顔の位置、およびそれぞれの顔の推定年齢範囲と性別などの情報を提供します。

また、このサービスは、多くの有名人を名前で識別でき、高水準の概念を集約できるように*ナレッジ・グラフ*を提供することができます。

1.  サンプルの <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> イメージをダウンロードします。
1.  `POST /v3/detect_faces` メソッドに以下のコマンドを発行して、イメージをアップロードして分析します。ユーザー独自の画像を使用する場合、最大サイズは 2 MB です。
    - `{api-key}` を、前にコピーしたサービス資格情報に置き換えます。
    - images\_file ロケーションを変更して、画像を保存した場所を指すようにします。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    応答には、場所、推定年齢、性別、ID とタイプ階層 (サービスがその顔を認識する場合)、およびそれぞれのスコアが含まれます。

    スコアは 0 から 1 までの範囲で、スコアが高いほど相関性が大きいことを示します。すべての顔が検出されますが、10 個を超える顔がある画像の場合、年齢および性別の信頼度スコアは、スコア 0 が返される可能性があります。

    ```json
    {
      "images": [
        {
          "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 次のステップ

{{site.data.keyword.visualrecognitionshort}} での組み込み default 分類器の使用方法について基本的に理解しました。次に、さらに詳細に検討します。



- [カスタム分類器の作成](/docs/services/visual-recognition/tutorial-custom-classifier.html)方法について学びます。
- 『[API reference ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}』で、API に関する説明を読みます。

### 帰属
{: #attributions}

- Flikr ユーザー [Ryan Edwards-Crewe ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.flickr.com/photos/ryanec/){: new_window} による [Fruit basket ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://flic.kr/p/JPHES){: new_window} は、[Creative Commons Attribution 2.0 の使用許諾![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} を受けて使用されました。このイメージに対する変更は行われていません。
- Flikr ユーザー [dcblog ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.flickr.com/photos/12863058@N08/){: new_window} による [obama ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://bit.ly/1T0DCl9){: new_window} は、[Creative Commons Attribution 2.0 の使用許諾![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} を受けて使用されました。このイメージに対する変更は行われていません。
