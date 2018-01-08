---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# 從 {{site.data.keyword.alchemyvisionshort}} 移轉至 {{site.data.keyword.visualrecognitionshort}}

{{site.data.keyword.alchemyvisionshort}} 服務在 2016 年 5 月 19 日已淘汰，且其功能已成為 {{site.data.keyword.visualrecognitionshort}} (GA) 的一部分。若要將部署在 {{site.data.keyword.Bluemix_notm}} 上的應用程式，從 {{site.data.keyword.alchemyvisionshort}} 服務移轉至 {{site.data.keyword.visualrecognitionshort}} 服務，請更新您的程式碼。
{: shortdesc}

{{site.data.keyword.alchemyvisionshort}} 與 {{site.data.keyword.visualrecognitionshort}} 之間的下列差異可能會影響您的應用程式碼：

- **類別與分類器：**在 {{site.data.keyword.alchemyvisionshort}} 中，已分析的影像會使用「標籤」(tag) 標記。在 {{site.data.keyword.visualrecognitionshort}} 中，「標籤」(tag) 稱為「類別」(class)。類別的群組稱為「分類器」(classifier)。來自 {{site.data.keyword.alchemyvisionshort}} 的所有預設標籤仍可用來作為 {{site.data.keyword.visualrecognitionshort}} 中的類別。
- **自訂分類器：**{{site.data.keyword.visualrecognitionshort}} 容許您訓練及建立自訂分類器與類別。
- **批次輸入：**在 {{site.data.keyword.visualrecognitionshort}} 中，您現在分類影像或影像 URL 的批次時，可以用壓縮檔 (.zip) 提交影像檔，或用 JSON 字串中的單一影像 URL。
- **指定語言：**在 {{site.data.keyword.alchemyvisionshort}} 中，您將標記呼叫的語言指定為查詢參數。在 {{site.data.keyword.visualrecognitionshort}} 中，您是在 `Accept-Language` 標頭指定 classify 呼叫的語言。
- **端點：**下列 {{site.data.keyword.alchemyvisionshort}} 功能包含在 {{site.data.keyword.visualrecognitionshort}} GA 版本的新端點中：

| 功能| {{site.data.keyword.alchemyvisionshort}} 端點（已淘汰）| {{site.data.keyword.visualrecognitionshort}} 端點 (GA) |
|---------------|--------------------|----------------|
| 使用內建分類器標記影像| `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| 偵測臉孔、年齡範圍，以及性別| `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| 從 HTML 或網站 URL 擷取主要影像| `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | 提供影像時可以藉由 `/v3/classify` 及 `/v3/detect_faces` 方法的 URL，而不透過獨立式端點。|
