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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Tutoriel d'initiation

Ce tutoriel vous explique comment utiliser certains discriminants intégrés dans {{site.data.keyword.visualrecognitionfull}} pour classifier une image et y détecter des visages.
{: shortdesc}

## Avant de commencer
{: #prerequisites}

- Créez une instance du service :
    - {: download} Si vous lisez ceci, vous avez créé votre instance de service. Il vous faut maintenant obtenir vos données d'identification.
    - Créez un projet depuis un service :
        1.  Rejoignez la page {{site.data.keyword.watson}} Developer Console [Services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Sélectionnez {{site.data.keyword.visualrecognitionshort}}, cliquez sur **Add Services** et inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
        1.  Entrez `vision-tutorial` comme nom de projet et cliquez sur **Create Project**.
- Copiez les données d'identification pour vous authentifier à votre instance de service :
    - {: download} Depuis le tableau de bord de service (que vous avez sous les yeux) :
        1.  Cliquez sur l'onglet **Service credentials**.
        1.  Cliquez sur **View credentials** sous **Actions**.
        1.  Copiez la valeur api-key.
        {: download}
    - A partir de votre projet **vision-tutorial** dans Developer Console, copiez la valeur `api-key` pour `"visual_recognition"` depuis la section **Credentials**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si vous utilisez {{site.data.keyword.Bluemix_dedicated_notm}}, créez votre instance de service depuis la page [{{site.data.keyword.visualrecognitionshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} du catalogue. Pour plus de détails sur la façon de trouver vos données d'identification de service, voir [Service credentials for Watson services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etape 1 : classifier une image
{: #classify}

1.  Téléchargez l'image exemple <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Emettez la commande ci-après pour télécharger l'image et la classifier par rapport à tous les discriminants intégrés :
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées précédemment.
    - Modifiez l'emplacement d'images\_file pour pointer sur l'endroit où vous avez sauvegardé l'image.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Si vous avez {{site.data.keyword.Bluemix_notm}} Dedicated, le noeud final `gateway-a.watsonplatform.net` ici peut ne pas être votre noeud final de service. Vérifiez l'`url` sur la page **Service credentials** de votre tableau de bord de service.{: tip}

    La réponse inclut le discriminant ou modèle General (qui utilise l'ID classifier_id `default`), les classes identifiées dans l'image et un score pour chaque classe.

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
        {
              "classes": [
            {
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
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    Les scores de confiance sont compris entre 0 à 1 ; plus le score est élevé, plus la corrélation est grande. Par défaut, les appels `/v3/classify` n'incluent pas les classes dont le score est inférieur à `0.5`.

## Etape 2 : détecter des visages dans une image
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} peut détecter la présence de visages dans les images. La réponse fournit des informations comme l'emplacement du visage sur l'image, ainsi qu'une estimation de la plage d'âge et du sexe de chaque personne dont le visage est représenté.

Le service est aussi capable d'identifier par leur nom de nombreuses célébrités et de fournir une base *knowledge graph* qui vous permet d'agréger des concepts de niveau supérieur.

1.  Téléchargez l'image exemple <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Emettez la commande suivante dans la méthode `POST /v3/detect_faces` pour télécharger et analyser l'image. Si vous utilisez votre propre image, la taille maximale est 2 Mo :
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées précédemment.
    - Modifiez l'emplacement d'images\_file pour pointer sur l'endroit où vous avez sauvegardé l'image.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    La réponse inclut un emplacement, une estimation de l'âge et du sexe de la personne visible, son identité et la hiérarchie de type (si le service reconnaît ce visage), et un score pour chacun de ces éléments.

    Les scores sont compris entre 0 et 1 ; plus le score est élevé, plus la corrélation est grande. Tous les visages sont détectés mais pour des images comportant plus de 10 visages, les scores de confiance d'âge et de sexe risquent de retourner la valeur 0.

    ```json
    {
      "images": [
    {
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
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Etapes suivantes

Vous savez maintenant comment utiliser le discriminant default intégré avec {{site.data.keyword.visualrecognitionshort}}. A
présent, approfondissez vos connaissances :

- Apprenez maintenant à [générer un discriminant personnalisé](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Informez-vous sur l'API en consultant [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

- [Corbeille de fruits ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://flic.kr/p/JPHES){: new_window}, photo prise par l'utilisateur Flikr [Ryan Edwards-Crewe ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.flickr.com/photos/ryanec/){: new_window}, utilisée sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0)![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à cette image.
- [Obama ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://bit.ly/1T0DCl9){: new_window}, photo prise par l'utilisateur Flikr [dcblog ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.flickr.com/photos/12863058@N08/){: new_window}, utilisée sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0)![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à cette image.
