---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: classify,classifying,Visual Recognition,getting started,detecting faces,detect faces,food model,general model,sample code

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 入门教程

本教程将指导您如何使用 {{site.data.keyword.visualrecognitionfull}} 中的一些内置模型对图像分类，然后检测图像中的人脸。
{: shortdesc}

如果想要在图形界面中工作，请使用 {{site.data.keyword.DSX}}。[启动工具 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window}，并遵循[视频 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://youtu.be/898RN31szg0){: new_window}。
{: tip}

## 开始之前
{: #prerequisites}

- {: hide-dashboard}创建服务的实例：
    1.  转至目录中的 [{{site.data.keyword.visualrecognitionshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 页面。
    1.  注册免费的 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
    1.  单击**创建**。
- {: hide-dashboard}复制凭证以向服务实例进行认证：
    1.  在**管理**页面上，单击**显示凭证**。
    1.  复制 `AIP 密钥`值。
- {: curl}确保您具有 `curl` 命令。
    - 测试是否安装了 `curl`。在命令行上运行以下命令。如果输出列出具有 SSL 支持的 `curl` 版本，那么将针对教程进行设置。

        ```bash
        curl -V
        ```
        {: pre}

    - 如果需要，请从 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 安装启用 SSL 的版本。如果想要从任何命令行位置运行 `curl`，请将文件位置添加到 PATH 环境变量。
- {:go}安装 [Go SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/go-sdk){: new_window}。

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java}安装 [Java SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/java-sdk){: new_window}。
    - {:java}Maven

        ```java
        <dependency>
          <groupId>com.ibm.watson.developer_cloud</groupId>
          <artifactId>java-sdk</artifactId>
          <version>{version}</version>
        </dependency>
        ```
        {: codeblock}

    - {:java}Gradle

        ```bash
        compile 'com.ibm.watson.developer_cloud:java-sdk:{version}'
        ```
        {:pre}
- {: javascript}安装 [Node SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/node-sdk){: new_window}。

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python}安装 [Python SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/python-sdk){: new_window}。

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby}安装 [Ruby SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}。

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## 步骤 1：对图像分类
{: #classify}

1.  发出以下调用以对[图像 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window} 分类。<span class="hide-dashboard">将 `{apikey}` 替换为先前复制的服务凭证。</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
          Version:   "2018-03-19",
          IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr != nil {
        panic(visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"),
        },
      )
      if responseErr != nil {
        panic(responseErr)
      }
      result := visualRecognition.GetClassifyResult(response)
      b, _ := json.MarshalIndent(result, "", "  ")
      fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    IamOptions options = new IamOptions.Builder()
      .apiKey("{apikey}"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg")
      .build();
    ClassifiedImages result = visualRecognition.classify(classifyOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');
    var fs = require('fs');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    var url= 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg';

    var params = {
      url: url,
    };

    visualRecognition.classify(params, function(err, response) {
      if (err) {
        console.log(err);
      } else {
        console.log(JSON.stringify(response, null, 2))
      }
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg'

    classes_result = visual_recognition.classify(url=url).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json"
    require "ibm_watson/visual_recognition_v3"
    include IBMWatson

    visual_recognition = VisualRecognitionV3.new(
      version: "2018-03-19",
      iam_apikey: "{apikey}"{: apikey}
    )
    url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"

    classes = visual_recognition.classify(url)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    响应包含在内置通用模型 (`"classifier_id": "default"`) 的图像中标识的类以及每个类的置信度分数。分数表示百分比，值越高表示置信度越高。缺省情况下，来自 `Classify` 调用的响应不包含分数低于 `0.5` (50%) 的类。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "circuit board",
                  "score": 0.578,
                  "type_hierarchy": "/electrical device/computer circuit/circuit board"
                },
                {
                  "class": "computer circuit",
                  "score": 0.755
                },
                {
                  "class": "electrical device",
                  "score": 0.757
                },
                {
                  "class": "disk controller",
                  "score": 0.553,
                  "type_hierarchy": "/controller/disk controller"
                },
                {
                  "class": "controller",
                  "score": 0.558
                },
                {
                  "class": "central processing unit",
                  "score": 0.535
                },
                {
                  "class": "PC board",
                  "score": 0.501,
                  "type_hierarchy": "/electrical device/computer circuit/PC board"
                },
                {
                  "class": "CPU board",
                  "score": 0.5,
                  "type_hierarchy": "/electrical device/computer circuit/CPU board"
                },
                {
                  "class": "electronic equipment",
                  "score": 0.6
                },
                {
                  "class": "memory device",
                  "score": 0.599
                },
                {
                  "class": "microchip",
                  "score": 0.592
                },
                {
                  "class": "jade green color",
                  "score": 0.838
                },
                {
                  "class": "emerald color",
                  "score": 0.787
                }
              ]
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 0
    }
    ```
    {: codeblock}

## 步骤 2：使用“食品”模型进行分类
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} 还包含内置“食品”模型，此模型对于您的食品项图像可能更准确。

1.  发出调用以根据“食品”模型对[食品图像 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} 分类。<span class="hide-dashboard">将 `{apikey}` 替换为先前复制的服务凭证。</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} -F "classifier_ids=food" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
          Version:   "2018-03-19",
          IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr != nil {
        panic(visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg"),
          ClassifierIds: []string{"food"},
        },
      )
      if responseErr != nil {
        panic(responseErr)
      }
      result := visualRecognition.GetClassifyResult(response)
      b, _ := json.MarshalIndent(result, "", "  ")
      fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    IamOptions options = new IamOptions.Builder()
      .apiKey("{apikey}"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg");
      .classifierIds(Arrays.asList("food"))
      .build();
    ClassifiedImages result = visualRecognition.classify(classifyOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    var url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg';
    var classifier_ids = ["food"];

    var params = {
      url: url,
      classifier_ids: classifier_ids
    };

    visualRecognition.classify(params, function(err, response) {
      if (err)
        console.log(err);
      else
        console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg'
    classifier_ids = ["food"]

    classes_result = visual_recognition.classify(url=url, classifier_ids=classifier_ids).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json"
    require "ibm_watson/visual_recognition_v3"
    include IBMWatson

    visual_recognition = VisualRecognitionV3.new(
      version: "2018-03-19",
      iam_apikey: "{apikey}"{: apikey}
    )
    url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"
    classifier_ids= ["food"]

    classes = visual_recognition.classify(url, classifier_ids)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    服务会返回以下结果。您可以看到 `classifier_id` 标识为 `food`。服务所标识的类也与第一个响应不同。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "food",
              "name": "food",
              "classes": [
                {
                  "class": "apple",
                  "score": 0.572,
                  "type_hierarchy": "/fruit/accessory fruit/apple"
                },
                {
                  "class": "accessory fruit",
                  "score": 0.572
                },
                {
                  "class": "fruit",
                  "score": 0.805
                },
                {
                  "class": "banana",
                  "score": 0.5,
                  "type_hierarchy": "/fruit/banana"
                }
              ]
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 0
    }
    ```

## 步骤 3：检测图像中的人脸
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} 可以检测到图像中的人脸。

1.  向 `Detect faces in an image` 方法发出以下调用以分析 [Ginni Rometty 的图像 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}。<span class="hide-dashboard">将 `{apikey}` 替换为先前复制的服务凭证。</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
      NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
        Version:   "2018-03-19",
        IAMApiKey: "{apikey}"{: apikey},
      })
    if visualRecognitionErr != nil {
      panic(visualRecognitionErr)
      }

    response, responseErr := visualRecognition.DetectFaces(
      &visualrecognitionv3.DetectFacesOptions{
        URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"),
      },
    )
    if responseErr != nil {
      panic(responseErr)
    }
    result := visualRecognition.GetClassifyResult(response)
    b, _ := json.MarshalIndent(result, "", "  ")
    fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    DetectFacesOptions detectFacesOptions = new DetectFacesOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg");
      .build();
    DetectedFaces result = visualRecognition.detectFaces(detectFacesOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
          version: '2018-03-19',
          iam_apikey: '{apikey}'{: apikey}
        });

    var params = {
      url: 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg'
    };

    visualRecognition.detectFaces(params, function(err, response) {
      if (err)
        console.log(err);
      else
        console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg'

    faces = visual_recognition.detect_faces(url).get_result()
    print(json.dumps(faces, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
      require "json"
      require "ibm_watson/visual_recognition_v3"
      include IBMWatson

      visual_recognition = VisualRecognitionV3.new(
        version: "2018-03-19",
        iam_apikey: "{apikey}"{: apikey}
      )
      url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"

      faces = visual_recognition.detect_faces(url)
      puts JSON.pretty_generate(faces.result)
      end
      ```
    {: ruby}
    {: codeblock}

    响应会提供人脸在图像中的位置以及每张人脸的估计年龄范围和性别。

    ```json
    {
      "images": [
        {
          "faces": [
            {
              "age": {
                "min": 50,
                "max": 53,
                "score": 0.8261783
              },
              "face_location": {
                "height": 744,
                "width": 606,
                "left": 460,
                "top": 373
              },
              "gender": {
                "gender": "FEMALE",
                "gender_label": "female",
                "score": 0.9999988
              }
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 后续步骤

您已经对如何使用 {{site.data.keyword.visualrecognitionshort}} 的内置分类器有了基本的了解。现在，可以更深入地探索以下内容：

- 使用自己的图像来试用这些调用。只需将图像大小保持在 10 MB 以下。
- 了解有关如何[构建定制模型](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)的更多信息。
- {: curl}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition){: new_window} 中有关 API 的信息。
- {: go}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window} 中有关 API 的信息。
- {: java}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window} 中有关 API 的信息。
- {: javascript}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window} 中有关 API 的信息。
- {: python}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window} 中有关 API 的信息。
- {: ruby}阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window} 中有关 API 的信息。

### 出处
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window}，作者是 [Darklanlan ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window}，依据 [CC BY 4.0 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window} 进行使用。此图像未进行任何更改。
- [Fruit Basket ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://flic.kr/p/JPHES){: new_window} 由 Flikr 用户 [Ryan Edwards-Crewe ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.flickr.com/photos/ryanec/){: new_window} 依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此图像未进行任何更改。
- [Ginni Rometty at the Fortune MPW Summit in 2011 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}，作者是 Asa Mathat/Fortune Live Media，依据 [CC BY 2.0 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window} 进行使用。此图像未进行任何更改。
