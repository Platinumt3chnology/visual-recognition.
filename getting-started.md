---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-15"

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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Getting started tutorial

This tutorial guides you through how to use some built-in models in {{site.data.keyword.visualrecognitionfull}} to classify an image and then detect faces in an image.
{: shortdesc}

## Before you begin
{: #prerequisites}
{: hide-dashboard}

- Create an instance of the service:
    1.  Go to the [{{site.data.keyword.visualrecognitionshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/visual-recognition){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  Click **Show** to view your credentials.
    1.  Copy the apikey value.
{: hide-dashboard}

## Step 1: Classify an image
{: #classify}

1.  Issue the following call to classify [an image ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window}. <span class="hide-dashboard">Replace `{api_key}` with the service credentials you copied earlier.</span>

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg&version=2018-03-19"
    ```
    {: pre}

    The response includes the classes identified in the image from the built-in General model (`"classifier_id": "default"`) and a confidence score for each class. The score represents a percentage, and higher values represent higher confidences. By default, responses from the `Classify` calls don't include classes with a score below `0.5` (50%).

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

1.  Issue a call to classify an [image of food ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} against the Food model.<span class="hide-dashboard">Replace `{api_key}` with the service credentials you copied earlier.</span>

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} -F "classifier_ids=food" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg&version=2018-03-19"
    ```
    {: pre}

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

## Step 3: Detect faces in an image
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} can detect faces in images.

1.  Issue the following call to the `Detect faces in an image` method to analyze an [image of Ginni Rometty ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}.<span class="hide-dashboard">Replace `{api_key}` with the service credentials you copied earlier.</span>

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg&version=2018-03-19"
    ```
    {: pre}

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

## Next steps

You have a basic understanding of how to use built-in classifiers with {{site.data.keyword.visualrecognitionshort}}. Now dive deeper:

- Try these calls with your own images. Just keep the image size under 10 MB.
- Learn more about how to [build a custom model](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Read about the API in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Attributions
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window} by [Darklanlan ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window} used under [CC BY 4.0 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window}. No changes were made to this image.
- [Fruit basket ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://flic.kr/p/JPHES){: new_window} by Flikr user [Ryan Edwards-Crewe ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.flickr.com/photos/ryanec/){: new_window} used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to this image.
- [Ginni Rometty at the Fortune MPW Summit in 2011 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} by Asa Mathat / Fortune Live Media used under [CC BY 2.0 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window}. No changes were made to this image.
