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

# 建立自訂分類器

您在「入門指導教學」中分類影像之後，您便可以訓練及建立自訂分類器（或模型）。使用自訂分類器，您可以訓練 {{site.data.keyword.visualrecognitionshort}} 服務，以分類影像符合您的商業需要。
{: shortdesc}

## 步驟 1：複製認證
{: #copy-credentials}

請使用您在「入門指導教學」中複製的認證。如果您未建立服務實例，請執行[開始之前](/docs/services/visual-recognition/getting-started.html#prerequisites)小節中的那些步驟。

## 步驟 2：建立自訂分類器
{: #create}

{{site.data.keyword.visualrecognitionshort}} 可以從您上傳的範例影像學習，以建立新的多資料類型分類器。每個範例檔案會針對該呼叫中的其他檔案訓練，正面的範例會儲存為類別。這些類別會分組以定義單一分類器，並傳回自己的評分。負面範例檔案不會儲存為類別。

1.  下載 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 及 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 範例訓練檔案。
1.  使用下列指令呼叫 `POST /v3/classifiers` 方法，它會上傳訓練資料並建立 `dogs` 分類器：
    - 將 `{api-key}` 取代為您在第一個步驟中複製的服務認證。
    - 修改 `{class}_positive_examples` 的位置，以指向您儲存 .zip 檔之處。

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

    正面範例檔名需要 `_positive_examples` 字尾。在此範例中，檔名是 `beagle_positive_examples`、`goldenretriever_positive_examples` 及 `husky_positive_examples`。字首（beagle、goldenretriever 及 husky）會傳回作為類別的名稱。
    {:tip }

    回應包含新的分類器 ID 及狀態，例如：

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

1.  定期檢查訓練狀態，直到您看到 `ready` 狀態為止。訓練會立即開始，且必須結束，您才能查詢分類器。將 `{api  key}` 及 `{classifier_id}` 取代為您的資訊：

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 步驟 3：更新現有自訂分類器

您無法使用免費 API 金鑰更新自訂分類器。如果您有免費金鑰，可以升級至標準方案。如需詳細資料，請參閱[變更方案](https://console.bluemix.net/docs/pricing/changing_plan.html)。
{: tip}

您可以藉由新增類別至分類器，或是新增影像至現有類別，來更新自訂分類器。在這裡，您會藉由新增 *Dalmatian* 類別至可以分類的狗類型，來改善您在步驟 2 中建立的分類器。您也會將貓的影像新增至 "dogs" 分類器的負面範例集。

1.  下載 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 及 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 範例訓練檔案。
1.  使用下列 cURL 指令呼叫 `POST /v3/classifiers/{classifier_id}` 方法，它會上傳訓練資料並更新分類器 "dogs\_1941945966"：
    - 將 `{api-key}` 取代為您在第一個步驟中複製的服務認證。
    - 將 `{classifier_id}` 取代為您要更新的分類器 ID。
    - 修改 `{class}_positive_examples` 的位置，以指向您儲存 .zip 檔之處。

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    現有的 "dogs" 分類器會被具有相同 classifier_id 的重新訓練分類器取代。回應會列出新的類別集和現行狀態。例如：

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

    訓練會立即開始。當新的可用時，狀態會變更為 `ready`。

    在現行狀態變更為 `ready` 狀態之前，請勿發出另一個重新訓練要求。多個訓練分類器的要求會導致只有單一個重新訓練生效。稱為 `retrained` 的時間戳記會顯示分類器重新訓練前次的完成時間。如果您在分類器重新訓練時呼叫 `/classify` 方法，會使用分類器的舊定義。
    {: tip}
1.  定期檢查訓練狀態，直到您看到 `ready` 狀態為止。將 `{api  key}` 及 `{classifier_id}` 取代為您的資訊：

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 步驟 4：使用自訂分類器分類影像
{: #classify}

新的分類器就緒時，請呼叫它以查看其執行。

1.  建立稱為 `myparams.json` 的 JSON 檔案，其中包含您呼叫的參數，例如新分類器的 `classifier_id` 以及一般模型分類器（使用 `default` classifier_id）。簡單的 JSON 檔案可能看似如下：

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  下載 <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a>。
1.  使用 `POST /v3/classify` 方法以測試您的自訂分類器。下列範例會針對 "dogs\_1941945966" 分類器來分類 `dogs.jpg` 影像：
    - 將 `{api-key}` 取代為您在第一個步驟中複製的服務認證。

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    若要只針對內建的一般模型分類，請省略 `parameters` 參數。
    {: tip}

    回應包含分類器、其類別，以及每個類別的評分。評分範圍從 0-1，評分越高表示相關性越強。如果識別了高評分的類別，則依預設 `/v3/classify` 呼叫會省略低評分的類別。您可以藉由在呼叫中指定 `threshold` 參數的浮點數值，設定要顯示的評分下限。

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

1.  檢查您的結果。

完成了！您已使用 {{site.data.keyword.visualrecognitionshort}} 建立、訓練並查詢自訂分類器。

### 刪除自訂分類器

您可能想要刪除自訂分類器，以用全新的實例開始開發應用程式。

若要刪除分類器，請呼叫 `DELETE /v3/classifiers/{classifier_id}` 方法。將 `{api_key)` 及 `classifier_id` 取代為您的資訊：

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## 後續步驟

既然您已對於如何使用自訂分類器具有基本的瞭解，可以再深入點：

- 進一步瞭解 [Best practices for custom classifiers ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}。
- 在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中閱讀 API 的相關資訊。

### 歸屬
{: #attributions}

本頁面上使用的所有影像都來自 Flikr，並根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。這些影像未經過任何變更。
