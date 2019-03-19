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

# 入門指導教學

本指導教學指導您如何在{{site.data.keyword.visualrecognitionfull}}中使用一些內建模型來分類影像，然後在影像中偵測臉孔。
{: shortdesc}

如果您偏好使用圖形介面，請使用{{site.data.keyword.DSX}}。[請啟動工具 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window}，然後遵循[影片 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://youtu.be/898RN31szg0){: new_window} 進行。
{: tip}

## 開始之前
{: #prerequisites}

- {: hide-dashboard}建立服務實例：
    1.  移至型錄中的 [{{site.data.keyword.visualrecognitionshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 頁面。
    1.  註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶，或者登入。
    1.  按一下**建立**。
- {: hide-dashboard}複製認證以向服務實例進行鑑別：
    1.  在**管理**頁面中，按一下**顯示認證**。
    1.  複製 `API Key` 值。
- {: curl}請確定您有 `curl` 指令。
    - 測試是否已安裝 `curl`。請在指令行上執行下列指令。如果輸出列出具有 SSL 支援的 `curl` 版本，表示您已經完成設定指導教學。

        ```bash
        curl -V
        ```
        {: pre}

    - 必要的話，請從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝已啟用 SSL 的版本。如果您要從任何指令行位置執行 `curl`，請將檔案位置新增至您的 PATH 環境變數。
- {:go} 安裝 [Go SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/go-sdk){: new_window}。

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} 安裝 [Java SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/java-sdk){: new_window}。
    - {:java} Maven

        ```java
        <dependency>
          <groupId>com.ibm.watson.developer_cloud</groupId>
          <artifactId>java-sdk</artifactId>
          <version>{version}</version>
        </dependency>
        ```
        {: codeblock}

    - {:java} Gradle

        ```bash
        compile 'com.ibm.watson.developer_cloud:java-sdk:{version}'
        ```
        {:pre}
- {: javascript} 安裝 [Node SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/node-sdk){: new_window}。

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} 安裝 [Python SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/python-sdk){: new_window}。

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} 安裝 [Ruby SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}。

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## 步驟 1：分類影像
{: #classify}

1.  發出下列呼叫來分類 [ 影像 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window}。<span class="hide-dashboard">請將 `{apikey}` 取代為您先前複製的服務認證。</span>

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

    回應包含來自內建 General 模型 (`"classifier_id": "default"`) 的影像中所識別的類別，以及每個類別的信任評分。評分以百分比表示，值越高代表信任度越高。依預設，`Classify` 呼叫的回應不包含評分低於 `0.5` (50%) 的類別。
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

## 步驟 2：使用 Food 模型分類
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} 還包含內建 Food 模型，對於您含有食物項目的影像可能會具有更高的準確性。

1.  對 Food 模型發出呼叫來分類 [ 食物的影像 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window}。<span class="hide-dashboard">請將 `{apikey}` 取代為您先前複製的服務認證。</span>

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

    服務傳回下列結果。您可以看到，`classifier_id` 已識別為 `food`。服務所識別的類別也和第一個回應不同。

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

## 步驟 3：在影像中偵測臉孔
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} 可以偵測影像中的臉孔。

1.  對 `Detect faces in an image` 方法發出下列呼叫來分析 [Ginni Rometty 的影像 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}。<span class="hide-dashboard">請將 `{apikey}` 取代為您先前複製的服務認證。</span>

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

    The response provides the location of the face in the image and the estimated age range and gender for each face.

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

## 後續步驟

您對如何在 {{site.data.keyword.visualrecognitionshort}} 使用內建分類器已經具有基本瞭解。現在，更深入點：

- 對您擁有的影像嘗試這些呼叫。請記得將影像大小保持在 10 MB 以下。
- 進一步瞭解如何[建置自訂模型](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)。
- {: curl}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition){: new_window} 中閱讀 API 的相關資訊。
- {: go}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window} 中閱讀 API 的相關資訊。
- {: java}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window} 中閱讀 API 的相關資訊。
- {: javascript}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window} 中閱讀 API 的相關資訊。
- {: python}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window} 中閱讀 API 的相關資訊。
- {: ruby}在 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window} 中閱讀 API 的相關資訊。

### 歸屬
{: #attributions}

- [PS55.jpg 中的 IBM VGA 90X8941 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window}，作者 [Darklanlan ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window}，根據 [CC BY 4.0 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window} 授權使用。此影像未經過任何變更。
- Flikr 使用者 [Ryan Edwards-Crewe ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.flickr.com/photos/ryanec/){: new_window} 提供的[水果籃 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://flic.kr/p/JPHES){: new_window}，根據 [Creative Commons Attribution 2.0 授權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。此影像未經過任何變更。
- [Ginni Rometty 出席 2011 年 Fortune MPW Summit ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}，作者 Mathat / Fortune Live Media，根據 [CC BY 2.0 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window} 授權使用。此影像未經過任何變更。
