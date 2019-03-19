---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Reconhecendo texto em uma imagem
{: #tutorial-recognize-text}

Este tutorial orienta sobre como fazer sua primeira chamada com o modelo Text beta do {{site.data.keyword.visualrecognitionshort}} para detectar e reconhecer texto em inglês em uma imagem.
{: shortdesc}

O modelo de Texto é um recurso beta privado e deve-se ter permissão do {{site.data.keyword.IBM_notm}} para fazer chamadas para o modelo. [Solicitar acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Para obter mais informações sobre recursos beta, consulte as [Notas sobre a liberação](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Antes de Começar
{: #tutorial-recognize-text-prerequisites}

1.  Acesse a página [{{site.data.keyword.visualrecognitionshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/visual-recognition){: new_window} no {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Inscreva-se para obter uma conta gratuita do {{site.data.keyword.Bluemix_notm}} ou efetue login.
    1.  Clique em  ** Criar **.
- Copie as credenciais para autenticar sua instância de serviço:
    1.  Clique em  ** Mostrar **  para visualizar suas credenciais.
    1.  Copie o valor da  ** chave API ** .

## Etapa 1: reconhecer texto em uma imagem
{: #tutorial-recognize-text-recognize-text}

1.  Emita a chamada a seguir para reconhecer texto em [uma imagem ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}. Substitua `{your_api_key}` pelo valor da chave de API copiado anteriormente.

    ```bash
    curl -u "apikey: {"{: apikey} \
    "https: //gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-downloads/visual-recognition/lookButDontTouch.jpg & version=2018-03-03-19"
    ```
    {: pre}

    A resposta inclui o texto reconhecido e as localizações de palavras no texto com uma pontuação de confiança para cada palavra. As informações de local podem ser usadas para desenhar caixas delimitadoras ao redor das palavras.

    ```json
    {
      "images": [ {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Próximos passos

Você tem um entendimento básico de como reconhecer texto em uma imagem. Explore ainda mais.

- Leia a  [ visão geral ](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-).
- Explore os métodos do modelo Text na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Atribuições
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} por [Lubo Minar ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://unsplash.com/@bubo){: new_window} no [Unsplash ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}. Nenhuma mudança foi feita nessa imagem.
