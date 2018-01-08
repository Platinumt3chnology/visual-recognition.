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

# Reconhecendo texto em uma imagem

{: shortdesc}

## Antes de Começar
{: #copy-credentials}

Use as credenciais que você copiou no "Tutorial de introdução" para este tutorial. Se você não criou uma instância de serviço, execute essas etapas na seção [Antes de começar](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Etapa 1: reconhecer texto em uma imagem
{: #recognize-text}

1.  Faça download da imagem de exemplo do <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download=""> de amostra...<img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externon" class="style-scope doc-content"></a>
1.  Emita o comando a seguir para o método `POST /v3/recognize_text` para fazer upload e analisar a imagem. Se você usar sua própria imagem, o tamanho máximo será de 2 MB:
    - Substitua `{api-key}` por essas credenciais de serviço que você copiou anteriormente.
    - Modifique o local do images\_file para apontar o local no qual você salvou a imagem.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \ "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    A resposta inclui uma hierarquia de local, de estimativa de idade, de gênero, de identidade e de tipo (se o serviço reconhece essa face) e uma pontuação para cada.

    Amplitude de pontuação de 0 a 1, com uma pontuação mais alta indicando maior correlação. Todas as faces são detectadas, mas para imagens com mais de 10 faces, pontuações de confiança de idade e de gênero podem retornar pontuações de 0.


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

## Próximas etapas

Você tem um entendimento básico de como usar os classificadores padrão com o {{site.data.keyword.visualrecognitionshort}}. Agora vá além:

- Leia sobre a API na [Referência de API![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

Todas as imagens usadas nesta página são do Flikr e usadas sob [licença do Creative Commons Attribution 2.0![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessas imagens.
