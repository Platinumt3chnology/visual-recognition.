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

# 版本注意事項

有下列的服務新特性及變更可用。
{: shortdesc}

## 測試版特性
{: #beta}

{{site.data.keyword.IBM_notm}} 發表了分類為測試版的服務、特性及語言支援供您評估。這些特性可能不穩定、經常變更，且可能在通知之後很快停止。測試版特性也可能不提供如一般可用特性提供的相同效能或相容性層次，且不適用於正式作業環境。測試版特性只在 [developerWorks Answers ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} 上受支援。

## 變更
{: #changelog}

有下列的服務新特性及變更可用。


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
      <img src="images/antarctica-iceberg.jpg" alt="南極洲的冰山">
      <table>
        <tr>
          <th>原始標籤</th>
          <th>其他標籤</th>
        </tr>
        <tr>
          <td>
          標籤：iceberg<br/>
          評分：0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          標籤：ice mass<br/>
          評分：0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          標籤：nature<br/>
          評分：0.770</td>
        </tr>
        <tr>
          <td>
          標籤：blue color<br/>
          評分：0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          標籤：alabaster color<br/>
          評分：0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>測試版中提供的新明確模型</strong>
      <p>
        在測試版中發表的明確模型會分類影像是否包含色情內容且不適合一般用途。您可以包含明確模型與其他模型，進行結合分析。例如，若要在您的要求中同時包含 `default` 及 `explicit` 分類器 ID，以傳回影像標籤及影像是否包含明確內容。
      <p>
        如需 API 呼叫的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image) 中的**分類影像**方法，或在 [API 瀏覽器 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify) 中嘗試模型。
      </p>
    </li>
    <li>
      <strong>支援較大的檔案大小</strong>
      <p>
        <strong>分類影像</strong>方法現在支援最多 10 MB 的影像檔，以及最多 100 MB 的 .zip 檔。
    </li>
    <li>
      <strong>傳遞分類器 ID 時需要陣列</strong>
      <p>
        API 現在會在您在**分類影像**方法的 **parameters** 物件之中傳入 `classifier_ids` 時施行陣列。先前，您可以用字串形式傳遞分類器 ID。如需相關資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image) 中的參數說明和範例檔案。
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

    如需 API 呼叫的詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 的**分類影像**方法。

### 2017 年 5 月 16 日
{: #16may2017}

- **新的 food 分類器可用：測試版**

    新的測試版食物識別模型提供食物項目影像的加強特性和正確性。**分類影像**方法容許您將這個新的分類器 "food" 新增至 `classifier_ids` 參數。

### 2017 4 月 5 日
{: #5april2017}

- **新的 {{site.data.keyword.visualrecognitionshort}} 工具可用：測試版**

    新的測試版特性 － {{site.data.keyword.visualrecognitionshort}} 工具，提供於 [https://watson-visual-recognition.ng.bluemix.net/ ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}。此工具有助於您更輕鬆地使用 {{site.data.keyword.visualrecognitionshort}} 服務。藉由輸入 {{{site.data.keyword.cloud_notm}} API 金鑰，您可以使用 GUI 存取「一般標記」和「臉孔偵測」特性，以及無縫地建立、重新訓練及刪除與 API 金鑰相關聯的自訂分類器，而不需要撰寫程式碼。

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

    IBM 已降低 {{site.data.keyword.visualrecognitionshort}} 服務上之自訂分類器的定價，並增加免費方案提供的內容。如需相關資訊，請參閱 [{{site.data.keyword.visualrecognitionshort}} 定價頁面](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)。

### 2016 年 10 月 7 日
{: #7october2016}

- **臉孔偵測加強功能**

    服務有新的臉孔偵測演算法，它改善了 `GET` 及 `POST /v3/detect_faces` 方法的回應。服務調整了低信任度年齡、名字和性別的臉孔偵測過濾。因此，會找到更多臉孔，並傳回更大範圍的信任度。

### 2016 年 9 月 8 日
{: #8september2016}

- **相似性搜尋測試版**

    使用者現在可以上傳自己的影像集合、使用影像搜尋該集合中的類似影像，然後服務會傳回前 100 名最類似的影像。相似性搜尋可以用於任何用途，使用者可以用最多每個集合一百萬張影像來自訂訓練服務。如需使用新的相似性搜尋功能的相關資訊，請參閱[指導教學](/docs/services/visual-recognition/tutorial-collections.html)，以及 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 頁面。

- **文字辨識現在為封閉測試版**

    `POST` 及 `GET /v3/recognize_text` 方法已回到封閉測試版。IBM 期待繼續支援使用服務的測試版用戶端，目前並無計畫進行另一個開放測試版。

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
- **臉孔偵測：**使用 `POST` 或 `GET /v3/detect_faces` 方法，以偵測影像中的臉孔，並取得其相關資訊，例如臉孔在影像中的位置，以及每張臉的預估年齡範圍和性別。服務也可以用名字識別名人，且可以提供知識圖形以便您執行有趣的聚集，成為更高層次的概念。
- **多資料類型自訂分類器：**您現在可以建立並訓練高度特殊化的分類器（由數個類別定義）。例如，您可以建立 "new\_red\_car" 分類器，它由類別 "new\_cars" 及 "red\_cars" 所定義。若要進一步瞭解建立多資料類型分類器，請參閱[訓練資料的結構](/docs/services/visual-recognition/customizing.html#structure)。
- **非同步訓練：**自訂分類器的訓練現在是非同步的，因此訓練呼叫會快速完成，而您的自訂分類器則繼續在背景中學習。若要檢查自訂分類器的訓練狀態，並找出它何時可以使用，請呼叫 `GET /v3/classifiers/{classifier_id}` 方法，然後檢查 `status` 回應參數。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 服務的最新版本是岔斷變更，引進了新版本的 {{site.data.keyword.visualrecognitionshort}} API（第 2 版）。第 1 版的 {{site.data.keyword.visualrecognitionshort}} 服務可以使用到服務結束測試版為止。

若要立即開始使用第 2 版的 API，請瞭解並更新您的程式碼以反映下列變更：

- 在第 1 版的服務中，您依標籤來分析影像。在第 2 版的服務中，標籤稱為**分類器**。分類器有以 `classifier_id` 參數指出的唯一分類器 ID，還有以 `name` 參數指出的簡稱。
- 分析影像用的 `POST /v1/recognize` 方法現在是 [`POST /v2/classify` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 方法。`labels_to_check` 參數重新命名為 `classifier_ids`。
- 第 1 版中用來擷取標籤清單的 `GET /v1/tag/labels` 方法，現在是用來擷取分類器清單的 [`GET /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} 方法。
- 除了擷取分類器清單之外，您也可以使用新的 [`GET /v2/classifiers/{classifier_id}` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window} 方法擷取特定分類器的詳細資料。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 讓您能使用新的 [`POST /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window} 方法建立自訂分類器。若要進一步瞭解建立自訂分類器，請參閱[建立自訂分類器](/docs/services/visual-recognition/customizing.html)。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 也讓您能使用新的 [`DELETE /v2/classifiers` ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window} 方法刪除自訂分類器。
- 第 2 版的測試版 {{site.data.keyword.visualrecognitionshort}} API 需要 `version` 參數。請指定您要使用的 API 版本發表日期，格式為 `MM-DD-YYYY`。
