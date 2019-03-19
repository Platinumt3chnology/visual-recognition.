---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: classify,classifying,Visual Recognition,getting started,detecting faces,detect faces,food model,general model,sample code

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
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Lernprogramm zur Einführung

Dieses Lernprogramm führt Sie durch die Verwendung einiger integrierter Modelle in {{site.data.keyword.visualrecognitionfull}} zur Klassifizierung eines Bildes und anschließenden Gesichtserkennung darin.
{: shortdesc}

Wenn Sie lieber mit einer grafischen Schnittstelle arbeiten, verwenden Sie {{site.data.keyword.DSX}}. [Starten Sie das Tool ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} und folgen Sie dem [Video ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://youtu.be/898RN31szg0){: new_window}.
{: tip}

## Vorbereitende Schritte
{: #prerequisites}

- {: hide-dashboard} Erstellen Sie eine Instanz des Service:
    1.  Wechseln Sie zur Seite [{{site.data.keyword.visualrecognitionshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/visual-recognition){: new_window} im Katalog.
    1.  Registrieren Sie sich entweder für ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
    1.  Klicken Sie auf **Erstellen**.
- {: hide-dashboard} Kopieren Sie die Berechtigungsnachweise, um sich für Ihre Serviceinstanz zu authentifizieren:
    1.  Klicken Sie auf der Seite **Verwalten** auf **Berechtigungsnachweise anzeigen**.
    1.  Kopieren Sie den Wert für `API Key` (API-Schlüssel).
- {: curl} Achten Sie darauf, den `curl`-Befehl zu verwenden.
    - Testen Sie, ob `curl` installiert wurde. Führen Sie den folgenden Befehl in der Befehlszeile aus. Wenn in der Ausgabe die `curl`-Version mit SSL-Unterstützung aufgelistet wird, sind Sie für das Lernprogramm vorbereitet.

        ```bash
        curl -V
        ```
        {: pre}

    - Installieren Sie gegebenenfalls eine SSL-fähige Version von [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Fügen Sie die Position der Datei zu den Pfadumgebungsvariablen hinzu, falls Sie vorhaben, `curl` von einer Position der Befehlszeile aus auszuführen.
- {:go} Installieren Sie das [Start-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/go-sdk){: new_window}.

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} Installieren Sie das [Java-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/java-sdk){: new_window}.
    - {:java} Maven

        ```java
        <dependency>
          <groupId>com.ibm.watson.developer_cloud</groupId>
          <artifactId>java-sdk</artifactId>
          <version>{version}</version>
        </dependency>
        ```
        {: codeblock}

    - {:java} Gradle

        ```bash
        compile 'com.ibm.watson.developer_cloud:java-sdk:{version}'
        ```
        {:pre}
- {: javascript} Installieren Sie das [Node-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/node-sdk){: new_window}.

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} Installieren Sie das [Python-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/python-sdk){: new_window}.

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} Installieren Sie das [Ruby-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}.

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## Schritt 1: Bild klassifizieren
{: #classify}

1.  Geben Sie folgenden Aufruf aus, um [ein Bild ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window} zu klassifizieren. <span class="hide-dashboard">Ersetzen Sie `{apikey}` durch die zuvor kopierten Serviceberechtigungsnachweise.</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
          Version:   "2018-03-19",
          IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr != nil {
        panic(visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"),
        },
      )
      if responseErr != nil {
        panic(responseErr)
      }
      result := visualRecognition.GetClassifyResult(response)
      b, _ := json.MarshalIndent(result, "", "  ")
      fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    IamOptions options = new IamOptions.Builder()
      .apiKey("{apikey}"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg")
      .build();
    ClassifiedImages result = visualRecognition.classify(classifyOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');
    var fs = require('fs');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    var url= 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg';

    var params = {
      url: url,
    };

    visualRecognition.classify(params, function(err, response) {
      if (err) {
        console.log(err);
      } else {
        console.log(JSON.stringify(response, null, 2))
      }
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg'

    classes_result = visual_recognition.classify(url=url).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json"
    require "ibm_watson/visual_recognition_v3"
    include IBMWatson

    visual_recognition = VisualRecognitionV3.new(
      version: "2018-03-19",
      iam_apikey: "{apikey}"{: apikey}
    )
    url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"

    classes = visual_recognition.classify(url)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    Die Antwort enthält die Klassen, die im Bild über das integrierte Modell "Allgemein" (`"classifier_id": "default"`) erkannt wurden, sowie einen Konfidenzscore für jede Klasse. Der Score stellt einen Prozentsatz dar, höhere Werte stellen höhere Konfidenzen dar. Standardmäßig enthalten Antworten von den `Classify`-Aufrufen keine Klassen mit einem Score unter `0,5` (50%).

    ```json
    {
      "images": [
    {
          "classifiers": [
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "circuit board",
                  "score": 0.578,
                  "type_hierarchy": "/electrical device/computer circuit/circuit board"
                },
                {
                  "class": "computer circuit",
                  "score": 0.755
                },
                {
                  "class": "electrical device",
                  "score": 0.757
                },
                {
                  "class": "disk controller",
                  "score": 0.553,
                  "type_hierarchy": "/controller/disk controller"
                },
                {
                  "class": "controller",
                  "score": 0.558
                },
                {
                  "class": "central processing unit",
                  "score": 0.535
                },
                {
                  "class": "PC board",
                  "score": 0.501,
                  "type_hierarchy": "/electrical device/computer circuit/PC board"
                },
                {
                  "class": "CPU board",
                  "score": 0.5,
                  "type_hierarchy": "/electrical device/computer circuit/CPU board"
                },
                {
                  "class": "electronic equipment",
                  "score": 0.6
                },
                {
                  "class": "memory device",
                  "score": 0.599
                },
                {
                  "class": "microchip",
                  "score": 0.592
                },
                {
                  "class": "jade green color",
                  "score": 0.838
                },
                {
                  "class": "emerald color",
                  "score": 0.787
                }
              ]
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 0
    }
    ```
    {: codeblock}

## Schritt 2: Klassifizierung mit dem Modell "Food" (Lebensmittel)
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} enthält auch ein integriertes Modell "Food" (Lebensmittel), das für Bilder mit Lebensmitteln eine höhere Genauigkeit liefern könnte.

1.  Geben Sie einen Aufruf aus, um anhand des Modells für Lebensmittel ein [Bild mit Lebensmitteln ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} zu klassifizieren. <span class="hide-dashboard">Ersetzen Sie `{apikey}` durch die zuvor kopierten Serviceberechtigungsnachweise.</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} -F "classifier_ids=food" "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
          Version:   "2018-03-19",
          IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr != nil {
        panic(visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg"),
          ClassifierIds: []string{"food"},
        },
      )
      if responseErr != nil {
        panic(responseErr)
      }
      result := visualRecognition.GetClassifyResult(response)
      b, _ := json.MarshalIndent(result, "", "  ")
      fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    IamOptions options = new IamOptions.Builder()
      .apiKey("{apikey}"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    ClassifyOptions classifyOptions = new ClassifyOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg");
      .classifierIds(Arrays.asList("food"))
      .build();
    ClassifiedImages result = visualRecognition.classify(classifyOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    var url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg';
    var classifier_ids = ["food"];

    var params = {
      url: url,
      classifier_ids: classifier_ids
    };

    visualRecognition.classify(params, function(err, response) {
      if (err)
        console.log(err);
      else
        console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg'
    classifier_ids = ["food"]

    classes_result = visual_recognition.classify(url=url, classifier_ids=classifier_ids).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json"
    require "ibm_watson/visual_recognition_v3"
    include IBMWatson

    visual_recognition = VisualRecognitionV3.new(
      version: "2018-03-19",
      iam_apikey: "{apikey}"{: apikey}
    )
    url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"
    classifier_ids= ["food"]

    classes = visual_recognition.classify(url, classifier_ids)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    Der Service gibt die folgenden Ergebnisse zurück. Es ist zu sehen, dass die `classifier_id` (Klassifikationsmerkmal-ID) mit `food` angegeben ist. Die Klassen, die der Service identifiziert hat, unterscheiden sich auch von der ersten Antwort.

    ```json
    {
      "images": [
    {
          "classifiers": [
            {
              "classifier_id": "food",
              "name": "food",
              "classes": [
                {
                  "class": "apple",
                  "score": 0.572,
                  "type_hierarchy": "/fruit/accessory fruit/apple"
                },
                {
                  "class": "accessory fruit",
                  "score": 0.572
                },
                {
                  "class": "fruit",
                  "score": 0.805
                },
                {
                  "class": "banana",
                  "score": 0.5,
                  "type_hierarchy": "/fruit/banana"
                }
              ]
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 0
    }
    ```

## Schritt 3: Gesichter in einem Bild erkennen
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} kann in Bildern Gesichter erkennen.

1.  Geben Sie folgenden Aufruf an die Methode `Detect faces in an image` (Gesichter in einem Bild erkennen) aus, um ein [Bild von Ginni Rometty ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} zu analysieren. <span class="hide-dashboard">Ersetzen Sie `{apikey}` durch die zuvor kopierten Serviceberechtigungsnachweise.</span>

    ```bash
    curl -u "apikey:{apikey}"{: apikey} "https://gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg&version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json"
      "fmt"
      "github.com/watson-developer-cloud/go-sdk/core"
      "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr := visualrecognitionv3.
      NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{
        Version:   "2018-03-19",
        IAMApiKey: "{apikey}"{: apikey},
      })
    if visualRecognitionErr != nil {
      panic(visualRecognitionErr)
    }

    response, responseErr := visualRecognition.DetectFaces(
      &visualrecognitionv3.DetectFacesOptions{
        URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"),
      },
    )
    if responseErr != nil {
      panic(responseErr)
    }
    result := visualRecognition.GetClassifyResult(response)
    b, _ := json.MarshalIndent(result, "", "  ")
    fmt.Println(string(b))
    ```
    {: go}
    {: codeblock}

    ```java
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
      version: '2018-03-19',
      iam_apikey: '{apikey}'{: apikey}
    });

    VisualRecognition visualRecognition = new VisualRecognition("2018-03-19", options);

    DetectFacesOptions detectFacesOptions = new DetectFacesOptions.Builder()
      .url("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg");
      .build();
    DetectedFaces result = visualRecognition.detectFaces(detectFacesOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3({
          version: '2018-03-19',
          iam_apikey: '{apikey}'{: apikey}
        });

    var params = {
      url: 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg'
    };

    visualRecognition.detectFaces(params, function(err, response) {
      if (err)
        console.log(err);
      else
        console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json
    from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3(
        '2018-03-19',
        iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg'

    faces = visual_recognition.detect_faces(url).get_result()
    print(json.dumps(faces, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
      require "json"
      require "ibm_watson/visual_recognition_v3"
      include IBMWatson

      visual_recognition = VisualRecognitionV3.new(
        version: "2018-03-19",
        iam_apikey: "{apikey}"{: apikey}
      )
      url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"

      faces = visual_recognition.detect_faces(url)
      puts JSON.pretty_generate(faces.result)
      end
      ```
    {: ruby}
    {: codeblock}

    Die Antwort gibt die Position des Gesichts im Bild sowie den geschätzten Altersbereich und das Geschlecht für jedes Gesicht an.

    ```json
    {
      "images": [
    {
          "faces": [
            {
              "age": {
                "min": 50,
                "max": 53,
                "score": 0.8261783
              },
              "face_location": {
                "height": 744,
                "width": 606,
                "left": 460,
                "top": 373
              },
              "gender": {
                "gender": "FEMALE",
                "gender_label": "female",
                "score": 0.9999988
              }
            }
          ],
          "source_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg",
          "resolved_url": "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Nächste Schritte

Sie haben nun ein grundlegendes Verständnis davon, wie integrierte Klassifikationsmerkmale mit {{site.data.keyword.visualrecognitionshort}} verwendet werden. Weitergehende Informationen finden Sie hier:

- Probieren Sie diese Aufrufe mit Ihren eigenen Bildern aus. Zu beachten ist nur, dass die Bildgröße unter 10 MB bleiben muss.
- Erfahren Sie mehr über die Vorgehseweise zum [Erstellen eines angepassten Modells](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- {: curl} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition){: new_window}.
- {: go} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window}.
- {: java} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window}.
- {: javascript} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window}.
- {: python} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window}.
- {: ruby} Informationen zur API finden Sie in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window}.

### Bildnachweis
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window} von [Darklanlan ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window}, verwendet unter [CC BY 4.0 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
- [Fruchtkorb ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://flic.kr/p/JPHES){: new_window} von Flikr-Benutzer [Ryan Edwards-Crewe ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.flickr.com/photos/ryanec/){: new_window}, verwendet unter der [Creative Commons Attribution 2.0-Lizenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
- [Ginni Rometty auf dem Fortune MPW Summit 2011 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} by Asa Mathat / Fortune Live Media used under [CC BY 2.0 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
