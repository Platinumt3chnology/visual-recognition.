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

# Migrating to {{site.data.keyword.visualrecognitionshort}} from {{site.data.keyword.alchemyvisionshort}}

On May 19, 2016, the {{site.data.keyword.alchemyvisionshort}} service was deprecated and its functionality became a part of {{site.data.keyword.visualrecognitionshort}} (GA). To migrate an application deployed on {{site.data.keyword.Bluemix_notm}} from the {{site.data.keyword.alchemyvisionshort}} service to the {{site.data.keyword.visualrecognitionshort}} service, update your code.
{: shortdesc}

The following differences between {{site.data.keyword.alchemyvisionshort}} and {{site.data.keyword.visualrecognitionshort}} might affect your application code:

- **Classes and classifiers:** In {{site.data.keyword.alchemyvisionshort}}, analyzed images were labelled with "tags". In {{site.data.keyword.visualrecognitionshort}}, "tags" are called "classes". Groups of classes are called "classifiers". All default tags from {{site.data.keyword.alchemyvisionshort}} are still available as classes in {{site.data.keyword.visualrecognitionshort}}.
- **Custom classifiers:** {{site.data.keyword.visualrecognitionshort}} allows you to train and create custom classifiers and classes.
- **Batch input:** In {{site.data.keyword.visualrecognitionshort}}, you can now classify batches of images or image URLs by submitting image files in a compressed (.zip) file or a single image URL in a JSON string.
- **Specify language:** In {{site.data.keyword.alchemyvisionshort}}, you specified the language of a tagging call as a query parameter. In {{site.data.keyword.visualrecognitionshort}}, you specify the language of a classify call in the `Accept-Language` header.
- **Endpoints:** The following {{site.data.keyword.alchemyvisionshort}} functionality is included in new endpoints in the GA release of {{site.data.keyword.visualrecognitionshort}}:

| Functionality | {{site.data.keyword.alchemyvisionshort}} endpoint (deprecated) | {{site.data.keyword.visualrecognitionshort}} endpoint (GA) |
|---------------|--------------------|----------------|
| Tag images with built-in classifiers | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Detect faces, age range, and gender | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Extract main image from HTML or a website URL | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | You can supply an image by URL to the `/v3/classify` and `/v3/detect_faces` methods, not through a standalone endpoint. |
