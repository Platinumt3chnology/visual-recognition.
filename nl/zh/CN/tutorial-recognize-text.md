---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# 识别图像中的文本

{: shortdesc}

## 开始之前
{: #copy-credentials}

使用您在本教程的“入门教程”中复制的凭证。如果没有创建服务实例，请执行[开始之前](/docs/services/visual-recognition/getting-started.html#prerequisites)部分中的那些步骤。

## 步骤 1：识别图像中的文本
{: #recognize-text}

1.  下载样本 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">... <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 示例图像
1.  发出以下命令调用 `POST /v3/recognize_text` 方法来上传和分析该图像。如果使用自己的图像，那么最大大小为 2 MB：
    - 将 `{api-key}` 替换为早先复制的服务凭证。
    - 修改 images\_file 的位置，使其指向映像的保存位置。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    响应包括位置、估计年龄、性别、身份和类型层次结构（如果服务识别到该人脸）以及每项的分数。

    分数范围为 0-1，分数越高，表示相关性越大。所有人脸都会检测到，但对于有 10 张以上人脸的图像，返回的年龄和性别置信度分数可能会为 0。


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## 后续步骤

您已经对如何使用 {{site.data.keyword.visualrecognitionshort}} 的缺省分类器有了基本的了解。现在，可以更深入地探索以下内容：

- 阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中有关 API 的信息。

### 出处
{: #attributions}

此页面上使用的所有图像均来自 Flikr，并依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。这些图像未进行任何更改。
