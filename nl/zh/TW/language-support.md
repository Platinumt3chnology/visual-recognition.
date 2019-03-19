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

# 支援語言

## Classify images
{: #language-support}

{{site.data.keyword.visualrecognitionfull}}的 **Classify images** 方法支援英文 (`en`)、阿拉伯文 (`ar`)、德文 (`de`)、西班牙文 (`es`)、法文 (`fr`)、義大利文 (`it`)、日文 (`ja`)、韓文 (`ko`)、葡萄牙文（巴西）(`pt-br`)、中文（簡體）(`zh-cn`)，以及中文（繁體）(`zh-tw`)。

這些語言可和所有內建模型的輸出類別搭配運作：`default`（也稱為「General 模型」）、`food` 和 `explicit`。

如需 API 呼叫的詳細資料，請參閱 [API 參考資料![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window} 中的 **Classify images** 方法。

## Detect faces
{: #detect_faces}

**Detect faces** 方法會在回應中傳回性別英文字（"Male" 和 "Female"）的翻譯。請使用 **Accept-Language** 要求標頭來設定語言。

如需詳細資料，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window} 中的 **Detect faces** 方法。
