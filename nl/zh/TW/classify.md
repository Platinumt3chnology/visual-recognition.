---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

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

# 關於分類器

當您分類影像時，Visual Recognition 會傳回在影像中找到的一組類別。它會從它訓練所在的影像衍生出該資訊。分類器是一組類別。

Visual Recognition 包含數個內建分類器，它們可以提供高正確性的結果，且您不必進行訓練。您也可以訓練自訂分類器，以建立特殊化類別。

Clarifai 入門
> 預測的類型是根據您執行輸入所透過的模型。例如，如果您透過 'food' 模型執行輸入，它傳回的預測將包含 'food' 模型所知道的概念。如果您透過 'color' 模型執行輸入，它將會傳回您影像中主要顏色的預測。

Clarifai
> Clarifai 提供許多不同的模型，它們會以不同的方式「看見」這世界。模型包含一組的概念。一個模型只會看到它包含的概念。
>
> 有時候您會想要有模型以您看世界的方式來看世界。API 允許您這麼做。您可以建立自己的模型，並用您自己的影像和概念來訓練它。一旦訓練它以您要的方式看世界，便可以使用該模型來進行預測。

## 內建分類器

Visual Recognition 包含一組分類器，可提供高正確性的結果而不需訓練。現行內建分類器名為 `default`、`food` 及 `explicit`。

### 預設分類器

預設分類器會從數以千計的可能標籤傳回類別，並組織成種類及子種類。可以傳回下列頂層種類：

- 動物（包括鳥類、爬蟲類、兩棲動物等等）
- 人和以人為導向的資訊與活動
- 食物（包括熟食和飲料）
- 植物（包括樹木、灌木、水生植物、蔬菜）
- 運動
- 自然（包括許多類型的自然形成物、地質結構）
- 運輸（陸、水、空）
- 以及更多其他內容，這其中包括家具、水果、樂器、工具、顏色、小機械、裝置、儀器、武器、建築物、結構與人造物體、服裝和花等等。

### Food 分類器

雖然預設分類器可以識別食物和飲料，您可以指定內建的 `food` 分類器，以針對...

### Explicit 分類器

Visual Recognition 可以分類影像是否不適合一般使用。`explicit` 分類器目前可識別可能被視為色情影像的內容。此這分類的常見縮寫稱為 _NSFW_，意思是_對工作不安全 (not safe for work)_。

高於或低於特定數目的評分並不保證影響是否明確。不過，您可以使用回應作為影像的起始過濾器，然後從該點進行更多分析。

回應：
```json
{
  "images": [
    {
      "classifiers": [
        {
          "classes": [
            {
              "class": "not explicit",
              "score": 0.704
            }
          ],
          "classifier_id": "explicit",
          "name": "explicit"
        }
      ],
      "resolved_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png",
      "source_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png"
    }
  ],
  "images_processed": 1
}
```
{: codeblock}

## 結合分類器


## 回應中的類別階層

`/v3/classify` 方法會在相關類別的階層內分類影像。例如，小獵犬的圖片可能分類為 "animal"，以及相關的 "dog" 和 "beagle"。與相關類別的正符合，在本例中為 "dog" 和 "beagle"，會提高母項回應的評分。在本例中，回應包含全部三種類別："animal"、"dog" 及 "beagle"。母類別 ("animal") 的評分會提高，因為它符合相關的類別（"dog" 及 "beagle"）。母項也是 "type\_hierarchy"，顯示它是階層的母項。

## 大量分類的準則

當您提交許多影像時，下列方法可讓服務的效率及效能最大化：

- 將影像裁剪或調整大小為 224 x 224 像素。目前服務針對此大小進行最佳化，但可能會改變。
    - 如果影像長寬比大於 2:1 或小於 1:2，請裁剪它。
    - 考慮將影像裁剪成多個方形影像，或只包含影像的中央，視什麼內容對您的使用最重要而定。
- 在單一 .zip 檔中提交最多 20 個影像。您不需要使用任何壓縮，因為 JPEG 和 PNG 影像是壓縮檔。
- 使用 **classifier_ids** 參數，以便僅指定您要使用的分類器。
- 雖然服務可讀取 EXIF 標籤並旋轉影像，為了最佳產量起見，請傳送不需要由服務旋轉的影像（EXIF **Orientation** 標籤設為 `1`）。
