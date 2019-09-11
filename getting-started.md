---

copyright:
  years: 2015, 2019
lastupdated: "2019-09-11"

keywords: visual recognition,visual recognition project,VisualRecognition,getting started,classify images, analyze images,tag images,image classification,image recognition,sample code

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
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
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}

# Getting started with {{site.data.keyword.visualrecognitionshort}}
{: #getting-started-tutorial}

This tutorial guides you through simple image recognition with {{site.data.keyword.visualrecognitionfull}}. You use the built-in models to analyze the images.
{: shortdesc}

To work in a graphical interface where you can create your own custom models, use <span class="hide-dashboard">[{{site.data.keyword.DSX}}](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: external}</span><span class="hide-in-docs">[{{site.data.keyword.DSX}}](tooling-url){: external}</span> and follow the [video](https://youtu.be/898RN31szg0){: external}.
{: tooling-url}
{: tip}

## Before you begin
{: #prerequisites}

- {: hide-dashboard} Create an instance of the service:
    1.  Go to the [{{site.data.keyword.visualrecognitionshort}}](https://{DomainName}/catalog/services/visual-recognition){: external} page in the catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Click **Create**.
- {: hide-dashboard} Copy the credentials to authenticate to your service instance:
    1.  On the **Manage** page, click **Show Credentials**.
    1.  Copy the `API Key` value.
- {: curl} Make sure that you have the `curl` command.
    - Test whether `curl` is installed. Run the following command on the command line. If the output lists the `curl` version with SSL support, you are set for the tutorial.

        ```bash
        curl -V
        ```
        {: pre}

    - If necessary, install a version with SSL enabled from [curl.haxx.se](https://curl.haxx.se/){: external}. Add the location of the file to your PATH environment variables if you want to run `curl` from any command-line location.
- {:go} Install the [Go SDK](https://github.com/watson-developer-cloud/go-sdk){: external}.

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} Install the [Java SDK](https://github.com/watson-developer-cloud/java-sdk){: external}.
    - {: java} Maven

        ```java
        <dependency>
          <groupId>com.ibm.watson</groupId>
          <artifactId>ibm-watson</artifactId>
          <version>[7,8)</version>
        </dependency>
        ```
        {: codeblock}

    - {: java} Gradle

        ```bash
        compile 'com.ibm.watson.developer_cloud:java-sdk:7.+'
        ```
        {:pre}
- {: javascript} Install the [Node SDK](https://github.com/watson-developer-cloud/node-sdk){: external}.

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} Install the [Python SDK](https://github.com/watson-developer-cloud/python-sdk){: external}.

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} Install the [Ruby SDK](https://github.com/watson-developer-cloud/ruby-sdk){: external}.

    ```bash
    gem install ibm_watson
    ```
    {:pre}

{{site.data.keyword.Bluemix_dedicated_notm}} plans authenticate by using `-u "{username}:{password}"` instead of `-u "apikey:{apikey}"`. Use the username and password values for your instance in the examples in this tutorial.
{: note}
{: curl}

## Step 1: Classify an image
{: #classify}

1.  Issue the following call to classify [an image](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: external}. <span class="hide-dashboard">Replace `{apikey}` with the service credentials you copied earlier.</span>

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
    import java.io.FileNotFoundException;

    import com.ibm.cloud.sdk.core.service.security.IamOptions;
    import com.ibm.watson.visual_recognition.v3.VisualRecognition;
    import com.ibm.watson.visual_recognition.v3.model.ClassifiedImages;
    import com.ibm.watson.visual_recognition.v3.model.ClassifyOptions;

    public class ClassifyUrlDefault {

      public static void main(String[] args) throws FileNotFoundException {

        IamOptions options = new IamOptions.Builder()
            .apiKey("{apikey}"{: apikey})
            .build();

        VisualRecognition service = new VisualRecognition("2018-03-19", options);

        ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
            .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg")
            .build();
        ClassifiedImages result = service.classify(classifyOptions).execute().getResult();
        System.out.println(
            "\n******** Classify with the General model ********\n" + result
                + "\n******** END Classify with the General model ********\n");
      }

    }
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

    The response includes the classes that are identified in the image from the built-in General model (`"classifier_id": "default"`) and a confidence score for each class. The score represents a percentage, and higher values represent higher confidences. By default, responses from the **Classify** calls don't include classes with a score below `0.5` (50%).

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

## Step 2: Classify with the Food model
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} also includes a built-in Food model that might be more accurate for your images with food items.

1.  Issue a call to classify an [image of food](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: external} against the Food model. <span class="hide-dashboard">Replace `{apikey}` with the service credentials you copied earlier.</span>

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
    import java.io.FileNotFoundException;
    import java.util.Collections;

    import com.ibm.cloud.sdk.core.service.security.IamOptions;
    import com.ibm.watson.visual_recognition.v3.VisualRecognition;
    import com.ibm.watson.visual_recognition.v3.model.ClassifiedImages;
    import com.ibm.watson.visual_recognition.v3.model.ClassifyOptions;

    public class ClassifyUrlFood {

      public static void main(String[] args) throws FileNotFoundException {

        IamOptions options = new IamOptions.Builder()
            .apiKey("{apikey}"{: apikey})
            .build();

        VisualRecognition service = new VisualRecognition("2018-03-19", options);

        ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
            .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg")
            .classifierIds(Collections.singletonList("food"))
            .build();
        ClassifiedImages result = service.classify(classifyOptions).execute().getResult();
        System.out.println(
            "\n******** Classify with the Food model ********\n" + result
                + "\n******** END Classify with the Food model ********\n");
      }

    }
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

    The service returns the following results. You can see that the `classifier_id` is identified as `food`. The classes that the service identified are also different from the first response.

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

## Next steps
{: #gs-next-steps}

You have a basic understanding of how to use built-in classifiers for image recognition with {{site.data.keyword.visualrecognitionshort}}. Now dive deeper:

- Try these calls with your own images. Keep the image size under 10 MB.
- Learn more about how to [build a custom model](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- {: curl} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition){: external}.
- {: go} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition?language=go){: external}.
- {: java} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition?language=java){: external}.
- {: javascript} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition?language=node){: external}.
- {: python} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition?language=python){: external}.
- {: ruby} Read about the API in the [API reference](https://{DomainName}/apidocs/visual-recognition?language=ruby){: external}.

### Attributions
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: external} by [Darklanlan](https://commons.wikimedia.org/wiki/User:Darklanlan){: external} used under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: external}. No changes were made to this image.
- [Fruit basket](https://flic.kr/p/JPHES){: external} by Flikr user [Ryan Edwards-Crewe](https://www.flickr.com/photos/ryanec/){: external} used under [Creative Commons Attribution 2.0 license](http://creativecommons.org/licenses/by/2.0/deed.en){: external}. No changes were made to this image.
- [Ginni Rometty at the Fortune MPW Summit in 2011](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: external} by Asa Mathat / Fortune Live Media used under [CC BY 2.0](https://creativecommons.org/licenses/by/2.0/legalcode){: external}. No changes were made to this image.
