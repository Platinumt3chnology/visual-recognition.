---

copyright:
  years: 2015, 2017
lastupdated: "2017-07-25"

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

# Finding similar images

After you classify an image in the Getting started example, you can use the beta Similarity Search service to create a collection of your own images and video frames, and then to find other images similar to the queried one within a collection of images. This tutorial guides you through how to create a custom collection, and then how to search that collection for similar images.
{: shortdesc}

## Step 1: Log in, create the service, and get your credentials

If you created your free instance of the {{site.data.keyword.visualrecognitionshort}}, use those credentials for this tutorial. If you have not created a service, go back and perform the steps in the beginning of [Getting Started](/docs/services/visual-recognition/getting-started.html).

## Step 2: Creating a collection

1. Use the `POST /v3/collections` method to create a new collection. Each user can create a maximum of five collections:

    - Replace `{api-key}` with your API key from {{site.data.keyword.Bluemix}}.
    - Replace `{your\_collection\_name}` with the name for your collection. The name can be a maximum of 128 UTF8 characters, with no spaces.

    ```bash
    curl -X POST
    -F "name={your_collection_name}"
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/collections?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    The response includes information about the collection:

    ```json
    {
      "collection_id": "dresses_1257263",
      "name": "dresses",
      "created": "2016-09-04T21:49:16.908Z",
      "images": "0",
      "status": "available",
      "capacity": "1000000"
    }
    ```
    {: codeblock}

    The status changes to `available` when the collection is ready for images.

1. If the call doesn't immediately return `available`, issue the `GET /v3/collections/{collection_id}` call to check the status:

    ```bash
    curl -X GET
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/collections/{collection_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Step 3: Adding images to your collection

Now add images to the collection.

1. Download the sample file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/blue-dress.jpg" download="blue-dress.jpg">blue-dress.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1. Call the beta `POST /v3/collections/{collection_id}/images` method to upload the image to the collection (maximum image size is 2 MB):
    - Replace `{api-key}` with the service credentials you copied in Step 1.
    - Modify the location of the `images_file` to point to where you saved the .jpg file.
    - Replace `{collection_id}` with the collection ID of the collection that you created in Step 1.

    ```bash
    curl -X POST
    -F "image_file=@blue-dress.jpg"
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/collections/{collection_id}/images?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    The response includes information about the image:

    ```json
    {
      "images":[
        {
          "image_id": "565838654",
          "created": "2016-09-04T21:49:16.908Z",
          "image_file": "blue_dress.jpg",
          "images_processed": 1
        }
      ]
    }
    ```
    {: codeblock}

1. Repeat steps 1-2 with <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/purple-dress.jpg" download="purple-dress.jpg">purple-dress.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/silver-dress.jpg" download="silver-dress.jpg">silver-dress.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>, and <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/red-dress.jpg" download="red-dress.jpg">red-dress.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> to create an example collection.

    When you create a collection, keep in mind that the service is intended to have 1000's of images in each collection, and can contain up to 1,000,000 images. It's not possible to add more than one image at once. Each image takes 1 second to upload, so it can take 11 days to upload 1,000,000 images. Uploading images concurrently is possible sometimes, but concurrency is not officially supported.

## Step 4: Finding similar images

You can search for similar images in your collection.

1.  Download the image file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/silver-dress2.jpg" download="silver-dress2.jpg">silver-dress2.jpg <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1.  Call the beta `POST /v3/collections/{collection_id}/find_similar` method with the following curl command to upload the image file that you downloaded above, and search your collection to see if there are similar images.
    - Replace `{api-key}` with the service credentials you copied in Step 1.
    - Modify the location of the `images_file` to point to where you saved the .jpg file.
    - Replace `{collection_id}` with the collection ID of the collection that you created in Step 2.

    ```bash
    curl -X POST
    -F "image_file=@silver-dress2.jpg"
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/collections/{collection_id}/find_similar?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

The response includes the images most similar to the image you specify with the confidence in the match.

```json
{
  "image_file": "silver-dress2.jpg",
  "similar_images": [
    {
      "image_id": "a4435d",
      "image_file": "silver-dress.jpg",
      "score": 1,
      "created": "2016-09-13T20:08:42.951Z"
    },
    {
      "image_id": "55e39b",
      "image_file": "red-dress.jpg",
      "score": 0.6123047,
      "created": "2016-09-13T20:05:42.951Z",
      "metadata": {
        "key": "value"
      }
    },
    {
      "image_id": "1e657a",
      "image_file": "blue-dress.jpg",
      "score": 0.60839844,
      "created": "2016-09-13T20:05:22.049Z",
      "metadata": {
        "key": "value"
      }
    },
    {
      "image_id": "88b900",
      "image_file": "purple-dress.jpg",
      "score": 0.57666016,
      "created": "2016-09-13T20:05:35.323Z",
      "metadata": {
        "key": "value"
      }
    }
  ],
  "images_processed": 1
}
```
{: codeblock}

## Deleting your collection

You might want to delete your collection to begin developing your application with a clean instance. To delete the collection, call the `DELETE /v3/collections/{collection_id}` method.
Issue the following cURL command to delete the collection. Replace `{api_key)` with your information. Include the `collection_id` for the collection you want to delete:

```bash
curl -X DELETE
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/collections/{collection_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## Next steps

Now that you have successfully created and searched a collection, dive deeper to create your own custom collections:

- Read about the API in the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}
- Check out the [developer tools](../developer-tools.html)

### Attributions

All images used on this page are from Flikr and used under [Creative Commons Attribution 2.0 license ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No changes were made to these images.

