---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

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

<!-- Link definitions -->

[watson-studio-reg]: https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs
[demo]: https://www.ibm.com/watson/services/visual-recognition/demo

# 版本注意事項
{: #release-notes}

有下列的服務新特性及變更可用。
{: shortdesc}

## 服務 API 版本化
{: version}

API 要求版本參數需要採用 `version=YYYY-MM-DD` 日期格式。每當我們以舊版不相容方式變更 API 時，就會發行新的 API 次要版本。

請在每個 API 要求中傳送版本參數。服務會使用您指定日期的 API 版本，或該日期之前的最新版本。請勿預設為現行日期。請改為指定符合與您的應用程式相容的版本的日期，並且在您的應用程式備妥可接受較新的版本之前，不要變更該日期。

現行版本為 `2018-03-19`。

## 測試版特性
{: #beta}

{{site.data.keyword.IBM_notm}} 發表了分類為測試版的服務、特性及語言支援供您評估。這些特性可能不穩定、經常變更，且可能在通知之後很快停止。測試版特性也可能不提供如一般可用特性提供的相同效能或相容性層次，且不適用於正式作業環境。測試版功能僅在 [IBM Developer Answers ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} 上提供支援。

## 變更
{: #changelog}

有下列的服務新特性及變更可用。


### 2019 年 1 月 15 日
{: #15january2019}

- **Detect Faces 中的性別的翻譯**
    - 現在，當您在 **Accept-Language** 要求標頭中提供語言時，**Detect Faces** 方法會傳回以該語言翻譯 "Male" 和 "Female" 的標籤。如需詳細資料，請參閱 [API 參考資料![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}。

### 2018 年 10 月 1 日
{: #01october2018}

- **2018 年 5 月 23 日之前建立的服務實例會被刪除。**

    - 如同先前的通知，2018 年 5 月 23 日之前建立的所有 {{site.data.keyword.visualrecognitionshort}} 實例都不再有作用。那些實例的資料現在都已刪除。如需如何移至新服務實例的詳細資料，請參閱[移轉](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)。
    - 在此日期之後建立的服務實例不受影響。
    - 如果您有任何問題，請聯絡 [IBM 支援中心 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/ibmcloudsupport){: new_window}。

### 2018 年 8 月 1 日
{: #01august2018}

- **Food 及 Explicit 模型的通用版**

    Food 及 Explicit 模型已從測試版移至通用版 (GA)。Food 模型可辨識比「一般」（預設）模式更多的食物及餐點。Explicit 模型可識別可能被視為色情影像的內容。

    不需要變更程式碼。兩種模型在「精簡」方案下皆為免費，「標準」方案下則為每個影像 $0.002。

    如需相關資訊，請參閱 <em>Watson 部落格</em>中的 [Updates to Watson Visual Recognition ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/visrec-price-reduction){: new_window}。

### 2018 年 7 月 1 日
{: #01july2018}

- **自訂模型的新定價**
    - 從 2018 年 7 月 1 日開始，使用自訂模型來分類影像的成本只要之前費率的一半，現在為每個影像 $0.002。如需詳細資料和其他重要資訊，請參閱 <em>Watson 部落格</em> 中的 [Updates to Watson Visual Recognition \- Price reduction for Custom Classification ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/visrec-price-reduction){: new_window}。

### 2018 年 6 月 21 日
{: #21june2018}

- **其他語言支援**

    - 現在，**Classify** 方法在`預設`（一般）模型類別的輸出中支援中文（簡體和繁體）和葡萄牙文（巴西）。如需完整的語言清單，請參閱[支援的語言](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)。
    - 現在，**Food** 和 **Explicit** 模型的回應中也支援所有語言。


### 2018 年 5 月 22 日
{: #22may2018}

- **新的 API 鑑別程序**:

    您現在要在新的端點對 Identity and Access Management (IAM) 進行鑑別：

    - 針對新實例使用不同的端點 URL。預設端點為 `https:/gateway.watsonplatform.net/visual-recognition/api/`。若要尋找服務實例的 URL，請按一下{{site.data.keyword.cloud_notm}} [儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/dashboard/apps?watson){: new_window} 中的實例，來檢查認證。
    - 修改您如何向 API 進行鑑別。您可以提供 IAM 金鑰或服務實例的存取記號。如需範例，請參閱[移轉](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)。

    對於在 2018 年 5 月 23 日之前建立的服務實例，鑑別程序及端點皆保持不變。請提供 `api_key` 查詢參數來進行鑑別。

- **精簡方案的更新**

    2018 年 5 月 22 日之後建立的「精簡」方案將會變更：

    - 如果您每個用都使用新的「精簡」方案實例，該新的「精簡」方案會在 30 天之後繼續提供使用。
    - 您可以在新的「精簡」方案之下建立及重新訓練兩個自訂模型，
    - 「精簡」方案可包含每月高達 1,000 個事件。您傳送以進行分類、偵測或訓練的每個影像都是一個事件。下載 Core ML 模型不會計入事件限制。

    如果您的需求超出「精簡」方案，請更新計費帳戶。[探索  ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} 定價方案。

- **資訊安全**：

    我們已經更新文件，以包括若干與資料隱私權相關的新的詳細資料。請閱讀[資訊安全](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security)中的詳細資料。

### 2018 年 4 月 12 日
{: #12april2018}

- **精簡方案上重新訓練自訂模型的支援**

    在「精簡」方案之下，當您想要更新或重新訓練模型時，已不再需要刪除及建立另一個自訂模型。現在，只要您保持每日及每月都不超過方案的[限制](https://console.bluemix.net/catalog/services/visual-recognition)，就可以更新自訂模型。

    如果您需要多個模型或相同模型的多個版本，請從「精簡」方案升級至計費帳戶。

- **包含 CORS 支援的新的次要版本**

    **版本：** `2018-03-19`

    現在，當您在要求中指定 `version=2018-03-19` 時，我們將支援「跨原點資源共用 (CORS) 」標頭。

### 2018 年 4 月 5 日
{: #5april2018}

- **Face 模型評分問題的修正**

  Face 模型中的年齡評分範圍已還原為原始範圍 0 到 1。請參閱 2018 年 4 月 2 日的[已知問題](#2april2018)。

- **新的 form-data 參數**

    **Classify images** 及 **Detect faces in images** 方法支援新的 form-data 參數。「分類影像」支援個別的 `url`、`classifier_ids`、`threshold` 以及 `owners` 參數，Detect faces 則支援 `url`。

    過去，您是在 JSON 字串中編碼值，然後傳遞**參數** form-data 參數。您可以針對所有的應用程式開發，在個別的 form-data 參數中使用傳遞這些值的新方法。如需詳細資料，請參閱 [API 參考資料![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition){: new_window}。

### 2018 年 4 月 2 日
{: #2april2018}

- **加強型 Face 模型的通用版**

    現在，通用版 (GA) 包含已更新的臉孔偵測模型。

    此加強型模型使用更廣泛的訓練資料集來針對年齡和性別增加臉孔偵測的正確性。例如，可透過減少 `min` 和 `max` 之間的範圍來提升年齡預測。之前的模型中的固定 9 年年齡範圍已經取代為動態且較小的範圍。平均年齡範圍現在是 4.9 年。

    - API 的變更

    加強型和舊版 Face 模型之間的其他差異如下：
        - 加強型模型支援 .gif 和 .tif 影像格式。
        - 加強型模型支援更大的檔案大小：影像檔最大 10 MB，.zip 檔最大 100 MB。
        - 加強型模型在回應中不包含 `FaceIdentity` 資訊。識別資訊指人員的 `name`、`score` 和 `type_hierarchy` 知識圖。

    如需 API 的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}。

    - 已知問題

        - 表單參數無法包含 **內容類型**。例如，此要求無法分析 **url** 參數，因為其中包含 `;type=text/plain`：

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - 年齡評分的範圍介於 0 到 0.3 之間。我們正在努力還原 0 到 1 的原始範圍。

    - 已淘汰測試版端點

    位於 `/v3/detect_faces_beta` 的測試版端點已淘汰，2018 年 5 月 17 日之後將無法存取。請確定您的要求指向 `/v3/detect_faces`。

### 2018 年 3 月 20 日
{: #20march2018}

- **整合 Apple 核心 ML**

    {{site.data.keyword.visualrecognitionshort}} 現在包含支援 Apple Core ML 模型格式。您可在 iOS 應用程式上使用 {{site.data.keyword.visualrecognitionshort}} 模型的 Core ML 版本。

    **開始進行開發**：若要開始使用 {{site.data.keyword.visualrecognitionshort}} 和 Core ML 進行開發，請到 GitHub 取得下列專案：

    - 在本端分類影像：[{{site.data.keyword.visualrecognitionshort}} 搭配 Core ML ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}。
    - 整合 {{site.data.keyword.discoveryfull}} 和結果：[{{site.data.keyword.visualrecognitionshort}} 和使用 Core ML進行探索 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}。
    - 探索 SDK：[Swift SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}。

- **API 的變更**

    整合中包含下列對 API 進行的與舊版相容的變更：

    - 新的 `core_ml_enabled` 欄位，指示分類器模型是否可以下載為 Core ML 模型。呼叫 `GET 和 POST /v3/classifiers` 及 `GET /v3/classifiers/{classifier_id}` 時會在回應中傳回此欄位。
    - 新的 `GET /v3/classifiers/{classifier_id}/core_ml_model` 方法，可將 Core ML 模型下載為 .mlmodel 檔案。您可以下載 3 月 19 日之後建立的自訂模型的 Core ML 模型檔。
    - 新的`更新日期`欄位，內含模型的最新訓練日期。`更新日期`欄位符合`重新訓練日期`欄位或`建立日期`欄位。

    如需 Core ML API 變更的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}。

- **可用的新工具：Watson Studio**

    [Watson Studio ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")][watson-studio-reg]{: new_window} 是一個新的整合環境，其中包含測試版 {{site.data.keyword.visualrecognitionshort}} 工具的取代項目。
Watson Studio 不僅支援 {{site.data.keyword.visualrecognitionshort}}，還支援許多其他{{site.data.keyword.cloud_notm}}服務和資源。您可以對您現有的 {{site.data.keyword.visualrecognitionshort}} 實例和分類器使用 Watson Studio。

     Watson Studio 透過雲端提供協同的環境。藉由 Watson Studio，開發人員、主題專家、資料科學家，以及其他人員可以建置及訓練 {{site.data.keyword.visualrecognitionshort}} 及其他 AI 模型。您也可以使用 Watson Studio 來存取使用 General 和 Face 模型。

     Watson Studio 還支援 Core ML。您可以針對您的自訂模型下載 Core ML 模型檔。

    [開始使用 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")][watson-studio-reg]{: new_window} Watson Studio。

- **自訂模型的已更新的深度學習架構**

    {{site.data.keyword.visualrecognitionshort}} 現在使用更快速且更有效率的深度學習網路架構來進行分類。更新的模型還能夠更牢固地區分和最上層類別和其餘類別。這種方法可能會導致更長的訓練時間。新的架構可用來訓練新的自訂模型。當您重新訓練現有的舊模型時，會使用原始架構。

    下列範例顯示與新架構之間的差異：

    ![男子拉弓射箭。相片取自 Unsplash，作者為 Annie Spratt](images/archery.jpg)

    <table>
      <tr>
        <th>原始類別和評分</th>
        <th>已更新的類別和評分</th>
      </tr>
      <tr>
        <td>射箭</br>0.99 </td>
        <td><strong>射箭<strong></br>0.9</td>
      </tr>
      <tr>
        <td>賽車</br>0.996398</td>
        <td><strong>騎自行車</strong></br>0.004</td>
      </tr>
      <tr>
        <td>騎自行車</br>0.0500174</td>
        <td><strong>釣魚</strong></br>0.001</td>
      </tr>
      <tr>
        <td>釣魚</br>0.11029</td>
        <td><strong>高爾夫</strong></br>0.031</td>
      </tr>
      <tr>
        <td>高爾夫</br>0.0980796</td>
        <td><strong>體操</strong></br>0.029</td>
      </tr>
      <tr>
        <td>體操</br>0.964391</td>
        <td><strong>柔道</strong></br>0.021</td>
      </tr>
      <tr>
        <td>柔道</br>0.339119</td>
        <td><strong>競速</strong></br>0.002</td>
      </tr>
      <tr>
        <td>滑冰</br>0.0393602</td>
        <td><strong>滑冰</strong></br>0.061</td>
      </tr>
      <tr>
        <td>滑雪</br>0.0310527</td>
        <td><strong>滑雪</strong></br>0.003</td>
      </tr>
      <tr>
        <td>田徑</br>0.208147</td>
        <td><strong>田賽</strong></br>0.035</td>
      </tr>
    </table>

- **法文語言支援**

    現在，**Classify** 方法的 `default` 模型類別輸出已支援法文。如需完整的語言清單，請參閱[支援的語言](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)。

### 2018 年2 月 23 日
{: #23february2018}

- **測試版提供加強型 Face 模型**

    目前提供已更新的 Face detection 模型。此測試版模型使用更廣泛的訓練資料集來針對年齡和性別增加臉孔偵測的正確性。如需相關資訊，請參閱 [增加 IBM Watson 的正確性 {{site.data.keyword.visualrecognitionshort}} 服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} 以及[減少 AI 模型中的偏差 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}。

    - 您可以在[展示 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")][demo]{: new_window} 以及測試版[視覺化識別工具 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} 中檢視已更新的模型的結果。
    - 可從 `/v3/detect_faces_beta` 取得測試版模型。

    測試版模型與通用版 (GA) 模型之間的差異；
    - 測試版模型支援 .gif 和 .tif 影像格式；此增強功能預期將應用於 GA 模型。
    - 測試版模型支援更大的檔案大小：影像檔最大 10 MB，.zip 檔最大 100 MB。此加強功能預期將應用於 GA 模型。
    - 測試版臉孔偵測在回應中不包含 `FaceIdentity` 資訊。
    - 測試版模型的 POST 要求需要不含空白的檔名。GA Face 模型不強制套用此限制。
    - 測試版模型的 POST 要求支援稱為 `url` 的個別表單參數。GA 模型將該資訊包含在 `parameters` JSON 物件中。如需詳細資料，請參閱 [API 瀏覽器 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-api-explorer.mybluemix){: new_window}。

- **臉孔識別已淘汰**

    GA Face 模型回應中的識別資訊已淘汰，將從 **2018 年 4 月 2 日**起從 API 移除。識別資訊指人員的 `name`、`score` 和 `type_hierarchy` 知識圖。

### 2018 年 1 月 16 日
{: #16january2018}

- **精簡帳戶和方案將取代免費方案**

    「精簡」帳戶為免費；不需要信用卡。不過，「精簡」方案服務實例會在 30 天之後刪除。

    您在「精簡」方案可使用的 API 呼叫數上限和「免費」方案稍有不同。在「精簡」方案，您每月最多可呼叫 7,500 次 API，每天最多可呼叫 250 次 API。

    當您擁有自訂分類器而要升級至計費帳戶時，請建立另一個服務實例並重建您的自訂分類器。

### 2017 年 12 月 11 日
{: #11december2017}

<ul>
  <li>
    <strong>提高一般模型的正確性及輸出</strong>
      <p>
        一般模型包含數千個標籤，現在能偵測更多次要物件，並且改良了場景偵測。這些改良有助於辨識影像較不突出的層面。此外，每個影像傳回的平均標籤數已增加到 10。
      </p>
      <p>
        下列影像顯示在更新之前的傳回標籤範例，以及現在傳回的其他標籤。
      </p>
      <img src="images/tree-flower.jpg" alt="杜鵑花植物的相片">
      <table>
        <tr>
          <th>原始標籤</th>
          <th>其他標籤</th>
        </tr>
        <tr>
          <td></td>
          <td>
          標籤：樹<br/>
          評分：0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          標籤：花 <br/>
          評分：0.792</td>
        </tr>
        <tr>
          <td>
          標籤：高山杜鵑花<br/>
          評分：0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          標籤：植物<br/>
          評分：0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          標籤：杜鵑花<br/>
          評分：0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            標籤：沼澤杜鵑花<br/>
          評分：0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            標籤：橘紅色<br/>
          評分：0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>測試版中提供的新的明確模型</strong>
      <p>
        在測試版中發表的明確模型會分類影像是否包含色情內容且不適合一般用途。您可以包含明確模型與其他模型，進行結合分析。例如，若要在您的要求中同時包含 `default` 及 `explicit` 分類器 ID，以傳回影像標籤及影像是否包含明確內容。
      <p>
如需 API 呼叫的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#classify-images) 中的 **Classify images** 方法。</p>
    </li>
    <li>
      <strong>支援較大的檔案大小</strong>
      <p>
        <strong>分類影像</strong>方法現在支援最多 10 MB 的影像檔，以及最多 100 MB 的 .zip 檔。
    </li>
    <li>
      <strong>傳遞分類器 ID 時需要陣列</strong>
      <p>
        API 現在會在您在**分類影像**方法的 **parameters** 物件之中傳入 `classifier_ids` 時施行陣列。先前，您可以用字串形式傳遞分類器 ID。如需相關資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#classify-images) 中的參數說明和範例檔案。
      </p>
    </li>
</ul>

### 2017 年 9 月 8 日
{: #8september2017}

- **測試版相似性搜尋與集合已結束**：截至 2017 年 9 月 8 日，相似性搜尋的測試版期間已經結束。如需相關資訊，請參閱 [Visual Recognition API – Similarity Search Update ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}。

### 2017 年 6 月 30 日
{: #30june2017}

- **改良標記**：我們增加了預設分類器的訓練影像數目。如此會更加改善正確辨識影像整體「場景」的能力。如需詳細資料，請參閱 [Further Enhancements for General Tagging Feature ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **其他語言**：**分類影像**方法除了英文、阿拉伯文、西班牙文和日文之外，現在也支援韓文、義大利文和德文。

    如需 API 呼叫的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window} 的**分類影像**方法。

### 2017 年 5 月 16 日
{: #16may2017}

- **新的 food 分類器可用：測試版**

    新的測試版食物識別模型提供食物項目影像的加強特性和正確性。**分類影像**方法容許您將這個新的分類器 "food" 新增至 `classifier_ids` 參數。

### 2017 4 月 5 日
{: #5april2017}

- **新的 {{site.data.keyword.visualrecognitionshort}} 工具可用：測試版**

    新的測試版特性 － {{site.data.keyword.visualrecognitionshort}} 工具，提供於 [https://watson-visual-recognition.ng.bluemix.net/ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}。此工具有助於您更輕鬆地使用 {{site.data.keyword.visualrecognitionshort}} 服務。藉由輸入 {{site.data.keyword.cloud_notm}} API 金鑰，您可以使用 GUI 存取「一般標記」和「臉孔偵測」特性，以及無縫地建立、重新訓練及刪除與 API 金鑰相關聯的自訂分類器，而不需要撰寫程式碼。

### 2017 年 3 月 8 日
{: #8march2017}

- **更新一般分類器標記的語言支援**

    一般分類器現在會傳回所有支援語言的標記。

- **已知的問題**

    **2017 年 4 月 13 日修正**：訓練或重新訓練在進行中時反覆地呼叫 `GET /classifiers`，以便檢查狀態，可能導致結束 (kill) 訓練工作。若要暫時解決此問題，請使用 `GET /classifiers/{classifier_id}` 輪詢新分類器的狀態。換句話說，針對單一分類器 ID 請使用分類器 `GET`，而不要使用 `GET /classifiers`，後者會取得所有分類器並且可能觸發此問題。請注意，`GET /classifiers/{classifier_id}` 也比較快速。

### 2016 年 12 月 15 日
{: #15december2016}

- **改良的一般分類器標記**

    - 一般分類器的深度學習演算法已經更新。在所有語言的標籤品質有顯著的改良，且服務傳回的英文標籤量明顯增加。這項高品質的標籤輸出也可用於您自行建立自訂分類器時。
    - 已新增彩色標記。服務現在會傳回影像中的前一或二名的顏色。

- **已知的問題**

    - 提交至展示且具有 EXIF meta 資料的影像，不會正確地指定方向（橫印與直印）給服務。iPhone 上傳的影像可能會包含 EXIF meta 資料標籤。這點的暫行解決方法是更新您的影像 meta 資料，不要根據 EXIF meta 資料標籤來指定影像的方向。通常只需要在電腦上開啟您的影像然後儲存它，就能達成。例如，在 Mac 上以預覽開啟然後儲存影像，便會設定正確的方向標籤。
    - 傳送具有 [EXIF 標籤 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://en.wikipedia.org/wiki/Exif){: new_window} 值 8、3 或 6 的影像給 {{site.data.keyword.visualrecognitionshort}} 服務可能會增加延遲。服務會將影像的像素旋轉至已編碼的觀點。您可以藉由預先旋轉影像，或移除對您 {{site.data.keyword.visualrecognitionshort}} 作業不重要的 EXIF 標頭來節省時間。

### 2016 年 12 月 1 日
{: #1december2016}

- **新的定價**

    {{site.data.keyword.IBM_notm}} 已降低 {{site.data.keyword.visualrecognitionshort}} 服務上的自訂分類器的計價，並增強「免費」方案的可用項目。如需相關資訊，請參閱 [{{site.data.keyword.visualrecognitionshort}} 定價頁面](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)。

### 2016 年 10 月 7 日
{: #7october2016}

- **臉孔偵測加強功能**

    服務有新的臉孔偵測演算法，它改善了 `GET` 及 `POST /v3/detect_faces` 方法的回應。服務調整了低信任度年齡、名字和性別的臉孔偵測過濾。因此，會找到更多臉孔，並傳回更大範圍的信任度。

### 2016 年 9 月 8 日
{: #8september2016}

- **相似性搜尋測試版**

    使用者現在可以上傳自己的影像集合、使用影像搜尋該集合中的類似影像，然後服務會傳回前 100 名最類似的影像。相似性搜尋可以用於任何用途，使用者可以用最多每個集合一百萬張影像來自訂訓練服務。如需使用新的相似性搜尋功能的相關資訊，請參閱[指導教學](/docs/services/visual-recognition/tutorial-collections.html)，以及 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 頁面。

- **文字辨識現在為封閉測試版**

    `POST` 及 `GET /v3/recognize_text` 方法已回到封閉測試版。{{site.data.keyword.IBM_notm}} 未來將繼續支援使用此服務的 BETA 客戶，目前沒有其他開放測試版的計劃。

### 2016 年 8 月 1 日

- **上市定價結束**

    自訂分類器訓練及重新訓練、自訂影像分類，以及自訂影像儲存空間不再免費。如需定價相關資訊，請參閱 {{site.data.keyword.visualrecognitionshort}} 服務[定價頁面](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)。

### 2016 年 7 月 5 日
{: #5july2016}

- **更新自訂分類器**

    自訂分類器不再受限於固定的訓練資料集。使用者現在可以用新的影像更新現有分類器，或新增其他正面或負面範例分類器至現有的已受訓分類器。藉由提供其他範例影像讓 Watson 學習，服務可以讓使用者的分類器更正確。自訂分類器現在可以隨著時間而學習，持續地更能瞭解視覺化資訊。

- **已知的問題**

    **2017 年 4 月 13 日修正**：使用者更新現有分類器之後的 30 或 90 秒，可能得到 500 錯誤碼。儘管發生錯誤，很有可能重新訓練要求已順利完成。請等待至少 2 分鐘，再使用 `GET classifiers/{classifier\_id}` 方法檢查分類器的狀態。如果狀態為 "ready"，並且已更新 "retrained" 時間戳記，則產生 500 代碼的重新訓練要求已成功。否則，如果 "retrained" 時間戳記未更新，在回應中會新增說明，解釋重新訓練為何失敗，服務也會將分類器回復成發出重新訓練要求之前的版本。

### 2016 年 5 月 20 日
{: #20 may 2016}

這是 {{site.data.keyword.visualrecognitionshort}} 服務的通用版。這個版本引進服務的第 3 版，且是一項岔斷變更。這個版本納入了來自 AlchemyVision 服務（已淘汰）的功能。

服務在測試版時建立的任何自訂分類器，都必須在服務的 GA 實例中重建。

對於 {{site.data.keyword.visualrecognitionshort}} 服務已經進行下列變更及更新：

- **版本日期：**為了利用此版本的特性，請使用 `2016-05-20` 作為 `version` 參數的值。
- **類別及分類器：**單一分類器現在稱為「類別」。在 GA 中，一群類別稱為「分類器」。
- **分類：**使用 `POST` 或 `GET /v3/classify` 方法，以使用預設類別快速且正確地識別各種主題和場景。
- **臉孔偵測：**使用 `POST` 或 `GET /v3/detect_faces` 方法，以偵測影像中的臉孔，並取得其相關資訊，例如臉孔在影像中的位置，以及每張臉的預估年齡範圍和性別。服務也可以依名稱來識別許多名人，以及提供知識圖，以便您將有趣的事物聚集成更高層次的概念。
- **多資料類型自訂分類器：**您現在可以建立並訓練高度特殊化的分類器（由數個類別定義）。例如，您可以建立 "new\_red\_car" 分類器，它由類別 "new\_cars" 及 "red\_cars" 所定義。若要進一步瞭解建立多資料類型分類器，請參閱[訓練資料的結構](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure)。
- **非同步訓練：**自訂分類器的訓練現在是非同步的，因此訓練呼叫會快速完成，而您的自訂分類器則繼續在背景中學習。若要檢查自訂分類器的訓練狀態，並找出它何時可以使用，請呼叫 `GET /v3/classifiers/{classifier_id}` 方法，然後檢查 `status` 回應參數。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 服務的最新版本是岔斷變更，引進了新版本的 {{site.data.keyword.visualrecognitionshort}} API（第 2 版）。第 1 版的 {{site.data.keyword.visualrecognitionshort}} 服務可以使用到服務結束測試版為止。

若要立即開始使用第 2 版的 API，請瞭解並更新您的程式碼以反映下列變更：

- 在第 1 版的服務中，您依標籤來分析影像。在第 2 版的服務中，標籤稱為**分類器**。分類器有以 `classifier_id` 參數指出的唯一分類器 ID，還有以 `name` 參數指出的簡稱。
- 分析影像用的 `POST /v1/recognize` 方法現在是 [`POST /v2/classify` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window} 方法。`labels_to_check` 參數重新命名為 `classifier_ids`。
- 第 1 版中用來擷取標籤清單的 `GET /v1/tag/labels` 方法，現在是用來擷取分類器清單的 [`GET /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} 方法。
- 除了擷取分類器清單之外，您也可以使用新的 [`GET /v2/classifiers/{classifier_id}` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window} 方法擷取特定分類器的詳細資料。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 讓您能使用新的 [`POST /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window} 方法建立自訂分類器。若要進一步瞭解建立自訂分類器，請參閱[建立自訂分類器](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 也讓您能使用新的 [`DELETE /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window} 方法刪除自訂分類器。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 需要 `version` 參數。請指定您要使用的 API 版本發表日期，格式為 `MM-DD-YYYY`。
