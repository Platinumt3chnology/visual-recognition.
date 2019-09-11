---

copyright:
  years: 2019
lastupdated: "2019-09-11"

keywords: activity,tracker,events,API,public API,subscription,binding

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
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.visualrecognitionshort}} Activity Tracker events
{: #at-events}

When you have {{site.data.keyword.visualrecognitionshort}} provisioned as a service in your {{site.data.keyword.cloud_notm}} account, you can see the following events in the [{{site.data.keyword.cloud_notm}} Activity Tracker](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).
{: shortdesc}

## List of events
{: #at-pubapi}

| Action | Description |
| -- | -- |
| visual_recognition.classifiers.get_core_ml_model | Retrieve a Core ML model file of a classifier |
| visual_recognition.classifiers.post | Train a new multi-faceted classifier on the uploaded image data |
| visual_recognition.classifiers.delete | Delete a classifier |
| visual_recognition.user_data.delete | Delete all data associated with a specified customer ID |
| visual_recognition.collection_images.get | Retrieve an image from a collection |
| visual_recognition.collection_images.post | Add an image to a collection |
| visual_recognition.collection_images.delete | Delete an image from a collection |
| visual_recognition.collection.delete | Delete all data associated with a specified image collection |

## Where to view events
{: #at-view}

Activity Tracker events are available in the Activity Tracker **account domain** that is available in the {{site.data.keyword.cloud_notm}} region where the events are generated.
