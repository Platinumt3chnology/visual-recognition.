---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# 資訊安全
{: #information-security}

IBM 致力於為我們的客戶及合作夥伴提供創新的資料隱私權、安全及控管解決方案。
{: shortdesc}

**注意事項：**客戶須負責確保本身遵循各種法令規章，包括「歐盟一般資料保護規範」。有關任何可能影響「客戶」業務之相關法令規章之確認與解釋，以及任何「客戶」為遵循該等法令規章所需採取之行動，「客戶」應自行負責向法律顧問取得諮詢意見。

本文所述的產品、服務及其他功能並不適合所有客戶情況，而且可用性可能受到限制。IBM 不提供法律、會計或審核意見，亦不聲明或保證其服務或產品可確保「客戶」符合任何法令規章。如果您需要針對建立的 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 資源要求 GDPR 支援

- 在歐盟之內，請參閱[針對在歐盟建立的 IBM Cloud Watson 資源提出支援要求](/docs/services/watson?topic=watson-gdpr-sar#request-EU)。
- 在歐盟之外，請參閱[針對歐盟之外的資源提出支援要求](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU)。

## 歐盟一般資料保護規範 (GDPR)
{: #gdpr}

IBM 致力於為我們的客戶及合作夥伴提供創新的資料隱私權、安全及控管解決方案，以協助他們達成 GDPR 合規性。

進一步瞭解 IBM 本身 GDPR 整備過程以及 GDPR 功能與產品與服務，以支援您完成 [這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ibm.com/gdpr){: new_window} 合規程序。

## 在 {{site.data.keyword.visualrecognitionshort}} 中標示及刪除資料
{: #gdpr-visrec}

### GDPR 安全移轉
{: #gdpr-visrec-update}

- 在 **2018 年 5 月 22 日**之前建立的所有 {{site.data.keyword.visualrecognitionfull}} 服務實例，都不適合需要符合歐盟一般資料保護規範 EU 2016/679 (GDPR) 的客戶。
- 受到 GDPR 約束的客戶需要[移轉至新的 {{site.data.keyword.visualrecognitionshort}} 服務實例](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)（於 **2018 年 5 月 22 日**提供使用）並對 {{site.data.keyword.visualrecognitionshort}} 服務採用新合約。
- 客戶需要佈建新的 {{site.data.keyword.visualrecognitionshort}} 服務，並產生*新鑑別金鑰*，以利用新的 {{site.data.keyword.visualrecognitionshort}} 服務。
- 如果客戶未佈建新的 {{site.data.keyword.visualrecognitionshort}} 服務，您要確認 IBM 未代為處理受到 GDPR 約束的客戶的「個人資料」。
- 未在 2018 年 5 月 22 日和 2018 年 10 月 1 日之間移至新的 {{site.data.keyword.visualrecognitionshort}} 服務的客戶的資料將會被刪除。

### 標示資料

如果您需要從具有多個客戶的 {{site.data.keyword.visualrecognitionshort}} 服務實例移除個別客戶的資料，您首先需要針對每個可能提供資料的個別客戶，將該資料和唯一的客戶 ID 建立關聯。

若要針對使用 **Create a classifier** 方法傳送的任何資料指定客戶 ID，請將 **X-Watson-Metadata: customer_id** 內容包含在要求標頭中。下列範例將客戶 ID `my_ID` 和要求建立關聯：

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

客戶 ID 字串支援多位元組字元。字元必須是 URL 編碼，而且要在訓練期間位於標頭中，以及在刪除期間位於查詢參數中。ID 可以包含英數和底線 (``_``) 字元。不支援下列字元：``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + 空格``。

您要負責建立客戶 ID 值，並確保每個值都是唯一。
{: important}

### 刪除標示的資料

若要刪除和客戶 ID 關聯的所有資料，請使用 **Delete labeled data** 方法。您傳遞 `customer_id={id}` 字串作為要求的查詢參數。下列範例會刪除客戶 ID `my_ID` 的所有資料：

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

**Delete labeled data** 方法會刪除與指定客戶 ID 相關聯的的所有資料，而且不會考量新增該資訊時使用何種方法。如果沒有任何與客戶 ID 相關聯的資料，此方法沒有作用。

刪除要求會以批次方式處理，可能需要長達 24 小時才能完成。
{: tip}

### 支援
{: #gdpr-visrec-support}

請將您的問題直接提交給您的客戶代表，或者直接向 [https://ibm.biz/ibmcloudsupport ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/ibmcloudsupport){: new_window} 尋求支援。
