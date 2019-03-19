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

# 入門チュートリアル

このチュートリアルでは、{{site.data.keyword.visualrecognitionfull}} でいくつかの組み込みモデルを使用してイメージを分類し、次にイメージ内の顔を検出する方法についてご案内します。
{: shortdesc}

グラフィカル・インターフェースによる操作をご希望の場合は、{{site.data.keyword.DSX}} を使用します。[ツール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} を起動して、[ビデオ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://youtu.be/898RN31szg0){: new_window} に従って操作を行ってください。
{: tip}

## 始めに
{: #prerequisites}

- {: hide-dashboard} 以下のようにして、サービスのインスタンスを作成します。
    1.  カタログの [{{site.data.keyword.visualrecognitionshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/visual-recognition){: new_window} ページに移動します。
    1.  無料の {{site.data.keyword.Bluemix_notm}} アカウントに登録するか、ログインします。
    1.  **「作成」**をクリックします。
- {: hide-dashboard} 以下のようにして、サービス・インスタンスに認証する資格情報をコピーします。
    1.  **「管理」**ページで、**「資格情報の表示」**をクリックします。
    1.  `API キー` の値をコピーします。
- {: curl} `curl` コマンドを使用できることを確認します。
    - `curl` がインストールされているかどうかをテストします。コマンド・ラインで以下のコマンドを実行します。出力に SSL 対応の `curl` バージョンがリストされていれば、チュートリアルを開始する準備は整っています。

        ```bash
        curl -V
        ```
        {: pre}

    - 必要な場合は、SSL を使用可能なバージョンを [curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} からインストールします。`curl` をコマンド・ラインで任意の場所から実行できるようにするには、PATH 環境変数にファイルの場所を追加します。
- {:go} [Go SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/go-sdk){: new_window} をインストールします。

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} [Java SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/java-sdk){: new_window} をインストールします。
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
- {: javascript} [Node SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/node-sdk){: new_window} をインストールします。

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} [Python SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/python-sdk){: new_window} をインストールします。

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} [Ruby SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window} をインストールします。

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## ステップ 1: イメージの分類
{: #classify}

1.  以下の呼び出しを発行して、[イメージ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window} を分類します。<span class="hide-dashboard">`{apikey}` を、前にコピーしたサービス資格情報に置き換えます。</span>

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

    応答には、組み込みの一般モデル (`"classifier_id": "default"`) によってイメージ内で識別されたクラスと、各クラスの信頼性スコアが含まれます。スコアはパーセンテージを表し、値が高いほど信頼度が高いことを意味します。デフォルトでは、`Classify` 呼び出しの応答には、`0.5` (50%) より低いスコアのクラスは含まれません。

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

## ステップ 2: Food モデルによる分類
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} には、食品のイメージをより正確に分類する、組み込みの Food モデルも含まれています。

1.  [食品のイメージ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} を Food モデルと突き合わせて分類する呼び出しを発行します。<span class="hide-dashboard">`{apikey}` を、前にコピーしたサービス資格情報に置き換えます。</span>

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

    このサービスによって、以下の結果が返されます。`classifier_id` が `food` として識別されていることが分かります。さらに、サービスによって識別されたクラスが、最初の応答とは異なることも分かります。

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

## ステップ 3: イメージ内の顔の検出
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} は、イメージ内で顔を検出できます。

1.  以下の呼び出しを `Detect faces in an image` メソッドに対して発行して、[ Ginni Rometty のイメージ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} を分析します。<span class="hide-dashboard">`{apikey}` を、前にコピーしたサービス資格情報に置き換えます。</span>

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

    応答は、イメージ内での顔の位置、およびそれぞれの顔の推定年齢範囲と性別を提供します。

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

## 次のステップ

{{site.data.keyword.visualrecognitionshort}} での組み込み分類器の使用法について基本的に理解できました。 次に、さらに詳細に検討します。

- これらの呼び出しを、お客様が所有するイメージで試してみてください。ただし、イメージのサイズは 10 MB を超えないようにします。
- [カスタム・モデルの作成](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)方法について学びます。
- {: curl} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition){: new_window} を参照してください。
- {: go} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window} を参照してください。
- {: java} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window} を参照してください。
- {: javascript} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window} を参照してください。
- {: python} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window} を参照してください。
- {: ruby} API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window} を参照してください。

### 帰属
{: #attributions}

- [Darklanlan ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window} による [IBM VGA 90X8941 on PS55.jpg ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window} は、[CC BY 4.0 の使用許諾 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window} を受けて使用されました。このイメージに対する変更は行われていません。
- Flikr ユーザー [Ryan Edwards-Crewe ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.flickr.com/photos/ryanec/){: new_window} による [Fruit basket ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://flic.kr/p/JPHES){: new_window} は、[Creative Commons Attribution 2.0 の使用許諾![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} を受けて使用されました。 このイメージに対する変更は行われていません。
- Asa Mathat / Fortune Live Media による [Ginni Rometty at the Fortune MPW Summit in 2011 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} は、[CC BY 2.0 の使用許諾 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window} を受けて使用されました。このイメージに対する変更は行われていません。
