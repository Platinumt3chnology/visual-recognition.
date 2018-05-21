---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-21"

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

# Migrating
{: #migrating}

Migrate to a new instance of the {{site.data.keyword.visualrecognitionfull}} service after May 22, 2018.
{: shortdesc}

To migrate your current models/classifiers and training data, you are first required to provision a new instance of the {{site.data.keyword.visualrecognitionshort}} service. Then, take the images you used to train the models in your current {{site.data.keyword.visualrecognitionshort}} service instance, and use those images to re-create your custom models in your new {{site.data.keyword.visualrecognitionshort}} service instance.

1.  Create a new instance of the {{site.data.keyword.visualrecognitionshort}} service:
      - Go to the [{{site.data.keyword.visualrecognitionshort}} page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} in the {{site.data.keyword.cloud_notm}} catalog.
      - Select a plan and click **Create**.
1.  From the service dashboard, select your new {{site.data.keyword.visualrecognitionshort}} service instance, then:
     - Click the **Service credentials** tab and select *View credentials*.
     ![Service credentials tab](images/apikey1.png)
     - Copy the API key as indicated here. You will need this key to re-create and train your custom models.
     ![Service credentials tab](images/apikey2.png)
1.  [Re-create your custom models](tutorial-custom-classifier.html#creating-a-custom-model) in your new instance of the {{site.data.keyword.visualrecognitionshort}} service.
1.  [Train your custom models](customizing.html#guidelines-for-training-classifiers) with your new {{site.data.keyword.visualrecognitionshort}} service instance.

**Note**: To create and train custom models in Watson Studio, [launch the Watson Studio tooling] ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-legacy){: new_window} after creating your new {{site.data.keyword.visualrecognitionshort}} service instance.
