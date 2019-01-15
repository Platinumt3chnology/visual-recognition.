---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-15"

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

# Supported languages

## Classify images
{: #classify}

The **Classify images** method of {{site.data.keyword.visualrecognitionfull}} supports English (`en`), Arabic (`ar`), German (`de`), Spanish (`es`), French (`fr`), Italian (`it`), Japanese (`ja`), Korean (`ko`), Portuguese (Brazilian) (`pt-br`), Chinese (Simplified) (`zh-cn`), and Chinese (Traditional) (`zh-tw`).

The languages work with the output classes of all the built-in models: `default` (also called the General model), `food`, and `explicit`.

For details about the API call, see the **Classify images** method in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

## Detect faces
{: #detect_faces}

The **Detect faces** methods return translations of the English words for gender ("Male" and "Female") in the response. Set the language with the **Accept-Language** request header.

For details, see the **Detect faces** methods in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

