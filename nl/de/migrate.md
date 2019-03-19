---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Migrieren
{: #migrating}

Zum Migrieren Ihrer aktuellen Modelle (Klassifikationsmerkmale) stellen Sie eine neue Instanz des {{site.data.keyword.visualrecognitionshort}}-Service bereit. Bei angepassten Modellen wird das Modell neu trainiert, indem ein weiteres Modell (Klassifikationsmerkmal) mit den Bildern aus dem früheren Modell erstellt wird.
{: shortdesc}

{{site.data.keyword.visualrecognitionfull}}-Serviceinstanzen, die **vor** dem 23. Mai 2018 erstellt wurden, haben die Host-URL `gateway-a.watsonplatform.net`. Diese Instanzen müssen auf eine {{site.data.keyword.visualrecognitionshort}}-Serviceinstanz migriert werden, damit sie weiterhin verwendet werden können.
{: deprecated}

1.  Erstellen Sie eine weitere Instanz des {{site.data.keyword.visualrecognitionshort}}-Service:
    1.  Wechseln Sie zur Seite [{{site.data.keyword.visualrecognitionshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/visual-recognition){: new_window} im Katalog.
    1.  Wählen Sie einen Plan aus und klicken Sie auf **Erstellen**.
1.  Kopieren Sie die neuen Berechtigungsnachweise, um sich bei Ihrer Serviceinstanz zu authentifizieren:
    1.  Klicken Sie auf der Seite **Verwalten** auf **Berechtigungsnachweise anzeigen**.
    1.  Kopieren Sie den Wert für `API Key` (API-Schlüssel).
1.  [Erstellen und trainieren Sie Ihre angepassten Modelle](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) in Ihrer neuen Instanz des {{site.data.keyword.visualrecognitionshort}}-Service.
1.  Ändern Sie die Art, wie der Service aufgerufen wird.

    Geben Sie dazu entweder einen IAM-Schlüssel (Identitäts- und Zugriffsmanagement) oder ein Zugriffstoken für Ihre Serviceinstanz an. Tokens bieten mehr Sicherheit, da sie regelmäßig erneuert werden müssen, und unterstützen Anforderungen, ohne dass Ihre Berechtigungsnachweise für den eingebetteten Service in jeden Aufruf eingeschlossen werden. API-Schlüssel verwenden die Basisauthentifizierung und laufen nicht ab.

    - Weitere Informationen zu Tokens finden Sie unter [Authentifizierung mit IAM-Tokens](/docs/services/watson?topic=watson-iam#iam).
    - Weitere Informationen zur Verwendung eines IAM-API-Schlüssels finden Sie in der [API-Referenz](https://{/apidocs/visual-recognition/#authentication).
