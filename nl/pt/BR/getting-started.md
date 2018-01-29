---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-29"

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

# Tutorial de introdução

Este tutorial o orienta como usar alguns classificadores integrados no {{site.data.keyword.visualrecognitionfull}} para classificar uma imagem e, em seguida, detectar faces em uma imagem.
{: shortdesc}

## Antes de Começar
{: #prerequisites}

- Crie uma instância do serviço:
    - {: download} Se você está vendo isto, sua instância de serviço foi criada. Agora, obtenha suas credenciais.
    - Crie um projeto por meio de um serviço:
        1.  Acesse a página Serviços do {{site.data.keyword.watson}} Developer Console[ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Selecione {{site.data.keyword.visualrecognitionshort}}, clique em **Incluir serviços** e se inscreva em uma conta grátis do {{site.data.keyword.Bluemix_notm}} ou efetue login.
        1.  Digite `vision-tutorial` como o nome do projeto e clique em **Criar projeto**.
- Copie as credenciais para autenticar sua instância de serviço:
    - {: download} No painel de serviço (que você está olhando):
        1.  Clique na guia **Credenciais de serviço**.
        1.  Clique em **Visualizar credenciais** em **Ações**.
        1.  Copie o valor api-key.
        {: download}
    - Em seu projeto **vision-tutorial** no Developer Console, copie o valor `api-key` para `"visual_recognition"` da seção **Credenciais**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se você usa o {{site.data.keyword.Bluemix_dedicated_notm}}, crie sua instância de serviço na página [{{site.data.keyword.visualrecognitionshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} no Catálogo. Para obter detalhes sobre como localizar suas credenciais de serviço, veja [Credenciais de serviço para serviços do Watson![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etapa 1: classificar uma imagem
{: #classify}

1.  Faça download da imagem de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Emita o comando a seguir para fazer upload da imagem e classificá-la com relação a todos os classificadores integrados:
    - Substitua `{api-key}` por essas credenciais de serviço que você copiou anteriormente.
    - Modifique o local do images\_file para apontar o local no qual você salvou a imagem.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Se você tiver o {{site.data.keyword.Bluemix_notm}} Dedicated, o terminal `gateway-a.watsonplatform.net` aqui poderá não ser seu terminal em serviço. Verifique a `url` na página **Credenciais de serviço** de seu painel de serviço.
    {: tip}

    A resposta inclui o modelo ou classificador Geral (que usa o classifier_id `default`), as classes identificadas na imagem e uma pontuação para cada classe.

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [ {
              "classes": [ {
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
      ], "images_processed": 1 }
    ```
    {: codeblock}

    As pontuações de confiança estão no intervalo de 0 a 1, com uma pontuação superior indicando maior correlação. Por padrão, as chamadas `/v3/classify` não incluem classes com uma pontuação abaixo de `0.5`.

## Etapa 2: detectar faces em uma imagem
{: #detect-faces}

O {{site.data.keyword.visualrecognitionshort}} pode detectar faces em imagens. A resposta fornece informações como o local da face na imagem e a faixa de idade estimada e o sexo para cada face.

O serviço também pode identificar várias celebridades por nome e pode fornecer um *gráfico de conhecimento* para que seja possível agregar os conceitos de nível superior.

1.  Faça download da imagem de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Emita o comando a seguir para o método `POST /v3/detect_faces` para fazer upload e analisar a imagem. Se você usar sua própria imagem, o tamanho máximo será de 2 MB:
    - Substitua `{api-key}` por essas credenciais de serviço que você copiou anteriormente.
    - Modifique o local do images\_file para apontar o local no qual você salvou a imagem.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \ "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    A resposta inclui uma hierarquia de local, de estimativa de idade, de gênero, de identidade e de tipo (se o serviço reconhece essa face) e uma pontuação para cada.

    Amplitude de pontuação de 0 a 1, com uma pontuação mais alta indicando maior correlação. Todas as faces são detectadas, mas para imagens com mais de 10 faces, pontuações de confiança de idade e de gênero podem retornar pontuações de 0.

    ```json
    {
      "images": [ {
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
      ], "images_processed": 1 }
    ```
    {: codeblock}

## Próximas Etapas

Você tem um entendimento básico de como usar o classificador padrão integrado com o {{site.data.keyword.visualrecognitionshort}}. Agora vá além:

- Saiba mais sobre como [construir um classificador customizado](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Atribuições
{: #attributions}

- [Cesta de frutas ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://flic.kr/p/JPHES){: new_window} pelo usuário do Flikr [Ryan Edwards-Crewe ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.flickr.com/photos/ryanec/){: new_window} usada sob [licença do Creative Commons Attribution 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessa imagem.
- [obama ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://bit.ly/1T0DCl9){: new_window} pelo usuário do Flikr [dcblog ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.flickr.com/photos/12863058@N08/){: new_window} usado sob [licença do Creative Commons Attribution 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessa imagem.
