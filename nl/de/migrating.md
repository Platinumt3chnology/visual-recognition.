---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# {{site.data.keyword.alchemyvisionshort}} auf {{site.data.keyword.visualrecognitionshort}} migrieren

Am 19. Mai 2016 wurde der Vertrieb des {{site.data.keyword.alchemyvisionshort}}-Service eingestellt und seine Funktionalität wurde in {{site.data.keyword.visualrecognitionshort}} (GA) integriert. Um eine unter {{site.data.keyword.Bluemix_notm}} bereitgestellte Anwendung vom {{site.data.keyword.alchemyvisionshort}}-Service zum {{site.data.keyword.visualrecognitionshort}}-Service zu migrieren, müssen Sie den Code aktualisieren.
{: shortdesc}

Die folgenden Unterschiede zwischen {{site.data.keyword.alchemyvisionshort}} und {{site.data.keyword.visualrecognitionshort}} können sich auf Ihren Anwendungscode auswirken:

- **Klassen und Klassifikationsmerkmale:** In {{site.data.keyword.alchemyvisionshort}} werden analysierte Bilder mit "Tags" gekennzeichnet. In {{site.data.keyword.visualrecognitionshort}} werden "Tags" als "Klassen" bezeichnet. Gruppen von Klassen sind "Klassifikationsmerkmale". Alle Standardtags von {{site.data.keyword.alchemyvisionshort}} sind weiterhin als Klassen in {{site.data.keyword.visualrecognitionshort}} verfügbar.
- **Benutzerdefinierte Klassifikationsmerkmale:** Bei {{site.data.keyword.visualrecognitionshort}} können Sie benutzerdefinierte Klassifikationsmerkmale und Klassen trainieren und erstellen.
- **Stapeleingabe:** In {{site.data.keyword.visualrecognitionshort}} können Sie nun Bildstapel oder Bild-URLs klassifizieren, indem Sie Bilddateien in einer komprimierten Datei (.zip) oder eine einzelne Bild-URL in einer JSON-Zeichenfolge zur Verarbeitung übergeben.
- **Angabe der Sprache:** In {{site.data.keyword.alchemyvisionshort}} haben Sie die Sprache eines Tagging-Aufrufs als Abfrageparameter angegeben. In {{site.data.keyword.visualrecognitionshort}} geben Sie die Sprache eines Classify-Aufrufs im Header `Accept-Language` an.
- **Endpunkte:** Die folgende {{site.data.keyword.alchemyvisionshort}}-Funktionalität ist in den neuen Endpunkten im GA-Release von {{site.data.keyword.visualrecognitionshort}} enthalten:

| Funktionalität | {{site.data.keyword.alchemyvisionshort}}-Endpunkt (veraltet) | {{site.data.keyword.visualrecognitionshort}}-Endpunkt (GA) |
|---------------|--------------------|----------------|
| Tagging von Bildern mit integrierten Klassifikationsmerkmalen | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Erkennung von Gesichtern, einer Altersgruppe und des Geschlechts | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Extraktion eines Hauptbilds aus HTML oder einer Website-URL | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | Sie können ein Bild per URL für die Methoden `/v3/classify` und `/v3/detect_faces` zur Verfügung stellen, nicht aber durch einen eigenständigen Endpunkt.|
