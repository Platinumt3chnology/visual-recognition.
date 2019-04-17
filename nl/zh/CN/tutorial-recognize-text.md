---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-17"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# 识别图像中的文本
{: #tutorial-recognize-text}

本教程将指导您如何首次使用 {{site.data.keyword.visualrecognitionshort}} Beta Text 模型来检测和识别图像中的英语文本。
{: shortdesc}

Text 模型是专用 Beta 功能，您必须具有来自 {{site.data.keyword.IBM_notm}} 的许可权才能调用此模型。[请求访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://datasciencex.typeform.com/to/nU6efl){: new_window}。有关 Beta 功能的更多信息，请参阅[发行说明](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)。
{: important}

## 开始之前
{: #tutorial-recognize-text-prerequisites}

1.  转至 {{site.data.keyword.Bluemix_notm}}“目录”中的 [{{site.data.keyword.visualrecognitionshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 页面。
    1.  注册免费的 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
    1.  单击**创建**。
- 复制凭证以向服务实例进行认证：
    1.  单击**显示**以查看凭证。
    1.  复制 **API 密钥**值。

## 步骤 1：识别图像中的文本
{: #tutorial-recognize-text-recognize-text}

1.  发出以下调用以识别[图像 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window} 中的文本。将 `{your_api_key}` 替换为先前复制的 API 密钥值。

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    响应包含已识别的文本、文本中单词的位置以及每个单词的置信度分数。位置信息可用于在单词周围绘制边界框。

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 后续步骤

您已经对如何识别图像中的文本有了基本了解。进一步探索。

- 阅读[概述](/docs/services/visual-recognition?topic=visual-recognition-recognize-text#recognize-text)。
- 探索 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window} 中的 Text 模型方法。

### 出处
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}，由 [Lubo Minar ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://unsplash.com/@bubo){: new_window} 在 [Unsplash ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} 上发布。此图像未进行任何更改。
