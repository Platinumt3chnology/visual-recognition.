---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-17"

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

# Reconnaissance de texte dans une image
{: #tutorial-recognize-text}

Ce tutoriel vous guide tout au long de votre premier appel avec le modèle Text de la version bêta de {{site.data.keyword.visualrecognitionshort}} pour détecter et reconnaître du texte en anglais dans une image.
{: shortdesc}

Le modèle Text est une fonction bêta privée, et {{site.data.keyword.IBM_notm}} doit vous autoriser à envoyer des appels au modèle. [Demandez l'accès à ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Pour plus d'informations sur les fonctions bêta, voir les [Notes sur l'édition](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Avant de commencer
{: #tutorial-recognize-text-prerequisites}

1.  Accédez à la page [{{site.data.keyword.visualrecognitionshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/visual-recognition){: new_window} du catalogue {{site.data.keyword.Bluemix_notm}}.
    1.  Inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
    1.  Cliquez sur **Créer**.
- Copiez les données d'identification pour vous authentifier à votre instance de service :
    1.  Cliquez sur **Afficher** pour voir vos données d'identification.
    1.  Copiez la valeur de la **clé d'API**. 

## Etape 1 : Reconnaissance du texte dans une image
{: #tutorial-recognize-text-recognize-text}

1.  Emettez l'appel suivant pour reconnaître du texte dans [une image ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}. Remplacez `{your_api_key}` par la valeur de clé d'API copiée précédemment.

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    La réponse inclut le texte reconnu et les emplacements des mots dans le texte, avec une cote de confiance pour chaque mot. Les informations d'emplacement peuvent être utilisées pour tracer des encadrés englobants autour des mots. 

    ```json
    {
      "images": [
    {
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

## Etapes suivantes

Vous avez à présent une compréhension de base de la reconnaissance de texte dans une image. Allez plus loin.

- Lisez la [présentation](/docs/services/visual-recognition?topic=visual-recognition-recognize-text#recognize-text).
- Explorez les méthodes du modèle Text dans [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Attributions
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} par [Lubo Minar ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://unsplash.com/@bubo){: new_window} sur [Unsplash ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}. Aucune modification n'a été apportée à cette image.
