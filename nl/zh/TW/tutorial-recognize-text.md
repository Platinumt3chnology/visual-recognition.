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

# 辨識影像中的文字
{: #tutorial-recognize-text}

本指導教學指導您如何進行第一次呼叫，並使用 {{site.data.keyword.visualrecognitionshort}} 測試版 Text 模型來偵測及辨識影像中的英文文字。
{: shortdesc}

Text 模型是一個專用測試版功能，您必須向 {{site.data.keyword.IBM_notm}} 取得許可權才能夠呼叫此模型。[要求存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://datasciencex.typeform.com/to/nU6efl){: new_window}。如需測試版功能的相關資訊，請參閱[版本注意事項](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)。
{: important}

## 開始之前
{: #tutorial-recognize-text-prerequisites}

1.  移至「{{site.data.keyword.Bluemix_notm}} 型錄」中的 [{{site.data.keyword.visualrecognitionshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 頁面。
    1.  註冊免費 {{site.data.keyword.Bluemix_notm}} 帳戶，或者登入。
    1.  按一下**建立**。
- 複製認證以向服務實例進行鑑別：
    1.  按一下**顯示**以檢視您的認證。
    1.  複製 **API 金鑰**值。

## 步驟 1：辨識影像中的文字
{: #tutorial-recognize-text-recognize-text}

1.  發出下列呼叫，來辨識 [影像 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}中的文字。請將 `{your_api_key}` 取代為您先前複製的 API 金鑰值 API。

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    回應包括所辨識的文字和每個單字在文字中的位置，以及每個單字的信任評分。位置資訊可用來繪製圍住單字的外框。

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

## 後續步驟

您對如何辨識影像中的文字已有基本瞭解。可以進一步進行探索。

- 請閱讀[概觀](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-)。
- 在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window} 中探索 Text 模型的方法。

### 歸屬
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}，作者 [Lubo Minar ![外部鏈結圖示 ](../../icons/launch-glyph.svg "外部鏈結圖示")](https://unsplash.com/@bubo){: new_window}，取自 [Unsplash ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}。此影像未經過任何變更。
