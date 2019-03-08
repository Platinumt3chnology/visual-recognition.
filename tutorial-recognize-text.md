---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-08"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Recognizing text in an image
{: #tutorial-recognize-text}

This tutorial guides you through how to make your first call with the {{site.data.keyword.visualrecognitionshort}} beta Text model to detect and recognize English text in an image.
{: shortdesc}

The Text model is a private beta feature, and you must have permission from {{site.data.keyword.IBM_notm}} to make calls to the model. [Request access ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. For more information about beta features, see [Release notes](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Before you begin
{: #tutorial-recognize-text-prerequisites}

1.  Go to the [{{site.data.keyword.visualrecognitionshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/visual-recognition){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  Click **Show** to view your credentials.
    1.  Copy the **API key** value.

## Step 1: Recognize text in an image
{: #tutorial-recognize-text-recognize-text}

1.  Issue the following call to recognize text in [an image ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}. Replace `{your_api_key}` with the API key value that you copied earlier.

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    The response includes the recognized text and the locations of words in the text with a confidence score for each word. The location information can be used to draw bounding boxes around the words.

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Next steps

You have a basic understanding of how to recognize text in an image. Explore further.

- Read the [overview](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-).
- Explore the Text model methods in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Attributions
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} by [Lubo Minar ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://unsplash.com/@bubo){: new_window} on [Unsplash ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}.  No changes were made to this image.
