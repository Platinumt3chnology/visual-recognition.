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

# 入門指導教學

本指導教學指引您如何在 {{site.data.keyword.visualrecognitionfull}} 使用部分內建分類器，來分類影像然後偵測影像中的臉孔。
{: shortdesc}

## 開始之前
{: #prerequisites}

- 建立服務實例：
    - {: download} 如果您看到這個，您已建立服務實例。現在，請取得您的認證。
    - 從服務建立專案：
        1.  移至 {{site.data.keyword.watson}} Developer Console [服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/developer/watson/services){: new_window} 頁面。
        1.  選取 {{site.data.keyword.visualrecognitionshort}}、按一下**新增服務**，然後註冊免費 {{site.data.keyword.Bluemix_notm}} 帳戶或是進行登入。
        1.  鍵入 `vision-tutorial` 作為專案名稱，然後按一下**建立專案**。
- 複製認證以向服務實例進行鑑別：
    - {: download} 從服務儀表板（您正在看的地方）：
        1.  按一下**服務認證**標籤。
        1.  按一下**動作**底下的**檢視認證**。
        1.  複製 api-key 值。
        {: download}
    - 在 Developer Console 從您的 **vision-tutorial** 專案的**認證**區段，複製 `"visual_recognition"` 的 `api-key` 值。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果您使用 {{site.data.keyword.Bluemix_dedicated_notm}}，請從型錄的 [{{site.data.keyword.visualrecognitionshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} 頁面建立服務實例。如需如何尋找服務認證的詳細資料，請參閱 [Watson 服務的服務認證 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步驟 1：分類影像
{: #classify}

1.  下載範例 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 影像。
1.  發出下列指令，以上傳影像並針對所有內建分類器來分類它。
    - 將 `{api-key}` 取代為先前複製的服務認證。
    - 修改 images\_file 的位置，以指向您儲存影像之處。

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    如果您有「{{site.data.keyword.Bluemix_notm}} 專用」，此處的 `gateway-a.watsonplatform.net` 端點可能不是服務服務端點。請檢查服務儀表板的**服務認證**頁面上的 `url`。
    {: tip}

    回應包括一般模型或分類器（使用 `default` classifier_id）、影像中識別的類別，以及每個類別的評分。

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

    信任評分範圍從 0 到 1，評分越高表示相關性越強。依預設，`/v3/classify` 呼叫不會包含評分低於 `0.5` 的類別。

## 步驟 2：偵測影像中的臉孔
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} 可以偵測影像中的臉孔。回應提供的資訊像是影像中臉孔的位置，以及每張臉的預估年齡範圍和性別。

服務也可以用名字識別名人，且可以提供*知識圖形* 以便您聚集更高層次的概念。

1.  下載範例 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 影像。
1.  發出下列指令給 `POST /v3/detect_faces` 方法，以上傳及分析影像。如果您使用自己的影像，大小上限為 2 MB：
    - 將 `{api-key}` 取代為先前複製的服務認證。
    - 修改 images\_file 的位置，以指向您儲存影像之處。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    回應包含位置、年齡估計、性別、身分及類型階層（如果服務認得該臉孔），以及每一項的評分。

    評分範圍從 0-1，評分越高表示相關性越強。所有臉孔都會偵測到，但對於具有超過 10 張臉孔的影像，年齡和性別信任評分可能會傳回 0 的評分。

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

## 後續步驟

您已對於如何使用內建的預設分類器搭配 {{site.data.keyword.visualrecognitionshort}} 具有基本的瞭解。現在，更深入點：

- 進一步瞭解如何[建置自訂分類器](/docs/services/visual-recognition/tutorial-custom-classifier.html)。
- 在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中閱讀 API 的相關資訊。

### 歸屬
{: #attributions}

- Flikr 使用者 [Ryan Edwards-Crewe ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.flickr.com/photos/ryanec/){: new_window} 提供的[水果籃 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://flic.kr/p/JPHES){: new_window}，根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此影像未經過任何變更。
- Flikr 使用者 [dcblog ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.flickr.com/photos/12863058@N08/){: new_window} 提供的[歐巴馬 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://bit.ly/1T0DCl9){: new_window} ，根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此影像未經過任何變更。
