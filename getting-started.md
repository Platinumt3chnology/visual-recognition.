---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-06"

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

# Getting started tutorial

This tutorial guides you through how to use the default classifiers in {{site.data.keyword.visualrecognitionfull}} to classify an image and then detect faces in an image.
{: shortdesc}

## Before you begin
{: #prerequisites}

If you already created a service instance, you're all set with these prerequisites. Move on to Step 1.
{: tip}

1.  Go to the [{{site.data.keyword.visualrecognitionshort}} service](https://console.{DomainName}/catalog/services/visual-recognition/) and either sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
1.  After you log in, type `vision-tutorial` in the **Service name** field of the {{site.data.keyword.visualrecognitionshort}} page. Click **Create**.

## Step 1: Copy your credentials
{: #copy-credentials}

After you create the service instance, you'll land on the dashboard for the instance. Here you can find the credentials to authenticate to your service instance.

1.  Click **Service credentials**.
1.  Click **View credentials** under **Actions**.
1.  Copy the `api-key` value.

## Step 2: Classifying an image

If you have {{site.data.keyword.Bluemix_notm}} Dedicated, the `gateway-a.watsonplatform.net` endpoint here might not be your service endpoint. Check the `url` on the **Service credentials** page of your service dashboard.
{: tip}

1.  Download the sample <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> image.
1.  Issue the following command to upload the image and classify it against all built-in classifiers:
    - Replace `{api-key}` with the service credentials you copied earlier.
    - Modify the location of the images\_file to point to where you saved the image.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    The response includes the default classifier, the classes identified in the image, and a score for each class.

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

    Scores range from 0-1, with a higher score indicating greater correlation. The `/v3/classify` calls don't include low-scoring classes by default.

## Step 3: Detecting faces in an image
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} can detect faces in images. The response provides information such as the location of the face in the image and the estimated age range and gender for each face.

The service can also identify many celebrities by name, and can provide a *knowledge graph* so that you can aggregate higher-level concepts.

1.  Download the sample <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> image.
1.  Issue the following command to the `POST /v3/detect_faces` method to upload and analyze the image. If you use your own image, the maximum size is 2 MB:
    - Replace `{api-key}` with the service credentials you copied earlier.
    - Modify the location of the images\_file to point to where you saved the image.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    The response includes a location, age estimate, gender, identity and type hierarchy (if the service recognizes that face), and a score for each.

    Scores range from 0-1, with a higher score indicating greater correlation. All faces are detected, but for images with more than 10 faces, age and gender confidence scores might return with scores of 0.

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

## Next steps

You have a basic understanding of how to use the default classifiers with {{site.data.keyword.visualrecognitionshort}}. Now dive deeper:

- Learn more about how to [build a custom classifier](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Read about the API in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

- [Fruit basket ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://flic.kr/p/JPHES){: new_window} by Flikr user [Ryan Edwards-Crewe ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.flickr.com/photos/ryanec/){: new_window} used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to this image.
- [obama ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://bit.ly/1T0DCl9){: new_window} by Flikr user [dcblog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.flickr.com/photos/12863058@N08/){: new_window} used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to this image.
