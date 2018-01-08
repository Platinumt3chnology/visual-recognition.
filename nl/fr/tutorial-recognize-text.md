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

# Reconnaissance de texte dans une image

{: shortdesc}

## Avant de commencer
{: #copy-credentials}

Utilisez les données d'identification que vous avez copiées dans le tutoriel d'initiation pour ce tutoriel. Si vous n'avez pas créé d'instance de service, effectuez la procédure de la section [Avant de commencer](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Etape 1 : reconnaître du texte dans une image
{: #recognize-text}

1.  Téléchargez l'image exemple <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>
1.  Emettez la commande suivante dans la méthode `POST /v3/recognize_text` pour télécharger et analyser l'image. Si vous utilisez votre propre image, la taille maximale est 2 Mo :
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées précédemment.
    - Modifiez l'emplacement d'images\_file pour pointer sur l'endroit où vous avez sauvegardé l'image.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    La réponse inclut un emplacement, une estimation de l'âge et du sexe de la personne visible, son identité et la hiérarchie de type (si le service reconnaît ce visage), et un score pour chacun de ces éléments.

    Les scores sont compris entre 0 et 1 ; plus le score est élevé, plus la corrélation est grande. Tous les visages sont détectés mais pour des images comportant plus de 10 visages, les scores de confiance d'âge et de sexe risquent de retourner la valeur 0.


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

## Etapes suivantes

Vous savez maintenant comment utiliser les discriminants default intégrés avec {{site.data.keyword.visualrecognitionshort}}. A
présent, approfondissez vos connaissances :

- Informez-vous sur l'API en consultant [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

Toutes les images utilisées sur cette page proviennent de Flikr et sont utilisées sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0) ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à ces images.
