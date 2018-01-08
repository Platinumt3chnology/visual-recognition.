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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Benutzerdefiniertes Klassifikationsmerkmal erstellen

Wenn Sie ein Bild im "Lernprogramm zur Einführung" klassifiziert haben, können Sie ein benutzerdefiniertes Klassifikationsmerkmal (oder Modell) trainieren und erstellen. Mit einem benutzerdefinierten Klassifikationsmerkmal können Sie den {{site.data.keyword.visualrecognitionshort}}-Service trainieren, um Bilder entsprechend Ihren Geschäftsanforderungen zu klassifizieren.
{: shortdesc}

## Schritt 1: Berechtigungsnachweise kopieren
{: #copy-credentials}

Verwenden Sie die Berechtigungsnachweise, die Sie im "Lernprogramm zur Einführung" kopiert haben. Wenn Sie keine Serviceinstanz erstellt haben, führen Sie diese Schritte im Abschnitt [Vorbereitende Schritte](/docs/services/visual-recognition/getting-started.html#prerequisites) aus.

## Schritt 2: Benutzerdefiniertes Klassifikationsmerkmal erstellen
{: #create}

{{site.data.keyword.visualrecognitionshort}} kann anhand von Beispielbildern lernen, die Sie hochladen, um ein neues Klassifikationsmerkmal mit mehreren Facetten zu erstellen. Jede Beispieldatei wird anhand der anderen Dateien in diesem Aufruf trainiert und positive Beispiele werden als Klassen gespeichert. Diese Klassen werden gruppiert, um ein einzelnes Klassifikationsmerkmal zu definieren, und sie geben ihre eigenen Scores zurück. Dateien mit negativen Beispielen werden nicht als Klassen gespeichert.

1.  Laden Sie die Beispieltrainingsdateien <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> und <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Rufen Sie die Methode `POST /v3/classifiers` mit dem folgenden Befehl auf, der die Trainingsdaten hochlädt und ein Klassifikationsmerkmal `dogs` erstellt:
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.
    - Ändern Sie die Position von `{klasse}_positive_examples`, um dorthin zu verweisen, wo Sie die .zip-Dateien gespeichert haben.

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

    Die Namen von Dateien mit positiven Beispielen erfordern das Suffix `_positive_examples`. In diesem Beispiel lauten die Dateinamen `beagle_positive_examples`, `goldenretriever_positive_examples` und `husky_positive_examples`. Das Präfix (beagle, goldenretriever und husky) wird als Klassenname zurückgegeben.{:tip }

    Die Antwort enthält eine neue ID und einen Status für das Klassifikationsmerkmal. Beispiel:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
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
      ]
    }
    ```
    {: codeblock}

1.  Prüfen Sie den Trainingsstatus in regelmäßigen Abständen, bis der Status `ready` (Bereit) angezeigt wird. Das Training beginnt unmittelbar und muss abgeschlossen sein, bevor Sie das Klassifikationsmerkmal abfragen können. Ersetzen Sie `{api-schlüssel}` und `{klassifikationsmerkmal-id}` durch Ihre Informationen:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{klassifikationsmerkmal-id}?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

## Schritt 3: Vorhandenes Klassifikationsmerkmal aktualisieren

Sie können ein benutzerdefiniertes Klassifikationsmerkmal nicht mit einem kostenlosen API-Schlüssel aktualisieren. Wenn Sie einen kostenlosen Schlüssel haben, können Sie ein Upgrade auf einen Standardplan ausführen. Weitere Informationen hierzu finden Sie unter [Plan ändern](https://console.bluemix.net/docs/pricing/changing_plan.html).
{: tip}

Sie können ein benutzerdefiniertes Klassifikationsmerkmal aktualisieren, indem Sie Klassen zu dem Klassifikationsmerkmal hinzufügen oder indem Sie Bilder zu einer vorhandenen Klasse hinzufügen. Hier verbessern Sie das Klassifikationsmerkmal, das Sie in Schritt 2 erstellt haben, indem Sie eine Klasse *dalmatian* (Dalmatiner) zu den Hundearten hinzufügen, die klassifiziert werden können. Außerdem fügen Sie Bilder von Katzen zu den negativen Beispielen für das Klassifikationsmerkmal "dogs" hinzu.

1.  Laden Sie die Beispieltrainingsdateien <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> und <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Rufen Sie die Methode `POST /v3/classifiers/{klassifikationsmerkmal-id}` mit dem folgenden cURL-Befehl auf, der die Trainingsdaten hochlädt und das Klassifikationsmerkmal "dogs\_1941945966" aktualisiert:
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.
    - Ersetzen Sie `{klassifikationsmerkmal-id}` durch die ID des Klassifikationsmerkmals, das Sie aktualisieren wollen.
    - Ändern Sie die Position von `{klasse}_positive_examples`, um dorthin zu verweisen, wo Sie die .zip-Dateien gespeichert haben.

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatiner.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{klassifikationsmerkmal-id}?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

    Das vorhandene Klassifikationsmerkmal "dogs" wird durch das neu trainierte Klassifikationsmerkmal mit derselben "klassifikationsmerkmal-id" ersetzt. Die Antwort listet die neue Gruppe von Klassen und den aktuellen Status auf. Beispiel:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    Das Training beginnt sofort. Wenn das neue verfügbar ist, ändert sich der Status in `ready` (Bereit).

Geben Sie erst nach dem aktuellen Status `ready` eine Anforderung zum Neutrainieren aus. Wenn Sie das Neutrainieren eines Klassifikationsmerkmals mehrfach anfordern, führt dies dazu, dass einmalig neu trainiert wird. Eine Zeitmarke mit der Bezeichnung `retrained` (Neu trainiert) wird für den Zeitpunkt angezeigt, zu dem das Klassifikationsmerkmal zum letzten Mal neu trainiert wurde. Wenn Sie die Methode `/classify` aufrufen, während das Klassifikationsmerkmal neu trainiert wird, wird die alte Definition des Klassifikationsmerkmals verwendet.
    {: tip}
1.  Prüfen Sie den Trainingsstatus in regelmäßigen Abständen, bis der Status `ready` angezeigt wird. Ersetzen Sie `{api-schlüssel}` und `{klassifikationsmerkmal-id}` durch Ihre Informationen:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{klassifikationsmerkmal-id}?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

## Schritt 4: Bild mit einem benutzerdefinierten Klassifikationsmerkmal klassifizieren
{: #classify}

Wenn das neue Klassifikationsmerkmal bereit ist, rufen Sie es auf, um zu ermitteln, wie es sich verhält.

1.  Erstellen Sie eine JSON-Datei mit dem Namen `myparams.json`, die die Parameter für Ihren Aufruf enthält, z. B. die Klassifikationsmerkmal-ID`` für Ihr neues Klassifikationsmerkmal und für das Klassifikationsmerkmals des Modells "Allgemein" (das die Klassifikationsmerkmal-ID `default`) verwendet. Eine einfache JSON-Datei könnte wie folgt aussehen:

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  Laden Sie die Datei <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Verwenden Sie die Methode `POST /v3/classify`, um Ihr benutzerdefiniertes Klassifikationsmerkmal zu testen. Das folgende Beispiel klassifiziert das Bild `dogs.jpg` anhand des Klassifikationsmerkmals "dogs\_1941945966":
    - Ersetzen Sie `{api-schlüssel}` durch die Serviceberechtigungsnachweise, die Sie im ersten Schritt kopiert haben.

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-schlüssel}&version=2016-05-20"
    ```
    {: pre}

    Wenn Sie die Klassifizierung nur anhand des integrierten Modells "Allgemein" vornehmen wollen, lassen Sie den Parameter `parameters` aus.
    {: tip}

    Die Antwort enthält Klassifikationsmerkmale, ihre Klassen und einen Score für jede Klasse. Die Scores liegen im Bereich von 0 bis 1, wobei ein höherer Score eine größere Korrelation bedeutet. Die `/v3/classify`-Aufrufe lassen Klassen mit geringem Score standardmäßig aus, wenn Klassen mit hohem Score identifiziert werden. Sie können einen Mindestscore für die Anzeige festlegen, indem Sie einen Gleitkommawert für den Parameter `threshold` in Ihrem Aufruf angeben.

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  Prüfen Sie Ihre Ergebnisse.

Sie sind fertig! Sie haben ein benutzerdefiniertes Klassifikationsmerkmal mit {{site.data.keyword.visualrecognitionshort}} erstellt, trainiert und abgefragt.

### Benutzerdefiniertes Klassifikationsmerkmal löschen

Sie können Ihr benutzerdefiniertes Klassifikationsmerkmal löschen, wenn Sie die Entwicklung Ihrer Anwendung mit einer bereinigten Instanz beginnen wollen. 

Um das Klassifikationsmerkmal zu löschen, rufen Sie die Methode `DELETE /v3/classifiers/{klassifikationsmerkmal-id}` auf. Ersetzen Sie `{api-schlüssel)` und `klassifikationsmerkmal-id` durch Ihre Informationen:

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{klassifikationsmerkmal-id}?api_key={api-schlüssel}&version=2016-05-20"
```
{: pre}

## Nächste Schritte

Sie haben nun ein grundlegendes Verständnis davon, wie Sie die benutzerdefinierten Klassifikationsmerkmale verwenden. Hier finden Sie weitergehende Informationen:

- [Bewährte Verfahren für benutzerdefinierte Klassifikationsmerkmale ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Bildnachweis
{: #attributions}

Alle Bilder auf dieser Seite stammen aus Flikr und werden unter [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} verwendet. An diesen Bildern wurden keine Änderungen vorgenommen.
