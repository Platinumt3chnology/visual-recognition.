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

# 移轉
{: #migrating}

若要移轉現行模型（分類器），請佈建新的 {{site.data.keyword.visualrecognitionshort}} 服務實例。對於自訂模型，請使用較早模型中的影像建立另一個模型（分類器），來重新訓練模型。
{: shortdesc}

2018 年 5 月 23 日**之前**建立的 {{site.data.keyword.visualrecognitionfull}} 服務將具有主機 URL `gateway-a.watsonplatform.net`。您必須將這些實例移轉至新的 {{site.data.keyword.visualrecognitionshort}} 服務實例，才能夠繼續使用它們。
{: deprecated}

1.  建立另一個 {{site.data.keyword.visualrecognitionshort}} 服務實例：
    1.  移至型錄中的 [{{site.data.keyword.visualrecognitionshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 頁面。
    1.  選取方案，然後按一下**建立**。
1.  複製新認證來向服務實例進行鑑別：
    1.  在**管理**頁面中，按一下**顯示認證**。
    1.  複製 `API Key` 值。
1.  在新的 {{site.data.keyword.visualrecognitionshort}} 服務實例中[重建和訓練您的自訂模型](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)。
1.  修改您的服務的呼叫方式。

    您要提供您的服務實例的 Identity and Access Management (IAM) 金鑰或存取記號。記號提供更大的安全性，因為它們必須定期更新，而且支援要求時不需要在每個呼叫中內含服務認證。API 金鑰使用基本鑑別而且不會到期。

    - 如需記號的相關資訊，請參閱[使用 IAM 記號鑑別](/docs/services/watson?topic=watson-iam#iam)。
    - 如需使用 IAM API 金鑰的相關資訊，請參閱 [API 參考資料](https://{DomainName}/apidocs/visual-recognition/#authentication)。
