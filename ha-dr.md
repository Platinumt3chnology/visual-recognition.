---

copyright:
  years: 2019
lastupdated: "2019-04-29"

keywords: HA,DR,high availability,disaster recovery

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
{:table: .aria-labeledby="caption"}

# High availability and disaster recovery
{: #ha-dr-top}

{{site.data.keyword.visualrecognitionfull}} supports high availability with no single point of failure. However, recovering from potential disasters that affect an entire location requires planning and preparation.
{: shortdesc}

You are responsible for understanding your configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and to restore your data in any location. See [How do I ensure zero downtime? ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} for more information.

## High availability
{: #ha-dr-availability}

{{site.data.keyword.visualrecognitionshort}} is hosted in the [Dallas location](/docs/resources?topic=resources-services_region#services_region), and traffic is load-balanced across several [data centers](/docs/overview?topic=overview-zero-downtime#zero-downtime).

## Disaster recovery
{: #ha-dr-recovery}

Disaster recovery can become an issue if an {{site.data.keyword.cloud_notm}} location experiences a significant failure that includes the potential loss of data. You must wait for {{site.data.keyword.IBM_notm}} to bring a location back online if it becomes unavailable. If underlying data services are compromised by the failure, you must also wait for {{site.data.keyword.IBM_notm}} to restore those data services.

If a catastrophic failure occurs, {{site.data.keyword.IBM_notm}} might not be able to recover data from database backups. In this case, you need to restore your data to return your service instance to its most recent state.

Your disaster recovery plan includes knowing, preserving, and being prepared to restore all data that is maintained on {{site.data.keyword.cloud_notm}}. This stored data includes images for custom models (v3) and images and training data for collections (v4).

### Disaster recovery for image classification custom models
{: #ha-dr-v3-overview}

For image classification, your disaster recovery plan includes only artifacts for custom models. The other models (General, Food, and Explicit), and face detection and text recognition are not trained from your data, so you don't have files to store locally.

#### Backing up images
You want to store the images that you use to train your custom models.

To find your custom models and training images, use the API or {{site.data.keyword.DSX}}:

- Models created with {{site.data.keyword.DSX}}:
    1.  Click a {{site.data.keyword.visualrecognitionshort}} service instance in your [resource list ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/resources?groups=resource-instance){: new_window}.
    1.  Click **Launch tool** on the Manage page. (You might see **Create a custom model**.)
    1.  Find your models from the **Assets** page of your {{site.data.keyword.visualrecognitionshort}} projects.
    1.  Download the _data assets_ that you used to create the models from the same **Assets** page.
    1.  For your Core ML applications, you can download the Core ML model file from the **Implementation** area of the model.
- Classifiers created with the API:
    - If you created the classifier with the API, there is no method to download the training images. Make sure that you store a backup of those images.
    - For your Core ML applications, you can download the Core ML model file by using the [**Retrieve a Core ML model of a classifier** ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition#retrieve-a-core-ml-model-of-a-classifier){: new_window} API method.

Save these files in a safe location.

#### Restoring your image classification custom model
{: #ha-dr-restore-v3}

You can now re-create your custom model with the images you saved. For more information, see [Creating a custom model](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).

### Disaster recovery with Custom Object Detection
{: #ha-dr-v4-overview}

For the Custom Object Detection feature, your disaster recovery plan includes images, training data and collection metadata.

#### Backing up collections
You want to store the images and the training data that you use to train a collection. You can also save the collection metadata to use to re-create a collection.

You can download the files and data with the {{site.data.keyword.visualrecognitionshort}} v4 API:

- Collections. Use the [**List collections** ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition-v4#list-collections){: new_window} method to get each `collection_id`.
- Image metadata. Use [**List images** ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition-v4#list-images){: new_window} to get the `image_id` for each image in each collection.
- Image files in .jpeg format. Use [**Get a JPEG file of an image** ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition-v4#get-a-jpeg-file-of-an-image){: new_window} to download each image in each collection. Only the images with training data form your training set and are used to train a collection.
- Image training data. Use [**Get image details** ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/visual-recognition-v4#get-image-details){: new_window} for the training data of each `image_id` in each collection.

#### Restore your collection
{: #ha-dr-recreate-v4}

You can now re-create your collection with the files and data you saved. For more information, see [Custom Object Detection](/docs/services/visual-recognition?topic=visual-recognition-object-detection-overview#object-detection-sequence) and search for "How to use Custom Object Detection."

### Client applications
{: #ha-dr-update-apps}

When you re-create a model or collection, the values of some items change, and these values might be used by your own applications.

- A different service instance has a new API key and might have a different URL.
- For image classification, the custom model has a different `classifier_id`.
- For v4, the collection has a new ID and the images might have new IDs.
