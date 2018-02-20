---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-23"

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

# Getting started tutorial

This tutorial guides you through how to use some built-in classifiers in {{site.data.keyword.visualrecognitionfull}} to classify an image and then detect faces in an image.
{: shortdesc}

## Before you begin
{: #prerequisites}

- Create an instance of the service:
    - {: download} If you're seeing this, you created your service instance. Now get your credentials.
    - Create a project from a service:
        1.  Go to the {{site.data.keyword.watson}} Developer Console [Services ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/developer/watson/services){: new_window} page.
        1.  Select {{site.data.keyword.visualrecognitionshort}}, click **Add Services**, and either sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
        1.  Type `vision-tutorial` as the project name and click **Create Project**.
- Copy the credentials to authenticate to your service instance:
    - {: download} From the service dashboard (what you're looking at):
        1.  Click the **Service credentials** tab.
        1.  Click **View credentials** under **Actions**.
        1.  Copy the api-key value.
        {: download}
    - From your **vision-tutorial** project in the Developer Console, copy the `api-key` value for `"visual_recognition"` from the  **Credentials** section.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

If you use {{site.data.keyword.Bluemix_dedicated_notm}}, create your service instance from the [{{site.data.keyword.visualrecognitionshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} page in the Catalog. For details about how to find your service credentials, see [Service credentials for Watson services ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Step 1: Classify an image
{: #classify}

1.  Download the sample <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> image.
1.  Issue the following command to upload the image and classify it against all built-in classifiers:
    - Replace `{api-key}` with the service credentials you copied earlier.
    - Modify the location of the images\_file to point to where you saved the image.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    If you have {{site.data.keyword.Bluemix_notm}} Dedicated, the `gateway-a.watsonplatform.net` endpoint here might not be your service endpoint. Check the `url` on the **Service credentials** page of your service dashboard.
    {: tip}

    The response includes the General model or classifier (which uses the `default` classifier_id), the classes identified in the image, and a score for each class.

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

    Confidence scores are in the range of 0 to 1, with a higher score indicating greater correlation. By default, the `/v3/classify` calls don't include classes with a score below `0.5`.

## Step 2: Detect faces in an image
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} can detect faces in images. The response provides information such as the location of the face in the image and the estimated age range and gender for each face.

The service can also identify many celebrities by name, and can provide a *knowledge graph* so that you can aggregate higher-level concepts.

You can try out the updated Face model, which can provide more accurate results with facial analysis of age and gender. To use the beta model, replace `/v3/detect_faces` with `/v3/detect_faces_beta` in the command in the following step.
{: tip}

1.  Download the sample <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> image.
1.  Issue the following command to the `POST /v3/detect_faces` method to upload and analyze the image. If you use your own image, the maximum size is 2 MB:
    - Replace `{api-key}` with the service credentials you copied earlier.
    - Modify the location of the images\_file to point to where you saved the image.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    The response includes a location, age estimate, gender, identity and type hierarchy (if the service recognizes that face), and a score for each. (Identity information is not available with the `/v3/detect_faces_beta` endpoint.)

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

You have a basic understanding of how to use the built-in default classifier with {{site.data.keyword.visualrecognitionshort}}. Now dive deeper:

- Learn more about how to [build a custom classifier](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Read about the API in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

- [Fruit basket ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://flic.kr/p/JPHES){: new_window} by Flikr user [Ryan Edwards-Crewe ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.flickr.com/photos/ryanec/){: new_window} used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to this image.
- [obama ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://bit.ly/1T0DCl9){: new_window} by Flikr user [dcblog ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.flickr.com/photos/12863058@N08/){: new_window} used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to this image.
