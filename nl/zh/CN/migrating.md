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

# 从 {{site.data.keyword.alchemyvisionshort}} 迁移到 {{site.data.keyword.visualrecognitionshort}}

2016 年 5 月 19 日，{{site.data.keyword.alchemyvisionshort}} 服务已弃用，并且其功能已成为 {{site.data.keyword.visualrecognitionshort}} (GA) 的一部分。要将在 {{site.data.keyword.Bluemix_notm}} 上部署的应用程序从 {{site.data.keyword.alchemyvisionshort}} 服务迁移到 {{site.data.keyword.visualrecognitionshort}} 服务，请更新代码。
{: shortdesc}

{{site.data.keyword.alchemyvisionshort}} 和 {{site.data.keyword.visualrecognitionshort}} 之间的下列差异可能会影响应用程序代码：

- **类和分类器：**在 {{site.data.keyword.alchemyvisionshort}} 中，已分析的图像会使用“标记”进行标记。在 {{site.data.keyword.visualrecognitionshort}} 中，“标记”称为“类”。一组类称为“分类器”。{{site.data.keyword.alchemyvisionshort}} 中的所有缺省标记仍可作为类在 {{site.data.keyword.visualrecognitionshort}} 中使用。
- **定制分类器：**{{site.data.keyword.visualrecognitionshort}} 支持培训和创建定制分类器和类。
- **批量输入：**在 {{site.data.keyword.visualrecognitionshort}} 中，现在可以通过在一个压缩 (.zip) 文件中或 JSON 字符串的单个图像 URL 中提交多个文件，对批量图像或图像 URL 分类。
- **指定语言：**在 {{site.data.keyword.alchemyvisionshort}} 中，已将 tagging 调用的语言指定为查询参数。在 {{site.data.keyword.visualrecognitionshort}} 中，可在 `Accept-Language` 头中指定 classify 调用的语言。
- **端点：**以下 {{site.data.keyword.alchemyvisionshort}} 功能包含在 {{site.data.keyword.visualrecognitionshort}} GA 发行版的新端点中：

| 功能| {{site.data.keyword.alchemyvisionshort}} 端点（已弃用）| {{site.data.keyword.visualrecognitionshort}} 端点 (GA) |
|---------------|--------------------|----------------|
| 使用内置分类器标记图像| `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| 检测人脸、年龄范围和性别| `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| 从 HTML 或 Web 站点 URL 中抽取主图像| `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | 可以通过 URL 向 `/v3/classify` 和 `/v3/detect_faces` 方法提供图像，而不通过独立端点提供。|
