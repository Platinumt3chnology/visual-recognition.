---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-02"

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

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## GDPR in Visual Recognition
{: #gdpr-visrec}

### GDPR Security Migration
{: #gdpr-visrec-update}

- All {{site.data.keyword.visualrecognitionfull}} service instances created before **May 22, 2018** are not suitable for clients that require compliance with the EU General Data Protection Regulation EU 2016/679 (GDPR).

- Clients that are subject to GDPR need to migrate to a new {{site.data.keyword.visualrecognitionfull}} service instance available on **May 22nd, 2018** and to adopt the new agreement for the {{site.data.keyword.visualrecognitionfull}} service.

- Clients will be required to provision a new {{site.data.keyword.visualrecognitionfull}} service and generate *new authentication keys* to utilize the new {{site.data.keyword.visualrecognitionfull}} service.

- If a client does not provision the new {{site.data.keyword.visualrecognitionfull}} service, you confirm that IBM is not processing any Personal Data on the client's behalf that is subject to the GDPR.

- The existing {{site.data.keyword.visualrecognitionfull}} service will come to an end on the **October 1st, 2018** and clients who have not moved to the new service by this time will have their data deleted.

### Migration steps
{: #gdpr-visrec-steps}

A forthcoming update to the {{site.data.keyword.visualrecognitionfull}} service is planned that will effectively allow your previously trained custom models/classifiers to be available in your new service instance.

- You will first be required to provision a new instance of the {{site.data.keyword.visualrecognitionshort}} service and generate new authentication keys for the new service.

- You will then use your prior and new {{site.data.keyword.visualrecognitionshort}} plan service authentication keys to request the migration of your custom models to your new {{site.data.keyword.visualrecognitionshort}} service instance.

**IMPORTANT**: For customers using the SDK, you will need to update your SDK version to be compatible with the new authentication process.

### FAQ/Support
{: #gdpr-visrec-faq}

Please direct questions to your account representative, or reach out to support directly here: [https://ibm.biz/ibmcloudsupport](https://ibm.biz/ibmcloudsupport).
