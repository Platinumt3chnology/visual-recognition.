
---
copyright:
  years: 2015, 2019
lastupdated: "2019-02-18"

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Migrating
{: #migrating}

{{site.data.keyword.visualrecognitionfull}} service instances created **before** May 23, 2018 have a host URL of `gateway-a.watsonplatform.net`. You must migrate those instances to a new {{site.data.keyword.visualrecognitionshort}} service instance to continue to use them.
{: shortdesc}

To migrate your current models (classifiers), you provision a new instance of the {{site.data.keyword.visualrecognitionshort}} service. For custom models, you re-train the model by creating another model (classifier) with the images from the earlier model.

1.  Create another instance of the {{site.data.keyword.visualrecognitionshort}} service:
      1.  Go to the [{{site.data.keyword.visualrecognitionshort}} page](https://console.bluemix.net/catalog/services/visual-recognition) in the {{site.data.keyword.cloud_notm}} catalog.
      1.  Select a plan and click **Create**.
1.  Copy the new credentials:
    1.  From the service dashboard, select your new {{site.data.keyword.visualrecognitionshort}} service instance.
    1.  Click the **Service credentials** tab and select *View credentials*.

        ![Service credentials tab](images/apikey1.png)
    1.  Copy the API key as indicated in the following image.

        ![Service credentials tab](images/apikey2.png)

1.  Modify how you call your service.

    There are two options to authenticate: token or API key. The token option provides greater security if, for example, your API request is somehow compromised, because the token expires after one hour. The API key is a more basic authentication method, and does not expire.

    The `gateway.watsonplatform.net` endpoint might not be your service endpoint. Check the URL on the Service credentials page of your service dashboard.
    {: tip}

    - Authenticating with an Identity and Access Management (IAM) token

        1.  Use the API key you copied to generate an Identity and Access Management (IAM) token. For more information, see [Authenticating with IAM tokens ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/watson/getting-started-iam.html#iamtoken).
        1.  Pass the access token from the response to {{site.data.keyword.visualrecognitionshort}} as a header with a bearer token. For example, specify the token in cURL with the syntax `--header 'Authorization: Bearer {access_token}'`.

      Some example calls with the token:

        - Classify an image using the default models

            ``` bash
              curl -X POST --header "Authorization: Bearer eyJhbGciOi......KIi8hdFs" \
              -F "images_file=@my_image.jpg" \
              "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
            ```
            {: pre}

        - Detect faces in images

            ```bash
            curl -X POST --header "Authorization: Bearer eyJhbGciOi......KIi8hdFs" \
            -F "images_file=@my_faces_image.jpg" \
            "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?version=2018-03-19"
            ```
            {: pre}

        - Retrieve a list of classifiers

            ```bash
              curl -X GET --header "Authorization: Bearer eyJhbGciOi......KIi8hdFs" \      "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
            ```
            {: pre}

    - Authenticating with an API key directly

        - Pass basic authentication information using the syntax `-u "username:password"`, where username is always `apikey` and password is the API key you copied.

      Some example calls with an IAM API key:

        - Classify an image using the default models

            ```bash
            curl -X POST -u "apikey:{apikey}" \
            -F "images_file=@my_image.jpg" \
            "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
            ```

        - Detect faces in images

            ```bash
            curl -X POST -u "apikey:{apikey}" \
            -F "images_file=@my_faces_image.jpg" \
            "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?version=2018-03-19"
            ```

        - Retrieve a list of classifiers

            ```bash
            curl -X GET -u "apikey:{apikey}" \
            "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
            ```

1.  [Re-create and train your custom models](/docs/services/visual-recognition/tutorial-custom-classifier.html#tutorial-custom-classifier) in your new instance of the {{site.data.keyword.visualrecognitionshort}} service.
