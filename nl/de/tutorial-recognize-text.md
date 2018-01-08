---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# Text in einem Bild erkennen

{: shortdesc}

## Vorbereitende Schritte
{: #copy-credentials}

Verwenden Sie die Berechtigungsnachweise, die Sie im "Lernprogramm zur Einführung" für dieses Lernprogramm kopiert haben. Wenn Sie keine Serviceinstanz erstellt haben, führen Sie diese Schritte im Abschnitt [Vorbereitende Schritte](/docs/services/visual-recognition/getting-started.html#prerequisites) aus.

## Schritt 1: Text in einem Bild erkennen
{: #recognize-text}

1.  Laden Sie das Beispielbild <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Geben Sie den folgenden Befehl für die Methode `POST /v3/recognize_text` ein, um das Bild hochzuladen und zu analysieren. Wenn Sie Ihr eigenes Bild verwenden, beträgt die maximale Größe 2 MB:
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie zuvor kopiert haben.
    - Ändern Sie die Position von images\_file, um dorthin zu verweisen, wo Sie das Bild gespeichert haben.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-schlüssel}&version=2016-05-20"
    ```

    Die Antwort enthält eine Position, ein geschätztes Alter, das Geschlecht sowie Identität, Typhierarchie (wenn der Service das Gesicht erkennt) und einen Score für alle.

    Die Scores liegen im Bereich von 0 bis 1, wobei ein höherer Score eine größere Korrelation bedeutet. Alle Gesichter werden erkannt, aber bei Bildern mit mehr als zehn Gesichtern werden für Alter und Geschlecht möglicherweise Scores von 0 zurückgegeben.


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## Nächste Schritte

Sie haben nun ein grundlegendes Verständnis davon, wie Sie die Standardklassifikationsmerkmale bei {{site.data.keyword.visualrecognitionshort}} verwenden. Weitergehende Informationen finden Sie hier:

- Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Bildnachweis
{: #attributions}

Alle Bilder auf dieser Seite stammen aus Flikr und werden unter [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} verwendet. An diesen Bildern wurden keine Änderungen vorgenommen.
