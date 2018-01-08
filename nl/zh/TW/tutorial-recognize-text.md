---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# 辨識影像中的文字

{: shortdesc}

## 開始之前
{: #copy-credentials}

請使用您在「入門指導教學」中複製的認證來進行此指導教學。如果您未建立服務實例，請執行[開始之前](/docs/services/visual-recognition/getting-started.html#prerequisites)小節中的那些步驟。

## 步驟 1：辨識影像中的文字
{: #recognize-text}

1.  下載範例 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 範例影像
1.  發出下列指令給 `POST /v3/recognize_text` 方法，以上傳及分析影像。如果您使用自己的影像，大小上限為 2 MB：
    - 將 `{api-key}` 取代為先前複製的服務認證。
    - 修改 images\_file 的位置，以指向您儲存影像之處。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    回應包含位置、年齡估計、性別、身分及類型階層（如果服務認得該臉孔），以及每一項的評分。

    評分範圍從 0-1，評分越高表示相關性越強。所有臉孔都會偵測到，但對於具有超過 10 張臉孔的影像，年齡和性別信任評分可能會傳回 0 的評分。


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    ```
    {: codeblock}

## 後續步驟

您已對於如何使用預設分類器搭配 {{site.data.keyword.visualrecognitionshort}} 具有基本的瞭解。現在，更深入點：

- 在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中閱讀 API 的相關資訊。

### 歸屬
{: #attributions}

本頁面上使用的所有影像都來自 Flikr，並根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。這些影像未經過任何變更。
