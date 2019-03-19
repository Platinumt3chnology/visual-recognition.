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

# Tutorial de introdução

Este tutorial orienta sobre como usar alguns modelos integrados no {{site.data.keyword.visualrecognitionfull}} para classificar uma imagem e, em seguida, detectar faces em uma imagem.
{: shortdesc}

Se preferir trabalhar em uma interface gráfica, use o {{site.data.keyword.DSX}}. [Ative a ferramenta ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} e siga o [vídeo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://youtu.be/898RN31szg0){: new_window}.
{: tip}

## Antes de Começar
{: #prerequisites}

- {: hide-dashboard} Crie uma instância do serviço:
    1.  Acesse a página [{{site.data.keyword.visualrecognitionshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/visual-recognition){: new_window} no catálogo.
    1.  Inscreva-se para obter uma conta gratuita do {{site.data.keyword.Bluemix_notm}} ou efetue login.
    1.  Clique em  ** Criar **.
- {: hide-dashboard} Copie as credenciais para autenticar sua instância de serviço:
    1.  Na página **Gerenciar**, clique em **Mostrar credenciais**.
    1.  Copie o valor da  ` Chave API ` .
- {: curl}Certifique-se de ter o comando `curl`.
    - Teste se o  ` curl `  está instalado. Execute o comando a seguir na linha de comandos. Se a saída listar a versão `curl` com suporte SSL, você estará pronto para começar o tutorial.

        ```bash
        curl -V
        ```
        {: pre}

    - Se necessário, instale uma versão com SSL ativado por meio de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Inclua o local do arquivo nas variáveis de ambiente PATH se desejar executar `curl` de qualquer local da linha de comandos.
- {:go} Instale o [SDK do Go ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/go-sdk){: new_window}.

    ```go
    go get -u github.com/watson-developer-cloud/go-sdk/...
    ```
    {: go}
    {: pre}

- {: java} Instale o [SDK do Java ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/java-sdk){: new_window}.
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
- {: javascript} Instale o [SDK do Node ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/node-sdk){: new_window}.

    ```bash
    npm install --save watson-developer-cloud
    ```
    {:pre}
- {: python} Instale o [SDK do Python ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/python-sdk){: new_window}.

    ```bash
    pip install --upgrade watson-developer-cloud
    ```
    {:pre}
- {: ruby} Instale o [SDK do Ruby ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/ruby-sdk){: new_window}.

    ```bash
    gem install ibm_watson
    ```
    {:pre}


## Etapa 1: classificar uma imagem
{: #classify}

1.  Emita a chamada a seguir para classificar [uma imagem ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg){: new_window}. <span class="hide-dashboard">Substitua `{apikey}` pelas credenciais de serviço que você copiou anteriormente.</span>

    ```bash
    curl -u "apikey: {"{: apikey} "https: //gateway.watsonplatform.net/visual-recognition/api/v3/classify?url=http=cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg & version=2018-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json" "fmt" "github.com/watson-developer-cloud/go-sdk/core" "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr: = visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{ Version: "2018-03-19", IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr! = nil {
        Pânico (visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"),
        },
      )
      if responseErr! = nil {
        panic(responseErr) }
      result := visualRecognition.GetClassifyResult(response) b, _ := json.MarshalIndent(result, "", " ")
      fmt.Println (string (b))
    ```
    {: go}
    {: codeblock}

    ```java
    Opções de IamOptions = new IamOptions.Builder ()
      .apiKey ("{"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition ("2018-03-19", options);

    ClassifyOptions ClassifyOptions = new ClassifyOptions.Builder ()
      .url("https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg")
      .build(); ClassifiedImages result = visualRecognition.classify(classifyOptions).execute(); System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require('watson-developer-cloud/visual-recognition/v3');
    var fs = require('fs');

    var visualRecognition = new VisualRecognitionV3 ({
      version: '2018-03-19', iam_apikey: '{apikey}'{: apikey}
    });

    var url= 'https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg';

    var params = {
      url: url,
    };

    visualRecognition.classify (params, function (err, response) {
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
    import json from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3( '2018-03-19', iam_apikey='{apikey}'{: apikey})

    url = 'https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg '

    classes_result = visual_recognition.classify(url=url).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json" require "ibm_watson/visual_recognition_v3" include IBMWatson

    visual_recognition = VisualRecognitionV3.new( version: "2018-03-19", iam_apikey: "{apikey}"{: apikey}
    )
    url= "https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"

    classes = visual_recognition.classify(url)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    A resposta inclui as classes identificadas na imagem do modelo General integrado (`"classifier_id": "default"`) e uma pontuação de confiança para cada classe. A pontuação representa uma porcentagem e os valores mais altos representam confianças mais altas. Por padrão, as respostas das chamadas `Classify` não incluem classes com uma pontuação abaixo de `0.5` (50%).

    ```json
    {
      "images": [ {
          "classifiers": [ {
              "classifier_id": "default", "name": "default", "classes": [ {
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

## Etapa 2: Classificar com o modelo Food
{: #classify-food}

O {{site.data.keyword.visualrecognitionshort}} também inclui um modelo Food integrado que pode ser mais preciso para suas imagens com itens alimentícios.

1.  Emita uma chamada para classificar uma [imagem de comida ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg){: new_window} com relação ao modelo Food. <span class="hide-dashboard">Substitua `{apikey}` pelas credenciais de serviço que você copiou anteriormente.</span>

    ```bash
    curl -u "apikey: {"{: apikey} -F "classifier_ids = food" "https: //gateway.watsonplatform.net/visual-recognition/api/v3/classify?https://watson-developer-cloud.github.io/doc-tutorial-tutorial-downloads/visual-downbowl.jpg & version=2018-03-19-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json" "fmt" "github.com/watson-developer-cloud/go-sdk/core" "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr: = visualrecognitionv3.
        NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{ Version: "2018-03-19", IAMApiKey: "{apikey}"{: apikey},
        })
      if visualRecognitionErr! = nil {
        Pânico (visualRecognitionErr)
      }

      response, responseErr := visualRecognition.Classify(
        &visualrecognitionv3.ClassifyOptions{
          URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg"),
          ClassifierIds: []string{"food"},
        },
      )
      if responseErr! = nil {
        panic(responseErr) }
      result := visualRecognition.GetClassifyResult(response) b, _ := json.MarshalIndent(result, "", " ")
      fmt.Println (string (b))
    ```
    {: go}
    {: codeblock}

    ```java
    Opções de IamOptions = new IamOptions.Builder ()
      .apiKey ("{"{: apikey})
      .build();

    VisualRecognition visualRecognition = new VisualRecognition ("2018-03-19", options);

    ClassifyOptions ClassifyOptions = new ClassifyOptions.Builder ()
      .url( " https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/thubowl.jpg");
      .classifierIds(Arrays.asList("food"))
      .build(); ClassifiedImages result = visualRecognition.classify(classifyOptions).execute(); System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require ('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3 ({
      version: '2018-03-19', iam_apikey: '{apikey}'{: apikey}
    });

    var url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg';
    var classifier_ids = ["food"];

    var params = {
      url: url,
      classifier_ids: classifier_ids
    };

    visualRecognition.classify (params, function (err, response) {
      if (err) console.log(err); else console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3( '2018-03-19', iam_apikey='{apikey}'{: apikey})

    url = 'https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg'
    classifier_ids = ["food"]

    classes_result = visual_recognition.classify(url=url, classifier_ids=classifier_ids).get_result()
    print(json.dumps(classes_result, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
    require "json" require "ibm_watson/visual_recognition_v3" include IBMWatson

    visual_recognition = VisualRecognitionV3.new( version: "2018-03-19", iam_apikey: "{apikey}"{: apikey}
    )
    url= "https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/640px-IBM_VGA_90X8941_on_PS55.jpg"
    classifier_ids= ["food"]

    classes = visual_recognition.classify(url, classifier_ids)
    puts JSON.pretty_generate(classes.result)
    end
    ```
    {: ruby}
    {: codeblock}

    O serviço retorna os resultados a seguir. É possível ver que o `classifier_id` está identificado como `food`. As classes que o serviço identificou também são diferentes da primeira resposta.

    ```json
    {
      "images": [ {
          "classifiers": [ {
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

## Etapa 3: Detectar faces em uma imagem
{: #detect-faces}

O {{site.data.keyword.visualrecognitionshort}} pode detectar faces em imagens.

1.  Emita a chamada a seguir para o método `Detect faces in an image` para analisar uma [imagem de Ginni Rometty ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window}. <span class="hide-dashboard">Substitua `{apikey}` pelas credenciais de serviço que você copiou anteriormente.</span>

    ```bash
    curl -u "apikey: {"{: apikey} "https: //gateway.watsonplatform.net/visual-recognition/api/v3/detect_faces?url=http=cloud.github.io/doc-tutorial-downloads/visual-downloads/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg & version=2018-03-03-03-19"
    ```
    {: pre}
    {: curl}

    ```go
    import (
      "encoding/json" "fmt" "github.com/watson-developer-cloud/go-sdk/core" "github.com/watson-developer-cloud/go-sdk/visualrecognitionv3"
    )

    visualRecognition, visualRecognitionErr: = visualrecognitionv3.
      NewVisualRecognitionV3(&visualrecognitionv3.VisualRecognitionV3Options{ Version: "2018-03-19", IAMApiKey: "{apikey}"{: apikey},
      })
    if visualRecognitionErr! = nil {
      Pânico (visualRecognitionErr)
    }

    response, responseErr := visualRecognition.DetectFaces(
      &visualrecognitionv3.DetectFacesOptions{
        URL: core.StringPtr("https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"),
      },
    )
    if responseErr! = nil {
      panic(responseErr) }
    result := visualRecognition.GetClassifyResult(response) b, _ := json.MarshalIndent(result, "", " ")
    fmt.Println (string (b))
    ```
    {: go}
    {: codeblock}

    ```java
    var VisualRecognitionV3 = require ('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3 ({
      version: '2018-03-19', iam_apikey: '{apikey}'{: apikey}
    });

    VisualRecognition visualRecognition = new VisualRecognition ("2018-03-19", options);

    DetectFacesOpções detectFacesOptions = new DetectFacesOptions.Builder ()
      .url( " https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg");
      .build();
    DetectedFaces result = visualRecognition.detectFaces(detectFacesOptions).execute();
    System.out.println(result);
    ```
    {: java}
    {: codeblock}

    ```javascript
    var VisualRecognitionV3 = require ('watson-developer-cloud/visual-recognition/v3');

    var visualRecognition = new VisualRecognitionV3 ({
          version: '2018-03-19', iam_apikey: '{apikey}'{: apikey}
        });

    var params = {
      url: 'https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg '
    };

    visualRecognition.detectFaces (params, function (err, response) {
      if (err) console.log(err); else console.log(JSON.stringify(response, null, 2))
    });
    ```
    {: javascript}
    {: codeblock}

    ```python
    import json from watson_developer_cloud import VisualRecognitionV3

    visual_recognition = VisualRecognitionV3( '2018-03-19', iam_apikey='{apikey}'{: apikey})

    url = 'https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg '

    faces = visual_recognition.detect_faces(url).get_result()
    print(json.dumps(faces, indent=2))
    ```
    {: python}
    {: codeblock}

    ```ruby
      require "json" require "ibm_watson/visual_recognition_v3" include IBMWatson

      visual_recognition = VisualRecognitionV3.new( version: "2018-03-19", iam_apikey: "{apikey}"{: apikey}
      )
      url= "https: //watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg"

      faces = visual_recognition.detect_faces(url)
      puts JSON.pretty_generate(faces.result)
      end
      ```
    {: ruby}
    {: codeblock}

    A resposta fornece o local da face na imagem, a faixa etária estimada e o sexo de cada face.

    ```json
    {
      "images": [ {
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
      ], "images_processed": 1 }
    ```
    {: codeblock}

## Próximas Etapas

Você tem um entendimento básico de como usar classificadores integrados com o {{site.data.keyword.visualrecognitionshort}}. Agora vá além:

- Tente essas chamadas com suas próprias imagens. Basta manter o tamanho da imagem abaixo de 10 MB.
- Saiba mais sobre como [construir um modelo customizado](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- {: curl} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition){: new_window}.
- {: go} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition?language=go){: new_window}.
- {: java} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition?language=java){: new_window}.
- {: javascript} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition?language=node){: new_window}.
- {: python} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition?language=python){: new_window}.
- {: ruby} Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition?language=ruby){: new_window}.

### Atribuições
{: #attributions}

- [IBM VGA 90X8941 em PS55.jpg ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://commons.wikimedia.org/wiki/File:IBM_VGA_90X8941_on_PS55.jpg){: new_window} por [Darklanlan ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://commons.wikimedia.org/wiki/User:Darklanlan){: new_window} usada em [CC BY 4.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://creativecommons.org/licenses/by/4.0/legalcode "Creative Commons Attribution 4.0"){: new_window}. Nenhuma mudança foi feita nessa imagem.
- [Cesta de frutas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://flic.kr/p/JPHES){: new_window} pelo usuário do Flikr [Ryan Edwards-Crewe ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.flickr.com/photos/ryanec/){: new_window} usada sob [licença do Creative Commons Attribution 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessa imagem.
- [Ginni Rometty na Fortune MPW Summit em 2011 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://commons.wikimedia.org/wiki/File:Ginni_Rometty_at_the_Fortune_MPW_Summit_in_2011.jpg){: new_window} por Asa Mathat/Fortune Live Media usada em [CC BY 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://creativecommons.org/licenses/by/2.0/legalcode){: new_window}. Nenhuma mudança foi feita nessa imagem.
