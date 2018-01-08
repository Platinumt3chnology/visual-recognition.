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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Création d'un discriminant personnalisé

Après avoir classifié une image dans le tutoriel d'initiation, vous êtes prêt à entraîner et créer un discriminant personnalisé (ou un modèle). Avec un discriminant personnalisé, vous pouvez entraîner le service {{site.data.keyword.visualrecognitionshort}} afin qu'il classifie des images pour répondre à vos besoins.
{: shortdesc}

## Etape 1 : copie de vos données d'identification
{: #copy-credentials}

Utilisez les données d'identification que vous avez copiées dans le tutoriel d'initiation. Si vous n'avez pas créé d'instance de service, effectuez la procédure de la section [Avant de commencer](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Etape 2 : création d'un discriminant personnalisé
{: #create}

{{site.data.keyword.visualrecognitionshort}} peut effectuer son apprentissage depuis des images exemple que vous avez téléchargées pour créer un nouveau discriminant  multi-facettes. Chaque fichier exemple est formé par rapport aux autres fichiers de cet appel, et les exemples positifs sont stockés sous forme de classes. Ces classes sont groupées pour définir un discriminant unique et retourner leurs propres scores. Les fichiers exemple négatifs ne sont pas stockés en tant que classes.

1.  Téléchargez les fichiers d'apprentissage exemple suivants : <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> et <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Appelez la méthode `POST /v3/classifiers` avec la commande ci-après, qui télécharge les données d'apprentissage et crée un discriminant `dogs` :
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées à la première étape.
    - Modifiez l'emplacement de `{class}_positive_examples` pour pointer sur l'endroit où vous avez sauvegardé les fichiers .zip.

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Les noms des fichiers exemple positifs requièrent le suffixe `_positive_examples`. Dans cet exemple, les noms de fichiers sont `beagle_positive_examples`, `goldenretriever_positive_examples` et `husky_positive_examples`. Le préfixe (beagle, goldenretriever et husky) est retourné en tant que nom de classe.{:tip }

    La réponse inclut un nouvel ID de discriminant et statut, par exemple :

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
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
      ]
    }
    ```
    {: codeblock}

1.  Vérifiez périodiquement le statut d'apprentissage jusqu'à voir un statut `ready`. L'apprentissage commence immédiatement et doit être terminé pour que vous puissiez
interroger le discriminant. Remplacez `{api  key}` et `{classifier_id}` par vos propres informations :

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Etape 3 : mise à jour d'un discriminant personnalisé existant

Vous ne pouvez pas mettre à jour un discriminant personnalisé avec une clé d'API gratuite. Si vous avez une clé gratuite, vous pouvez procédez à une mise à niveau vers un plan standard. Pour plus de détails, voir [Changement de plan](https://console.bluemix.net/docs/pricing/changing_plan.html).
{: tip}

Vous pouvez mettre à jour un discriminant personnalisé soit en ajoutant des classes au discriminant, soit en ajoutant des images à une classe existante. Ici, vous améliorez le discriminant que vous avez créé à l'étape 2 en ajoutant une classe *Dalmatian* aux types de chiens qui peuvent être classifiés. Vous pouvez aussi ajouter des images de chats à l'ensemble exemple négatif pour le discriminant "chiens".

1.  Téléchargez les fichiers d'apprentissage exemple suivants : <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> et <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Appelez la méthode `POST /v3/classifiers/{classifier_id}` avec la commande cURL ci-après, qui télécharge les données d'apprentissage et met à jour le discriminant "dogs\_1941945966":
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées à la première étape.
    - Remplacez `{classifier_id}` par l'ID du discriminant que vous vous voulez mettre à jour.
    - Modifiez l'emplacement de `{class}_positive_examples` pour pointer sur l'endroit où vous avez sauvegardé les fichiers .zip.

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Le discriminant existant "dogs" est remplacé par le discriminant ayant fait l'objet d'un réapprentissage avec le même ID classifier_id. La réponse répertorie le nouvel ensemble de classe et le statut actuel. Exemple :

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    L'apprentissage commence immédiatement. Quand le nouvel ensemble est disponible, le statut passe à `ready`.

    N'émettez pas une autre demande de réapprentissage avant que l'état du statut actuel ne soit à `ready`. Plusieurs demandes de réapprentissage d'un discriminant n'aboutissent qu'à l'exécution d'un seul réapprentissage. Un horodatage intitulé `retrained` indique la dernière fois que le réapprentissage d'un discriminant s'est terminé. Si vous appelez la méthode `/classify` alors que le discriminant est en réapprentissage, la dernière définition du discriminant est utilisée.{: tip}
1.  Vérifiez périodiquement le statut d'apprentissage jusqu'à voir un statut `ready`. Remplacez `{api  key}` et `{classifier_id}` par vos propres informations :

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Etape 4 : classification d'une image avec un discriminant personnalisé
{: #classify}

Quand le nouveau discriminant est prêt, appelez-le pour voir comment il se comporte.

1.  Créez un fichier JSON intitulé `myparams.json` qui inclut les paramètres de votre appel, comme l'ID `classifier_id` pour votre nouveau discriminant ainsi que pour celui du modèle General (qui utilise l'ID classifier_id `default`). Un fichier JSON simple ressemble à ceci :

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  Téléchargez le fichier <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Utilisez la méthode `POST /v3/classify` pour tester votre discriminant personnalisé. L'exemple suivant classifie l'image `dogs.jpg` par rapport au discriminant "dogs\_1941945966" :
    - Remplacez `{api-key}` par les données d'identification de service que vous avez copiées à la première étape.

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Pour ne classifier que par rapport au modèle intégré General, omettez le paramètre `parameters`.
    {: tip}

    La réponse inclut les discriminants, leurs classes et un score pour chaque classe. Les scores sont compris entre 0 et 1 ; plus le score est élevé, plus la corrélation est grande. Les appels `/v3/classify` omettent les classes à scores bas par défaut si des classes à scores élevés sont identifiées. Vous pouvez définir un score minimum à afficher en spécifiant une valeur en virgule flottante pour le paramètre `threshold` de votre appel.

    ```json
    {
      "images": [
    {
          "classifiers": [
        {
              "classes": [
            {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [
            {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  Examinez vos résultats.

Vous avez terminé ! Vous avez créé, entraîné et interrogé un discriminant personnalisé avec {{site.data.keyword.visualrecognitionshort}}.

### Suppression de votre discriminant personnalisé

Vous pouvez vouloir supprimer votre discriminant personnalisé pour commencer à développer votre application avec une instance propre.

Pour supprimer le discriminant, appelez la méthode `DELETE /v3/classifiers/{classifier_id}`. Remplacez `{api_key)` et`classifier_id` par vos propres informations :

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## Etapes suivantes

Maintenant que vous savez maintenant comment utiliser les discriminants personnalisés, vous pouvez aller plus loin :

- Consultez la page [Best practices for custom classifiers in Watson Visual Recognition![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Informez-vous sur l'API en consultant [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attributions
{: #attributions}

Toutes les images utilisées sur cette page proviennent de Flikr et sont utilisées sous licence [Creative Commons - Attribution 2.0 Generic (CC BY 2.0)![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Aucune modification n'a été apportée à ces images.
