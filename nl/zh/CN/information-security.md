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

# 信息安全
{: #information-security}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全性和监管解决方案。
{: shortdesc}

**声明：**
客户应负责确保自身遵守各种法律和法规，包括《欧盟一般数据保护条例》。客户须自行负责就可能会影响客户业务的任何相关法律法规的认定和解释以及客户为了遵守此类法律法规需要采取的任何行动，从合格的法律顾问那里获得意见。

此处描述的产品、服务和其他功能并不适用于所有客户情形，并且在可用性方面可能有限制。IBM 不会提供法律、会计或审计建议，也不会表述或保证其服务或产品将确保客户遵守任何法律或法规。如果需要为创建的 {{site.data.keyword.cloud}}{{site.data.keyword.watson}} 资源请求 GDPR 支持

- 在欧盟，请参阅[请求对欧盟内创建的 IBM Cloud Watson 资源的支持](/docs/services/watson?topic=watson-gdpr-sar#request-EU)。
- 在欧盟以外的地区，请参阅[请求对欧盟以外的资源的支持](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU)。

## 欧盟一般数据保护条例 (GDPR)
{: #gdpr}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全性和监管解决方案，以帮助他们完成 GDPR 合规旅程。

在[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/gdpr) 了解有关 IBM 自己的 GDPR 就绪性旅程以及支持您合规旅程的 GDPR 功能和产品的更多信息。{: new_window}.

## 标注和删除 {{site.data.keyword.visualrecognitionshort}} 中的数据
{: #gdpr-visrec}

### GDPR 安全性迁移
{: #gdpr-visrec-update}

- **2018 年 5 月 22 日**前创建的所有 {{site.data.keyword.visualrecognitionfull}} 服务实例不适合需要遵守欧盟一般数据保护条例（EU 2016/679，GDPR）的客户。
- 受 GDPR 约束的客户需要[迁移到 **2018 年 5 月 22 日**可用的新 {{site.data.keyword.visualrecognitionshort}} 服务实例](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)并针对 {{site.data.keyword.visualrecognitionshort}} 服务采用新协议。
- 客户需要供应新的 {{site.data.keyword.visualrecognitionshort}} 服务并生成*新的认证密钥*以利用新的 {{site.data.keyword.visualrecognitionshort}} 服务。
- 如果客户未供应新的 {{site.data.keyword.visualrecognitionshort}} 服务，那么您确认 IBM 不会代表受 GDPR 约束的客户处理任何个人数据。
- 对于未在 2018 年 5 月 22 日至 2018 年 10 月 1 日之间移至新的 {{site.data.keyword.visualrecognitionshort}} 服务的客户，其数据将被删除。

### 标注数据

如果需要从包含多个客户的 {{site.data.keyword.visualrecognitionshort}} 服务实例除去单个客户的数据，首先需要将该数据与可能提供了数据的每个个人的唯一客户标识相关联。

要针对使用 **Create a classifier** 方法发送的任何数据指定客户标识，请在请求头中包含 **X-Watson-Metadata: customer_id** 属性。以下示例将客户标识 `my_ID` 与请求相关联：

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

针对客户标识字符串支持多字节字符。训练期间头中和删除期间查询参数中的字符必须采用 URL 编码。标识可包含字母数字和下划线 (``_``) 字符。不支持以下字符：``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + 和空格``。

您负责创建客户标识值，并确保每个值唯一。
{: important}

### 删除标记的数据

要删除与客户标识相关联的所有数据，请使用 **Delete labeled data** 方法。作为查询参数随请求一起传递字符串 `customer_id={id}`。以下示例删除客户标识 `my_ID` 的所有数据：

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

**Delete labeled data** 方法删除与指定的客户标识相关联的所有数据，无论添加信息所用的方法是什么。如果没有数据与客户标识相关联，那么该方法无效。

删除请求将进行批量处理，可能需要最长 24 小时才能完成。
{: tip}

### 支持
{: #gdpr-visrec-support}

向帐户代表提问，或者通过 [https://ibm.biz/ibmcloudsupport ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/ibmcloudsupport){: new_window} 直接联系支持人员。
