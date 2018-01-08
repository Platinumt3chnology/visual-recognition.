---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Lernprogramm zur Einführung

In diesem Lernprogramm wird schrittweise beschrieben, wie integrierte Klassifikationsmerkmale in {{site.data.keyword.visualrecognitionfull}} verwendet werden können, um ein Bild zu klassifizieren und dann Gesichter in einem Bild zu erkennen.
{: shortdesc}

## Vorbereitende Schritte
{: #prerequisites}

- Erstellen Sie eine Instanz des Service:
    - {: download} Wenn Sie dies sehen, haben Sie Ihre Serviceinstanz erstellt. Fordern Sie nun Ihre Berechtigungsnachweise an.
    - Erstellen Sie ein Projekt aus dem Service:
        1.  Wechseln Sie in der {{site.data.keyword.watson}} Developer Console zur Seite [Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Wählen Sie {{site.data.keyword.visualrecognitionshort}} aus, klicken Sie auf **Services hinzufügen** und registrieren Sie sich für ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
        1.  Geben Sie `vision-tutorial` als Projektname ein und klicken Sie auf **Projekt erstellen**.
- Kopieren Sie die Berechtigungsnachweise, um sich für Ihre Serviceinstanz zu authentifizieren:
    - {: download} Gehen Sie vom Service-Dashboard (das gerade angezeigt wird) wie folgt vor:
        1.  Klicken Sie auf die Registerkarte **Serviceberechtigungsnachweise**.
        1.  Klicken Sie unter **Aktionen** auf **Berechtigungsnachweise anzeigen**.
        1.  Kopieren Sie den Wert "api-schlüssel".
        {: download}
    - Kopieren Sie in Ihrem Projekt **vision-tutorial** in der Developer Console den Wert `api-schlüssel` für `"visual_recognition"` aus dem Abschnitt **Berechtigungsnachweise**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Wenn Sie {{site.data.keyword.Bluemix_dedicated_notm}} verwenden, erstellen Sie Ihre Serviceinstanz von der Seite [{{site.data.keyword.visualrecognitionshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} im Katalog. Hinweise dazu, wie Sie Ihre Serviceberechtigungsnachweise finden, enthält der Abschnitt [Serviceberechtigungsnachweise für Watson-Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Schritt 1: Bild klassifizieren
{: #classify}

1.  Laden Sie das Beispielbild <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Geben Sie den folgenden Befehl ein, um das Bild hochzuladen und es anhand aller integrierten Klassifikationsmerkmale zu klassifizieren:
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie zuvor kopiert haben.
    - Ändern Sie die Position von images\_file, um dorthin zu verweisen, wo Sie das Bild gespeichert haben.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

    Wenn Sie mit {{site.data.keyword.Bluemix_notm}} Dedicated arbeiten, ist der Endpunkt `gateway-a.watsonplatform.net` hier möglicherweise nicht Ihr Serviceendpunkt. Prüfen Sie die `URL` auf der Seite **Serviceberechtigungsnachweise** Ihres Service-Dashboards.{: tip}

    Die Antwort enthält das Modell oder das Klassifikationsmerkmal "Allgemein" (mit der Klassifikationsmerkmal-ID `default`), die im Bild identifizierten Klassen und einen Score für jede Klasse.

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    Die Verlässlichkeitsscores liegen im Bereich von 0 bis 1, wobei ein höherer Score eine größere Korrelation bedeutet. Standardmäßig enthalten die `/v3/classify`-Aufrufe keine Klassen mit einem Score unter `0,5`.

## Schritt 2: Gesichter in einem Bild erkennen
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} kann in Bildern Gesichter erkennen. Die Antwort bietet verschiedene Informationen wie die Position des Gesichts in dem Bild sowie die geschätzte Altersgruppe und das Geschlecht jeder Person.

Der Service erkennt auch viele bekannte Persönlichkeiten aus dem öffentlichen Leben und er kann einen *Knowledge Graph* bereitstellen, in dem Informationen systematisch miteinander verknüpft werden können.

1.  Laden Sie das Beispielbild <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Geben Sie den folgenden Befehl für die Methode `POST /v3/detect_faces` ein, um das Bild hochzuladen und zu analysieren. Wenn Sie Ihr eigenes Bild verwenden, beträgt die maximale Größe 2 MB:
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie zuvor kopiert haben.
    - Ändern Sie die Position von images\_file, um dorthin zu verweisen, wo Sie das Bild gespeichert haben.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

    Die Antwort enthält eine Position, ein geschätztes Alter, das Geschlecht sowie Identität, Typhierarchie (wenn der Service das Gesicht erkennt) und einen Score für alle.

    Die Scores liegen im Bereich von 0 bis 1, wobei ein höherer Score eine größere Korrelation bedeutet. Alle Gesichter werden erkannt, aber bei Bildern mit mehr als zehn Gesichtern werden für Alter und Geschlecht möglicherweise Scores von 0 zurückgegeben.

    ```json
    {
      "images": [
    {
      "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Nächste Schritte

Sie haben nun ein grundlegendes Verständnis davon, wie Sie das integrierte Standardklassifikationsmerkmal bei {{site.data.keyword.visualrecognitionshort}} verwenden. Weitergehende Informationen finden Sie hier:

- Informationen dazu, wie Sie ein [benutzerdefiniertes Klassifikationsmerkmal erstellen](/docs/services/visual-recognition/tutorial-custom-classifier.html) können.
- Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Bildnachweis
{: #attributions}

- [Fruchtkorb ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://flic.kr/p/JPHES){: new_window} von Flikr-Benutzer [Ryan Edwards-Crewe ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.flickr.com/photos/ryanec/){: new_window}, verwendet unter der [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
- [Obama ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://bit.ly/1T0DCl9){: new_window} von Flikr-Benutzer [dcblog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.flickr.com/photos/12863058@N08/){: new_window}, verwendet unter der [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
