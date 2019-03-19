---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

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

<!-- Link definitions -->

[api-ref-text]: https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text

# 自然场景中的文本识别 (Beta)
{: #recognize-text}

使用 {{site.data.keyword.visualrecognitionshort}} Beta Text 模型可检测并识别图像中的英语文本。Text 模型旨在识别图像中的场景文本，而不是文档中更密集的文本。

Text 模型是专用 Beta 功能，您必须具有来自 {{site.data.keyword.IBM_notm}} 的许可权才能调用此模型。[请求访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://datasciencex.typeform.com/to/nU6efl){: new_window}。有关 Beta 功能的更多信息，请参阅[发行说明](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)。
{: important}

Text 模型识别短文本字符串的效果最好。例如，Text 模型的一个常见用途是读取符号。

![围绕已识别单词的带边界框的路标。Ashim D’Silva 在 Unsplash 上提供的照片](images/walk-signal-detection.png) ![在路标图像中检测到的单词和置信度分数](images/walk-signal-response.png)

白色框表明模型在图像中识别的每个单词。

## 响应
{: #recognize-text-response}

响应包括检测到的字符串，并且该字符串中的每个单词使用以下信息确定：

- 识别的单词。
- 分数，用于指示识别单词的置信度。
- 围绕单词的边框的位置。此框指示单词在图像中的位置。
- 检测到的单词所在行的行号。

## 良好文本识别准则
{: #recognize-text-guidelines}

图像中的文字符合以下准则时，可以更好地进行识别：

- 文本以完整单词为主，而不是一串字母，如产品代码。模型识别的是单词，而不是单个字符，并可能会丢弃单字母“单词”或数字。
- 文本以标准字体印刷，而不是高度风格化字体。例如，可能无法识别牌照或电影海报标题中的文本。同样，手写文本也可能无法识别。
- Text 模型主要是用英语单词训练的。因此，不大可能识别其他语言的文本。

## 后续步骤
{: #recognize-text-next-steps}

- [执行调用](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text)以识别图像中的文本。
- 熟悉 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")][api-ref-text]{: new_window} 中的 API。
