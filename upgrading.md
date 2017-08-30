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

# Upgrading from beta to GA of the Visual Recognition service

On May 20, 2016, the {{site.data.keyword.visualrecognitionshort}} service released in General Availability (GA). The following sections explain how to upgrade from beta to GA.
{: shortdesc}

Any custom classifiers that were created while the service was in Beta will not be available in GA and must be recreated in a GA instance of the service. To use the GA features of the {{site.data.keyword.visualrecognitionshort}} service with a {{site.data.keyword.Bluemix}} application that uses a beta instance of the service, complete the following steps:

1.  Create a new {{site.data.keyword.watson}} {{site.data.keyword.visualrecognitionshort}} instance.
1.  Bind the new instance of the service to your app in {{site.data.keyword.Bluemix}}.
1.  Gather the data that was used to initially create the custom classifiers. For more information, see [Structure of the training data](/docs/services/visual-recognition/customizing.html#structure).
1.  Upload the training data to create new custom classifiers in the GA instance. For more information, see [Guidelines for training classifiers](/docs/services/visual-recognition/customizing.html).
1.  In your app, point to the new custom classifiers.
1.  Unbind the beta service from your app in {{site.data.keyword.Bluemix}}, and then delete it.

To learn more about the changes made to the {{site.data.keyword.visualrecognitionshort}} service from beta to GA, see the [Release notes](/docs/services/visual-recognition/release-notes.html).

