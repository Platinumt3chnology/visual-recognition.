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

# 機密保護
{: #information-security}

IBM は、お客様やパートナーに、データ・プライバシー、セキュリティー、およびガバナンスに関する革新的なソリューションを提供します。
{: shortdesc}

**注意:**
お客様自身が欧州連合の一般データ保護規則を含む各種法令を遵守するために必要な措置を講ずるのはお客様の責任です。 お客様のビジネスに影響を及ぼす可能性のある関連法令の特定およびそれらの解釈、ならびにかかる関連法令を遵守するためにお客様が講ずるべき必要措置に関する助言は、お客様の責任により適格な弁護士から得るものとします。

本書に記載の製品、サービス、および他の機能が、すべてのお客様の状況に適しているとは限らず、使用する際に制約を受ける場合があります。 IBM は、法律、会計または監査に関する助言を提供することはしませんし、IBM のサービスまたは製品が、お客様のあらゆる法令遵守の裏付けとなる表明または保証もいたしません。
以下の場所で作成された {{site.data.keyword.cloud}} {{site.data.keyword.watson}} リソースの GDPR サポートを要請する必要がある場合の手順

- EU 内の場合、[Requesting support for IBM Cloud Watson resources created in the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-EU) を参照してください。
- EU 外の場合、[Requesting support for resources outside the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU) を参照してください。

## EU 一般データ保護規則 (GDPR)
{: #gdpr}

IBM は、お客様やパートナーに、データ・プライバシー、セキュリティー、およびガバナンスに関する革新的なソリューションを提供して、GDPR に対する準拠が完了するまでの過程を支援します。

GDPR に対する準備を整えるための IBM 独自の過程と、準拠が完了するまでの過程をサポートする弊社の GDPR 機能とオファリングについて詳しくは、[ここ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/gdpr){: new_window} を参照してください。

## {{site.data.keyword.visualrecognitionshort}} でのデータのラベル付けと削除
{: #gdpr-visrec}

### GDPR に伴うセキュリティー・マイグレーション
{: #gdpr-visrec-update}

- **2018 年 5 月 22 日**より前に作成された、{{site.data.keyword.visualrecognitionfull}} のすべてのサービス・インスタンスは、EU 一般データ保護規則 (GDPR) (規則 2016/679) への準拠が必要なお客様には適していません。
- GDPR の対象となるお客様は、**2018 年 5 月 22 日**から使用可能になる[新しい {{site.data.keyword.visualrecognitionshort}} サービス・インスタンスへのマイグレーション](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)と、{{site.data.keyword.visualrecognitionshort}} サービスの新しいご使用条件への同意が必要です。
- お客様が新しい {{site.data.keyword.visualrecognitionshort}} サービスを使用するためには、新しい {{site.data.keyword.visualrecognitionshort}} サービスのプロビジョンと*新しい認証キー* の生成が必要です。
- 新しい {{site.data.keyword.visualrecognitionshort}} サービスをプロビジョンしない場合、お客様は、GDPR が適用される個人データをお客様に代わって IBM が処理することはないということを承認したことになります。
- 2018 年 5 月 22 日から 2018 年 10 月 1 日までの間に新しい {{site.data.keyword.visualrecognitionshort}} サービスに移行しない場合、お客様のデータは削除されます。

### データのラベル付け

複数の顧客が参加している {{site.data.keyword.visualrecognitionshort}} サービス・インスタンスから 1 人の顧客のデータを削除する必要がある場合は、最初に、データを提供した可能性のある個別の顧客ごとに、そのデータを固有の顧客 ID と関連付ける必要があります。

**Create a classifier** メソッドで送信されるデータの顧客 ID を指定するには、要求ヘッダーに **X-Watson-Metadata: customer_id** プロパティーを含めます。以下の例では、顧客 ID `my_ID` を要求に関連付けています。

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

顧客 ID のストリングでは、マルチバイトの文字がサポートされています。これらの文字は、ヘッダー内 (トレーニング時) と照会パラメーター内 (削除時) の両方で、URL エンコードされている必要があります。ID には、英数字およびアンダースコアー (``_``) 文字を含めることができます。``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + スペース`` の文字はサポートされていません。

顧客 ID の値を作成し、それらが固有の値になるようにする責任はお客様にあります。
{: important}

### ラベル付きデータの削除

顧客 ID に関連付けられているすべてのデータを削除するには、**Delete labeled data** メソッドを使用します。ストリング `customer_id={id}` を照会パラメーターとして要求と一緒に渡します。以下の例は、顧客 ID `my_ID` のすべてのデータを削除します。

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

**Delete labeled data** メソッドは、情報を追加したメソッドが何であるかにかかわらず、指定された顧客 ID に関連付けられたすべてのデータを削除します。顧客 ID に関連付けられたデータがない場合は、このメソッドを実行しても何も効果がありません。

削除要求はバッチ処理され、完了するまでに最長で 24 時間かかる場合があります。
{: tip}

### サポート
{: #gdpr-visrec-support}

ご質問がある場合は、お客様のアカウント担当者にお問い合わせいただくか、[https://ibm.biz/ibmcloudsupport ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/ibmcloudsupport){: new_window} に直接サポートをご依頼ください。
