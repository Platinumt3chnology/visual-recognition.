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

# 시작하기 튜토리얼

이 튜토리얼은 {{site.data.keyword.visualrecognitionfull}}의 일부 기본 제공 모델을 사용하여 이미지를 분류한 후에 이미지에서 얼굴을 감지하는 방법을 안내합니다.
{: shortdesc}

그래픽 인터페이스에서 작업하려는 경우 {{site.data.keyword.DSX}}를 사용하십시오. [도구를 실행 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window}하고 [동영상 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://youtu.be/898RN31szg0){: new_window}을 시청하십시오.
{: tip}

## 시작하기 전에
{: #prerequisites}

- {: hide-dashboard}서비스 인스턴스 작성:
    1.  카탈로그에서 [{{site.data.keyword.visualrecognitionshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 페이지로 이동하십시오. 
    1.  무료 {{site.data.keyword.Bluemix_notm}} 계정을 등록하거나 로그인하십시오. 
    1.  **작성**을 클릭하십시오. 
- {: hide-dashboard}서비스 인스턴스를 인증하기 위한 인증 정보 복사:
    1.  **관리** 페이지에서 **인증 정보 표시**를 클릭하십시오. 
    1.  `API Key` 값을 복사하십시오. 
- {: curl} `curl` 명령이 있는지 확인하십시오. 
    - `curl`이 설치되었는지 테스트하십시오. 명령행에서 다음 명령을 실행하십시오. SSL 지원을 제공하는 `curl` 버전이 출력에 나열될 경우 튜토리얼용으로 설정된 것입니다. 

        ```bash
        curl -V
        ```
        {: pre}

    - 필요한 경우 SSL 지원 버전을 [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 설치하십시오. 원하는 명령행 위치에서 `curl`을 실행하려는 경우 파일 위치를 PATH 환경 변수에 추가하십시오. 
- {:go} [Go SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/go-sdk){: new_window}를 설치하십시오. 

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java}[Java SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/java-sdk){: new_window}를 설치하십시오. 
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
- {: javascript}[Node SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/node-sdk){: new_window}를 설치하십시오. 

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python}[Python SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/python-sdk){: new_window}를 설치하십시오. 

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby}[Ruby SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}를 설치하십시오. 

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## 1단계: 이미지 분류
{: #classify}

1.  다음 호출을 실행하여 [이미지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window}를 분류하십시오. <span class="hide-dashboard">`{apikey}`를 앞에서 복사한 서비스 인증 정보로 대체하십시오. </span>

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

    응답에는 기본 제공 일반 모델(`"classifier_id": "default"`)의 이미지에서 식별된 클래스 및 각 클래스에 대한 신뢰도 점수가 포함되어 있습니다. 이 점수는 백분율로 표시되며, 값이 클수록 더 높은 신뢰도를 나타냅니다. 기본적으로 `Classify` 호출의 응답에는 점수가 `0.5`(50%) 미만인 클래스가 포함되지 않습니다.

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

## 2단계: 음식 모델로 분류
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}}은 또한 음식 항목이 포함된 이미지에 더 정확할 수 있는 기본 제공 음식 모델도 제공합니다. 

1.  호출을 실행하여 음식 모델에 대해 [음식 이미지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window}를 분류하십시오. <span class="hide-dashboard">`{apikey}`를 앞에서 복사한 서비스 인증 정보로 대체하십시오. </span>

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

    서비스가 다음 결과를 리턴합니다. `classifier_id`가 `food`로 식별됨을 알 수 있습니다. 서비스가 식별한 클래스도 첫 번째 응답과 다릅니다.

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

## 3단계: 이미지에서 얼굴 감지
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}}은 이미지에서 얼굴을 감지할 수 있습니다.

1.  `Detect faces in an image` 메소드에 대해 다음 호출을 실행하여 [Ginni Rometty의 이미지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}를 분석하십시오. <span class="hide-dashboard">`{apikey}`를 앞에서 복사한 서비스 인증 정보로 대체하십시오. </span>

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

    응답은 이미지에서 얼굴의 위치 및 각 얼굴의 예상 연령 범위와 성별을 제공합니다. 

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

## 다음 단계

{{site.data.keyword.visualrecognitionshort}}에서 기본 제공 분류자를 사용하는 기본적인 방법을 살펴보았습니다. 이제 심층 학습을 수행합니다.

- 자체 이미지를 사용하여 이러한 호출을 시도하십시오. 이미지 크기는 10MB 미만으로 유지하십시오. 
- [사용자 정의 모델을 빌드](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)하는 방법에 대해 학습하십시오. 
- {: curl}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition){: new_window}에서 API 관련 자료를 읽어보십시오.
- {: go}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window}에서 API 관련 자료를 읽어보십시오.
- {: java}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window}에서 API 관련 자료를 읽어보십시오.
- {: javascript}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window}에서 API 관련 자료를 읽어보십시오.
- {: python}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window}에서 API 관련 자료를 읽어보십시오.
- {: ruby}[API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window}에서 API 관련 자료를 읽어보십시오.

### 저작권
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window}는 [Darklanlan ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window}에 의해 [CC BY 4.0 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window}에서 사용되었습니다. 이 이미지는 변경되지 않았습니다.
- [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용된 Flikr 사용자 [Ryan Edwards-Crewe ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.flickr.com/photos/ryanec/){: new_window}의 [과일 바구니 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://flic.kr/p/JPHES){: new_window}. 이 이미지는 변경되지 않았습니다.
- [Ginni Rometty at the Fortune MPW Summit in 2011 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}은 Asa Mathat / Fortune Live Media에 의해 [CC BY 2.0 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window}에서 사용되었습니다. 이 이미지는 변경되지 않았습니다.
