---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# 画像内のテキストの認識
{: #tutorial-recognize-text}

このチュートリアルでは、{{site.data.keyword.visualrecognitionshort}} ベータ版の Text モデルで初回呼び出しを行って、画像内の英語のテキストを検出して認識する方法を示します。
{: shortdesc}

Text モデルはプライベート・ベータ機能です。このモデルを呼び出すには、{{site.data.keyword.IBM_notm}} の許可が必要です。[アクセスをリクエストしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://datasciencex.typeform.com/to/nU6efl){: new_window}。ベータ機能について詳しくは、[リリース・ノート](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)を参照してください。
{: important}

## 始めに
{: #tutorial-recognize-text-prerequisites}

1.  {{site.data.keyword.Bluemix_notm}} カタログの [{{site.data.keyword.visualrecognitionshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/visual-recognition){: new_window} ページに移動します。
    1.  無料の {{site.data.keyword.Bluemix_notm}} アカウントに登録するか、ログインします。
    1.  **「作成」**をクリックします。
- 以下のようにして、サービス・インスタンスに認証する資格情報をコピーします。
    1.  **「表示」**をクリックして、資格情報を表示します。
    1.  **「API キー」**の値をコピーします。

## ステップ 1: 画像内のテキストを認識する
{: #tutorial-recognize-text-recognize-text}

1.  [画像 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window} に含まれるテキストを認識させるために、以下の呼び出しを発行します。`{your_api_key}` を、先ほどコピーした API キーの値に置き換えます。

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    応答には、認識されたテキスト (text) と、そのテキスト内の各単語 (word) の位置 (location)、および各単語の信頼性スコア (score) が含まれます。location 情報を使用することで、各単語の周囲に境界ボックスを描くことができます。

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 次のステップ

画像内のテキストを認識する方法について、基本的な理解が得られました。さらに調べてください。

- [概説](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-)を参照します。
- [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window} で、Text モデルのメソッドについて調べます。

### 帰属
{: #tutorial-recognize-text-attributions}

- [Unsplash ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} での [Lubo Minar ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://unsplash.com/@bubo){: new_window} による [lookButDontTouch ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}。このイメージに対する変更は行われていません。
