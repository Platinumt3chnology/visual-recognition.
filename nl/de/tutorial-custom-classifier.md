---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Angepasstes Modell erstellen
{: #tutorial-custom-classifier}

Wenn Sie im "Lernprogramm zur Einführung" ein Bild analysiert haben, können Sie ein angepasstes Modell trainieren und erstellen. Mit einem angepassten Modell können Sie den {{site.data.keyword.visualrecognitionshort}}-Service trainieren, um Bilder entsprechend Ihren Geschäftsanforderungen klassifizieren zu können.
{: shortdesc}

## Schritt 1: Berechtigungsnachweise kopieren
{: #copy-credentials}

Verwenden Sie die Berechtigungsnachweise, die Sie im "Lernprogramm zur Einführung" kopiert haben. Wenn Sie keine Serviceinstanz erstellt haben, führen Sie diese Schritte im Abschnitt [Vorbereitende Schritte](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites) aus.

## Schritt 2: Angepasstes Modell erstellen
{: #create}

{{site.data.keyword.visualrecognitionshort}} kann anhand von Beispielbildern, die Sie hochladen, lernen, ein neues Modell mit mehreren Facetten zu erstellen. Jede Beispieldatei wird anhand der anderen Dateien in diesem Aufruf trainiert und positive Beispiele werden als Klassen gespeichert. Diese Klassen werden gruppiert, um ein einzelnes Modell zu definieren, und geben ihre eigenen Scores zurück. Dateien mit negativen Beispielen werden nicht als Klassen gespeichert.

1.  Laden Sie die Beispieltrainingsdateien <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> und <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> herunter.
1.  Rufen Sie die Methode `POST /v3/classifiers` mit dem folgenden Befehl auf, der die Trainingsdaten hochlädt und das angepasste Modell `dogs` erstellt:
    - Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.
    - Ändern Sie die Position von `{klasse}_positive_examples`, um dorthin zu verweisen, wo Sie die .zip-Dateien gespeichert haben.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    Die Namen von Dateien mit positiven Beispielen erfordern das Suffix `_positive_examples`. In diesem Beispiel lauten die Dateinamen `beagle_positive_examples`, `goldenretriever_positive_examples` und `husky_positive_examples`. Das Präfix (beagle, goldenretriever und husky) wird als Klassenname zurückgegeben.
    {:tip }

    Die Antwort enthält eine neue ID und einen Status für das Klassifikationsmerkmal. Beispiel:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  Prüfen Sie den Trainingsstatus in regelmäßigen Abständen, bis der Status `ready` (Bereit) angezeigt wird. Das Training beginnt sofort und muss abgeschlossen sein, bevor Sie das Modell abfragen können. Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) und `{classifier_id}` (die Klassifikationsmerkmal-ID) durch Ihre Angaben:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Schritt 3: Vorhandenes angepasstes Modell aktualisieren
{: #tutorial-custom-classifier-update}

Sie können ein angepasstes Modell aktualisieren, indem Sie entweder Klassen zum Modell hinzufügen oder Bilder zu einer vorhandenen Klasse hinzufügen. Hier verbessern Sie das Modell, das Sie in Schritt 2 erstellt haben, durch Hinzufügen einer Klasse *dalmatian* (Dalmatiner) zu den klassifizierbaren Hunderassen. Zusätzlich fügen Sie Bilder von Katzen zu der Gruppe von negativen Beispielen für das angepasste Modell "dogs" hinzu.

1.  Laden Sie die Beispieltrainingsdateien <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> und <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> herunter.
1.  Rufen Sie die Methode `POST /v3/classifiers/{classifier_id}` mit dem folgenden cURL-Befehl auf, der die Trainingsdaten hochlädt und das angepasste Modell "dogs\_1941945966" aktualisiert:
    - Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.
    - Ersetzen Sie `{classifier_id}` (die Klassifizierungs-ID) durch die ID des angepassten Modells, das Sie aktualisieren wollen.
    - Ändern Sie die Position von `{klasse}_positive_examples`, um dorthin zu verweisen, wo Sie die .zip-Dateien gespeichert haben.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    Das vorhandene angepasste Modell "dogs" wird durch das neu trainierte Modell mit derselben Klassifizierungs-ID ersetzt. Die Antwort listet die neue Gruppe von Klassen und den aktuellen Status auf. Beispiel:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    Das Training beginnt sofort. Wenn das neue verfügbar ist, ändert sich der Status in `ready` (Bereit).

    Geben Sie erst nach dem aktuellen Status `ready` eine Anforderung zum Neutrainieren aus. Wenn Sie das Neutrainieren eines Modells mehrfach anfordern, führt dies dazu, dass einmalig neu trainiert wird. Eine Zeitmarke mit dem Namen `updated` zeigt die Zeit an, zu der das Modell zuletzt aktualisiert wurde. Wenn Sie die Methode `/classify` aufrufen, während das Modell neu trainiert wird, wird die alte Definition des Modells verwendet.
    {: tip}
1.  Prüfen Sie den Trainingsstatus in regelmäßigen Abständen, bis der Status `ready` (Bereit) angezeigt wird. Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) und `{classifier_id}` (die Klassifikationsmerkmal-ID) durch Ihre Angaben:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Schritt 4: Bild mit einem angepassten Modell klassifizieren
{: #tutorial-custom-classifier-classify}

Wenn das neue Modell bereit ist, rufen Sie es auf, um zu ermitteln, wie es sich verhält.

1.  Laden Sie die Datei <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> herunter.
1.  Verwenden Sie die Methode `POST /v3/classify` zum Testen Ihres angepassten Modells. Im folgenden Beispiel wird das Bild `dogs.jpg` anhand des angepassten Modells "dogs\_1941945966" und des integrierten allgemeinen Modells `default` klassifiziert:
    - Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    Für eine Klassifizierung nur anhand des integrierten allgemeinen Modells lassen Sie den Parameter `classifier_ids` aus.
    {: tip}

    Die Antwort enthält Klassifikationsmerkmale, ihre Klassen sowie einen Score für jede Klasse. Die Scores liegen im Bereich von 0 bis 1, wobei ein höherer Score eine größere Korrelation bedeutet. Die `/v3/classify`-Aufrufe lassen Klassen mit geringem Score standardmäßig aus, wenn Klassen mit hohem Score identifiziert werden. Sie können einen Mindestscore für die Anzeige festlegen, indem Sie einen Gleitkommawert für den Parameter `threshold` in Ihrem Aufruf angeben.

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  Prüfen Sie Ihre Ergebnisse.

Sie sind fertig! Sie haben ein angepasstes Modell mit {{site.data.keyword.visualrecognitionshort}} erstellt, trainiert und abgefragt.

### Angepasstes Modell löschen
{: #tutorial-custom-classifier-delete}

Möglicherweise möchten Sie Ihr angepasstes Modell löschen, um die Entwicklung Ihrer Anwendung in einer sauberen Instanz zu beginnen.

Zum Löschen des Modells rufen Sie die Methode `DELETE /v3/classifiers/{classifier_id}` auf. Ersetzen Sie `{your_api_key)` (Ihren API-Schlüssel) und `classifier_id` (die Klassifikationsmerkmal-ID) durch Ihre Angaben:

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## Nächste Schritte
{: #tutorial-custom-classifier-next-steps}

Mit diesem grundlegenden Verständnis von der Verwendung angepasster Modelle können Sie nun komplexere Aufgaben vornehmen:

- [Bewährte Verfahren für benutzerdefinierte Klassifikationsmerkmale ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Bildnachweis
{: #tutorial-custom-classifier-attributions}

Alle Bilder auf dieser Seite stammen aus Flikr und werden unter [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} verwendet. An diesen Bildern wurden keine Änderungen vorgenommen.
