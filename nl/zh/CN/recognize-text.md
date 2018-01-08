---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# 自然场景中的文本识别

使用 Beta 文本模型可检测并识别图像中的英文文本。文本模型旨在识别图像中的印刷场景文本，而不是文档中更密集的文本。

文本模型是 Beta 功能，不适用于生产环境。有关更多信息，请参阅[发行说明](/docs/services/visual-recognition/release-notes.html#beta)中的“Beta 功能”。
{: tip}

文本模型识别短文本字符串的效果最好。例如，文本模型的一个常见用途是读取路标。

![检测到有边框围绕的路标中的单词](images/road-sign-text-detection.png)

![路标图像中检测到的单词和置信度分数](images/road-sign-text-response.png)

白色框表明模型在图像中检测到的每个单词。

## 响应

响应包括检测到的字符串，并且该字符串中的每个单词使用以下信息确定：

- 检测到的单词
- 分数，用于指示检测到的单词的准确性置信度。
- 围绕单词的边框的位置。此框指示单词在图像中的位置。
- 检测到的单词所在行的行号。

## 良好文本识别准则

图像中的文字符合以下准则时，可以更好地进行识别：

- 文本以完整单词为主，而不是一串字母，如产品代码。模型识别的是单词，而不是单个字符，并可能会丢弃单字母“单词”或数字。
- 文本以标准字体印刷，而不是高度风格化字体。例如，可能无法识别牌照或电影海报标题中的文本。同样，手写文本也可能无法识别。
- 文本至少占图像的 5% 。
- 文字倾斜不超过水平 45 度。Beta 文本模型可读取 EXIF 标记并旋转图像。但为了获得最佳吞吐量，请发送不需要服务进行旋转的图像（EXIF **方向**标记设置为 `1`）。
- 文本模型是用英语单词培训的。因此，可能无法识别其他文本语言。

## 后续步骤

熟悉 [API Explorer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window} 中的 API

如果您对文本模型有任何疑问或意见，请通过 kgong@us.ibm.com 与 Kevin Gong 联系。

---

转至主[文档](/docs/services/visual-recognition/index.html)。
