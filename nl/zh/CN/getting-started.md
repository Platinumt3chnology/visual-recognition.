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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 入门教程

本教程将指导您如何使用 {{site.data.keyword.visualrecognitionfull}} 中的一些内置分类器对图像分类，然后检测图像中的人脸。
{: shortdesc}

## 开始之前
{: #prerequisites}

- 创建服务的实例：
    - {: download} 如果看到此内容，说明您已创建服务实例。现在，请获取凭证。
    - 通过服务创建项目：
        1.  转至 {{site.data.keyword.watson}} 开发者控制台[服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/developer/watson/services){: new_window} 页面。
        1.  选择 {{site.data.keyword.visualrecognitionshort}}，单击**添加服务**，然后注册免费 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
        1.  输入 `vision-tutorial` 作为项目名称，然后单击**创建项目**。
- 复制凭证以向服务实例进行认证：
    - {: download} 在服务仪表板（即在查看的内容）中：
        1.  单击**服务凭证**选项卡。
        1.  单击**操作**下的**查看凭证**。
        1.  复制 api-key 值。
        {: download}
    - 在开发者控制台的 **vision-tutorial** 项目中，复制**凭证**部分中“`visual_recognition`”的 `api-key` 值。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果使用的是 {{site.data.keyword.Bluemix_dedicated_notm}}，请在“目录”的 [{{site.data.keyword.visualrecognitionshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} 页面中创建服务实例。有关如何查找服务凭证的详细信息，请参阅 [Watson 服务的服务凭证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步骤 1：对图像分类
{: #classify}

1.  下载样本 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 图像。
1.  发出以下命令上传图像，并根据所有内置分类器对其分类：
    - 将 `{api-key}` 替换为早先复制的服务凭证。
    - 修改 images\_file 的位置，使其指向映像的保存位置。

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    如果拥有的是 {{site.data.keyword.Bluemix_notm}} Dedicated，那么此处的 `gateway-a.watsonplatform.net` 端点可能不是服务端点。请检查服务仪表板的**服务凭证**页面上的 `url`。
    {: tip}

    响应包含通用模型或分类器（使用 `default` classifier_id）、在图像中识别到的类和每个类的分数。

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    置信度分数的范围为 0 到 1，分数越高，表示相关性越大。缺省情况下，`/v3/classify` 调用不会包含分数低于 `0.5` 的类。

## 步骤 2：检测图像中的人脸
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} 可以检测到图像中的人脸。响应会提供人脸相关信息，例如人脸在图像中的位置以及每张人脸的估计年龄范围和性别。

该服务还可以通过姓名来识别许多名人，并且可以提供*知识图*，以便您可以聚合更高级别的概念。

1.  下载样本 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 图像。
1.  发出以下命令调用 `POST /v3/detect_faces` 方法来上传和分析该图像。如果使用自己的图像，那么最大大小为 2 MB：
    - 将 `{api-key}` 替换为早先复制的服务凭证。
    - 修改 images\_file 的位置，使其指向映像的保存位置。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    响应包括位置、估计年龄、性别、身份和类型层次结构（如果服务识别到该人脸）以及每项的分数。

    分数范围为 0-1，分数越高，表示相关性越大。所有人脸都会检测到，但对于有 10 张以上人脸的图像，返回的年龄和性别置信度分数可能会为 0。

    ```json
    {
      "images": [
        {
          "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 后续步骤

您已经对如何使用 {{site.data.keyword.visualrecognitionshort}} 的内置缺省分类器有了基本的了解。现在，可以更深入地探索以下内容：

- 了解有关如何[构建定制分类器](/docs/services/visual-recognition/tutorial-custom-classifier.html)的更多信息。
- 阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中有关 API 的信息。

### 出处
{: #attributions}

- [Fruit Basket ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://flic.kr/p/JPHES){: new_window} 由 Flikr 用户 [Ryan Edwards-Crewe ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.flickr.com/photos/ryanec/){: new_window} 依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此图像未进行任何更改。
- [obama ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://bit.ly/1T0DCl9){: new_window} 由 Flikr 用户 [dcblog ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.flickr.com/photos/12863058@N08/){: new_window} 依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此图像未进行任何更改。
