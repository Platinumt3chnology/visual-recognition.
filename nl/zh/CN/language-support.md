---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition languages,language support,supported languages

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

# 支持的语言
{: #language-support-top}

## 图像分类
{: #language-support}

{{site.data.keyword.visualrecognitionfull}} 的 **Classify images** 方法支持英语 (`en`)、阿拉伯语 (`ar`)、德语 (`de`)、西班牙语 (`es`)、法语 (`fr`)、意大利语 (`it`)、日语 (`ja`)、韩语 (`ko`)、巴西葡萄牙语 (`pt-br`)、简体中文 (`zh-cn`) 和繁体中文 (`zh-tw`)。

这些语言处理所有内置模型的输出类：`default`（也称为“通用”模型）、`food` 和 `explicit`。

有关 API 调用的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window} 中的 **Classify images** 方法。

## 检测人脸
{: #detect_faces}

**Detect faces** 方法在响应中返回性别的英语单词（“Male”和“Female”）的翻译。使用 **Accept-Language** 请求头设置语言。

有关详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window} 中的**检测人脸**方法。
