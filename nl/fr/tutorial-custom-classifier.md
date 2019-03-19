---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Création d'un modèle personnalisé
{: #tutorial-custom-classifier}

Après avoir analysé une image dans le tutoriel d'initiation, vous êtes prêt à entraîner et créer un modèle personnalisé. Avec un modèle personnalisé, vous pouvez entraîner le service {{site.data.keyword.visualrecognitionshort}} à classifier des images afin de répondre à vos besoins.
{: shortdesc}

## Etape 1 : Copie de vos données d'identification
{: #copy-credentials}

Utilisez les données d'identification que vous avez copiées dans le tutoriel d'initiation. Si vous n'avez pas créé d'instance de service, effectuez la procédure de la section [Avant de commencer](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites).

## Etape 2 : Création d'un modèle personnalisé
{: #create}

{{site.data.keyword.visualrecognitionshort}} peut effectuer son apprentissage à partir d'images exemple téléchargées afin de créer un nouveau modèle multi-facettes. Chaque fichier exemple est formé par rapport aux autres fichiers de cet appel, et les exemples positifs sont stockés sous forme de classes. Ces classes sont regroupées afin de définir un modèle unique et renvoyer leurs propres scores. Les fichiers exemple négatifs ne sont pas stockés en tant que classes.

1.  Téléchargez les fichiers d'apprentissage exemple suivants : <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a> et <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>.
1.  Appelez la méthode `POST /v3/classifiers` à l'aide de la commande ci-après, qui télécharge les données d'apprentissage et crée un modèle personnalisé `dogs` :
    - Remplacez `{your_api_key}` par les données d'identification du service que vous avez copiées à la première étape.
    - Modifiez l'emplacement de `{class}_positive_examples` pour pointer sur l'endroit où vous avez sauvegardé les fichiers .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    Les noms des fichiers exemple positifs requièrent le suffixe `_positive_examples`. Dans cet exemple, les noms de fichiers sont `beagle_positive_examples`, `goldenretriever_positive_examples` et `husky_positive_examples`. Le préfixe (beagle, goldenretriever et husky) est retourné en tant que nom de classe.
    {:tip }

    La réponse inclut un nouvel ID de discriminant et statut, par exemple :

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
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
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  Vérifiez périodiquement le statut d'apprentissage jusqu'à voir un statut `ready`. L'apprentissage commence immédiatement et doit être terminé pour que vous puissiez interroger le modèle. Remplacez `{your_api_key}` et `{classifier_id}` par vos informations :

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Etape 3 : Mise à jour d'un modèle personnalisé existant
{: #tutorial-custom-classifier-update}

Vous pouvez mettre à jour un modèle personnalisé soit en ajoutant des classes au modèle, soit en ajoutant des images à une classe existante. Ici, vous améliorez le modèle créé à l'étape 2 en ajoutant une classe *Dalmatian* aux types de chiens qui peuvent être classifiés. Vous pouvez également ajouter des images de chats à l'ensemble exemple négatif pour le modèle personnalisé "chiens".

1.  Téléchargez les fichiers d'apprentissage exemple suivants : <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a> et <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>.
1.  Appelez la méthode `POST /v3/classifiers/{classifier_id}` avec la commande cURL ci-après, qui télécharge les données d'apprentissage et met à jour le modèle personnalisé "dogs\_1941945966" :
    - Remplacez `{your_api_key}` par les données d'identification du service que vous avez copiées à la première étape.
    - Remplacez `{classifier_id}` par l'ID du modèle personnalisé à mettre à jour.
    - Modifiez l'emplacement de `{class}_positive_examples` pour pointer sur l'endroit où vous avez sauvegardé les fichiers .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    Le modèle personnalisé existant "dogs" est remplacé par le modèle ayant fait l'objet d'un réapprentissage avec le même ID classifier_id. La réponse répertorie le nouvel ensemble de classe et le statut actuel. Exemple :

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    L'apprentissage commence immédiatement. Quand le nouvel ensemble est disponible, le statut passe à `ready`.

    N'émettez pas une autre demande de réapprentissage avant que l'état du statut actuel ne soit à `ready`. Plusieurs demandes de réapprentissage d'un modèle n'aboutissent qu'à l'exécution d'un seul réapprentissage. Un horodatage appelé `updated` indique la date et l'heure auxquelles le modèle a été mis à jour le plus récemment. Si vous appelez la méthode `/classify` alors que le modèle est en réapprentissage, l'ancienne définition du modèle est utilisée.{: tip}
1.  Vérifiez périodiquement le statut d'apprentissage jusqu'à voir un statut `ready`. Remplacez `{your_api_key}` et `{classifier_id}` par vos informations :

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Etape 4 : Classification d'une image avec un modèle personnalisé
{: #tutorial-custom-classifier-classify}

Quand le nouveau modèle est prêt, appelez-le pour voir comment il se comporte.

1.  Téléchargez le fichier <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>.
1.  Utilisez la méthode `POST /v3/classify` pour tester votre modèle personnalisé. L'exemple suivant classifie l'image `dogs.jpg` en fonction du modèle personnalisé "dogs\_1941945966" et du modèle General `default` intégré :
    - Remplacez `{your_api_key}` par les données d'identification du service que vous avez copiées à la première étape.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    Pour une classification uniquement par rapport au modèle General intégré, omettez le paramètre `classifier_ids`.
    {: tip}

    La réponse inclut les discriminants (modèles), leurs classes et un score pour chaque classe. Les scores sont compris entre 0 et 1 ; plus le score est élevé, plus la corrélation est grande. Les appels `/v3/classify` omettent les classes à scores bas par défaut si des classes à scores élevés sont identifiées. Vous pouvez définir un score minimum à afficher en spécifiant une valeur en virgule flottante pour le paramètre `threshold` de votre appel.

    ```json
    {
      "images": [
    {
          "classifiers": [
        {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  Examinez vos résultats.

Vous avez terminé. Vous avez créé, entraîné et interrogé un modèle personnalisé avec {{site.data.keyword.visualrecognitionshort}}.

### Suppression de votre modèle personnalisé
{: #tutorial-custom-classifier-delete}

Vous pouvez vouloir supprimer votre modèle personnalisé pour commencer à développer votre application avec une instance propre.

Pour supprimer le modèle, appelez la méthode `DELETE /v3/classifiers/{classifier_id}`. Remplacez `{your_api_key)` et`classifier_id` par vos propres informations :

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## Etapes suivantes
{: #tutorial-custom-classifier-next-steps}

A présent que vous savez comment utiliser des modèles personnalisés, vous pouvez aller plus loin :

- Consultez la page [Best practices for custom classifiers in Watson Visual Recognition![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Informez-vous sur l'API en consultant la documentation de [référence sur l'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Attributions
{: #tutorial-custom-classifier-attributions}

Toutes les images utilisées sur cette page proviennent de Flikr et sont utilisées sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0)![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à ces images.
