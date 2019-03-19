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

# 建立自訂模型
{: #tutorial-custom-classifier}

您完成「入門指導教學」中的影像分析後，即可以訓練及建立自訂模型。使用自訂模型，您可以訓練 {{site.data.keyword.visualrecognitionshort}} 服務來分類影像，以符合您的商業需要。
{: shortdesc}

## 步驟 1：複製認證
{: #copy-credentials}

請使用您在「入門指導教學」中複製的認證。如果您未建立服務實例，請執行[開始之前](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites)小節中的那些步驟。

## 步驟 2：建立自訂模型
{: #create}

{{site.data.keyword.visualrecognitionshort}} 可以從您上傳的範例影像學習，以建立新的多資料類型模型。每個範例檔案會針對該呼叫中的其他檔案訓練，正面的範例會儲存為類別。這些類別會分組以定義單一模型，並傳回各自的評分。負面範例檔案不會儲存為類別。

1.  下載 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 及 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 範例訓練檔案。
1.  使用下列指令呼叫 `POST /v3/classifiers` 方法，以上傳訓練資料及建立 `dogs` 自訂模型：
    - 將 `{your_api_key}` 取代為您在第一個步驟中複製的服務認證。
    - 修改 `{class}_positive_examples` 的位置，以指向您儲存 .zip 檔之處。

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

    正面範例檔名需要 `_positive_examples` 字尾。在此範例中，檔名是 `beagle_positive_examples`、`goldenretriever_positive_examples` 及 `husky_positive_examples`。字首（beagle、goldenretriever 及 husky）會傳回作為類別的名稱。
    {:tip }

    回應包含新的分類器 ID 及狀態，例如：

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

1.  定期檢查訓練狀態，直到您看到 `ready` 狀態為止。訓練會立即開始，而且必須完成，您才能夠查詢模型。請將 `{your_api_key}` 及 `{classifier_id}` 取代為您的資訊：

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 步驟 3：更新現有自訂模型
{: #tutorial-custom-classifier-update}

您可以藉由新增類別至模型或新增影像至現有類別，來更新自訂模型。在這裡，您可以藉由新增*大麥町犬*類別至可以分類「狗」類型來改進您在步驟 2 中建立的模型。您也可以將 cat 的影像新增至 "dogs" 自訂模型的負面範例集。

1.  下載 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 及 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 範例訓練檔案。
1.  使用下列 cURL 指令呼叫 `POST /v3/classifiers/{classifier_id}` 方法，以上傳訓練資料及更新自訂模型 "dogs\_1941945966"：
    - 將 `{your_api_key}` 取代為您在第一個步驟中複製的服務認證。
    - 將 `{classifier_id}` 取代為您要更新的自訂模型的 ID。
    - 修改 `{class}_positive_examples` 的位置，以指向您儲存 .zip 檔之處。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    現有 "dogs" 自訂模型會取代為具有相同 classifier_id 且重新訓練的 "dogs" 自訂模型。回應會列出新的類別集和現行狀態。例如：

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

    訓練會立即開始。當新的可用時，狀態會變更為 `ready`。

    在現行狀態變更為 `ready` 狀態之前，請勿發出另一個重新訓練要求。多個重新訓練模型的要求會導致單一重新訓練生效。名稱為 `updated` 的時間戳記顯示最近更新模型的時間。如果您在模型正在進行重新訓練時呼叫 `/classify` 方法，將會使用模型的舊定義。{: tip}
1.  定期檢查訓練狀態，直到您看到 `ready` 狀態為止。請將 `{your_api_key}` 及 `{classifier_id}` 取代為您的資訊：

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 步驟 4：使用自訂模型分類影像
{: #tutorial-custom-classifier-classify}

新的模型備妥後，請呼叫該模型以查看它的執行狀況。

1.  下載 <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a>。
1.  使用 `POST /v3/classify` 方法來測試您的自訂模型。下列範例同時使用 "dogs\_1941945966" 自訂模型及內建的`預設`一般模型來分類 `dogs.jpg` 影像：
    - 將 `{your_api_key}` 取代為您在第一個步驟中複製的服務認證。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    若只要針對內建 General 模型進行分類，請省略 `classifier_ids` 參數。{: tip}

    回應包括分類器（模型）、它們的類別，以及每個類別的評分。評分範圍從 0-1，評分越高表示相關性越強。如果識別了高評分的類別，則依預設 `/v3/classify` 呼叫會省略低評分的類別。您可以藉由在呼叫中指定 `threshold` 參數的浮點數值，設定要顯示的評分下限。

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

1.  檢查您的結果。

完成了！您已經使用 {{site.data.keyword.visualrecognitionshort}} 來建立、訓練及查詢自訂模型。

### 刪除您的自訂模型
{: #tutorial-custom-classifier-delete}

您可能想要刪除您的自訂模型，來以全新的實例開始開發應用程式。

若要刪除模型，請呼叫 `DELETE /v3/classifiers/{classifier_id}` 方法。請將 `{your_api_key)` 及 `classifier_id` 取代為您的資訊：

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## 後續步驟
{: #tutorial-custom-classifier-next-steps}

現在，您對如何使用自訂模型已有基本瞭解，您可以更深入探索：

- 進一步瞭解 [Best practices for custom classifiers ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}。
- 在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition){: new_window} 中閱讀 API 的相關資訊。

### 歸屬
{: #tutorial-custom-classifier-attributions}

本頁面上使用的所有影像都來自 Flikr，並根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。這些影像未經過任何變更。
