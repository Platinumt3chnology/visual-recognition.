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

# Tutoriel d'initiation
{: #getting-started-tutorial}

Ce tutoriel vous guide tout au long de l'utilisation de différents modèles intégrés dans {{site.data.keyword.visualrecognitionfull}} pour classifier une image et y détecter des visages.
{: shortdesc}

Si vous préférez travailler dans une interface graphique, utilisez {{site.data.keyword.DSX}}. [Lancez l'outil ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} et suivez la [vidéo ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://youtu.be/898RN31szg0){: new_window}.
{: tip}

## Avant de commencer
{: #prerequisites}

- {: hide-dashboard} Créez une instance du service :
    1.  Accédez à la page [{{site.data.keyword.visualrecognitionshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/visual-recognition){: new_window} du catalogue.
    1.  Inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
    1.  Cliquez sur **Créer**.
- {: hide-dashboard} Copiez les données d'identification pour vous authentifier à votre instance de service :
    1.  Sur la page **Gérer**, cliquez sur **Afficher les données d'identification**.
    1.  Copiez la valeur de la `clé d'API`. 
- {: curl} Vérifiez que vous disposez bien de la commande `curl`.
    - Testez si `curl` est installé. Exécutez la commande suivante sur la ligne de commande. Si la sortie indique la version `curl` avec le support SSL, vous êtes prêt à commencer le tutoriel. 

        ```bash
        curl -V
        ```
        {: pre}

    - Si nécessaire, installez une version avec SSL activé depuis [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Ajoutez l'emplacement du fichier à vos variables d'environnement PATH si vous souhaitez exécuter `curl` depuis un emplacement de ligne de commande. 
- {:go} Installez le [SDK Go ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/go-sdk){: new_window}.

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} Installez le [SDK Java ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/java-sdk){: new_window}.
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
- {: javascript} Installez le [SDK Node ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/node-sdk){: new_window}.

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} Installez le [SDK Python ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/python-sdk){: new_window}.

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} Installez le [SDK Ruby ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}.

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## Etape 1 : Classification d'une image
{: #classify}

1.  Emettez l'appel suivant pour classifier [une image ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window}. <span class="hide-dashboard">Remplacez `{apikey}` par les données d'identification de service copiées précédemment.</span>

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

    La réponse inclut les classes identifiées dans l'image à partir du modèle General intégré (`"classifier_id": "default"`) et une cote de confiance pour chaque classe. Le score représente un pourcentage, et plus les valeurs sont élevées, plus la fiabilité est élevée. Par défaut, les réponses à des appels `Classify` n'incluent pas les classes avec un score inférieur à `0.5` (50 %).

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

## Etape 2 : Classification avec le modèle Food
{: #classify-food}

{{site.data.keyword.visualrecognitionshort}} inclut également un modèle Food intégré qui peut être plus précis pour vos images de nourriture. 

1.  Emettez un appel pour classifier une [image de nourriture ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} en fonction du modèle Food. <span class="hide-dashboard">Remplacez `{apikey}` par les données d'identification de service copiées précédemment.</span>

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

    Le service renvoie les résultats suivants. Vous pouvez voir que l'ID `classifier_id` est identifié en tant que `food`. Les classes identifiées par le service sont également différentes de la première réponse. 

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

## Etape 3 : Détection de visages dans une image
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} peut détecter la présence de visages dans les images.

1.  Emettez l'appel suivant de la méthode `Detect faces in an image` pour analyser une [image de Ginni Rometty ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}. <span class="hide-dashboard">Remplacez `{apikey}` par les données d'identification de service copiées précédemment.</span>

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

    La réponse indique l'emplacement du visage dans l'image, ainsi qu'une estimation de la plage d'âge et du sexe de chaque personne dont le visage est représenté.

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

## Etapes suivantes
{: #gs-next-steps}

Vous possédez une compréhension de base de l'utilisation de discriminants intégrés avec {{site.data.keyword.visualrecognitionshort}}. A présent, approfondissez vos connaissances :

- Essayez ces appels avec vos propres images. Veillez seulement à ce que la taille des images ne dépasse pas 10 Mo.
- Apprenez maintenant à [générer un modèle personnalisé](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- {: curl} Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition){: new_window}.
- {: go} Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window}.
- {: java} Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window}.
- {: javascript} Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window}.
- {: python} Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window}.
- {: ruby} Informez-vous sur l'API en consultant la documentation de [de référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window}.

### Attributions
{: #attributions}

- [IBM VGA 90X8941 on PS55.jpg ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window} par [Darklanlan ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window} utilisé sous [CC BY 4.0 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window}. Aucune modification n'a été apportée à cette image.
- [Corbeille de fruits ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://flic.kr/p/JPHES){: new_window}, photo prise par l'utilisateur Flikr [Ryan Edwards-Crewe ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.flickr.com/photos/ryanec/){: new_window}, utilisée sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0)![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à cette image.
- [Ginni Rometty at the Fortune MPW Summit in 2011 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} par Asa Mathat / Fortune Live Media utilisé sous [CC BY 2.0 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window}. Aucune modification n'a été apportée à cette image.
