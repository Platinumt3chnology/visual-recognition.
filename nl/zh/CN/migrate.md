---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 迁移
{: #migrating}

要迁移当前模型（分类器），请供应 {{site.data.keyword.visualrecognitionshort}} 服务的新实例。对于定制模型，通过使用来自先前模型的图像创建另一个模型（分类器），从而重新训练模型。
{: shortdesc}

2018 年 5 月 23 日**之前**创建的 {{site.data.keyword.visualrecognitionfull}} 服务实例具有主机 URL `gateway-a.watsonplatform.net`。必须将这些实例迁移到新的 {{site.data.keyword.visualrecognitionshort}} 服务实例以继续进行使用。
{: deprecated}

1.  创建 {{site.data.keyword.visualrecognitionshort}} 服务的另一个实例：
    1.  转至目录中的 [{{site.data.keyword.visualrecognitionshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 页面。
    1.  选择一个套餐，然后单击**创建**。
1.  复制新凭证以向服务实例进行认证：
    1.  在**管理**页面上，单击**显示凭证**。
    1.  复制 `AIP 密钥`值。
1.  在 {{site.data.keyword.visualrecognitionshort}} 服务的新实例中，[重新创建并训练定制模型](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)。
1.  修改服务的调用方式。

    针对服务实例提供 Identity and Access Management (IAM) 密钥或访问令牌。令牌提供更高的安全性，因为它们必须定期进行更新，而且支持每个调用中未嵌入服务凭证的请求。API 密钥使用基本认证，并且不会到期。

    - 有关令牌的更多信息，请参阅[使用 IAM 令牌进行认证](/docs/services/watson?topic=watson-iam#iam)。
    - 有关使用 IAM API 密钥的更多信息，请参阅 [API 参考](https://{DomainName}/apidocs/visual-recognition/#authentication)。
