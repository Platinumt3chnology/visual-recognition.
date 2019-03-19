---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom object detection,object detection,bounding boxes,visual inspection
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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

<!-- Link definitions -->

[api-ref-v4]: https://{DomainName}/apidocs/visual-recognition-v4

# Custom Object Detection (version bêta)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} Custom Object Detection (version bêta) identifie les éléments et leur emplacement dans une image. Le service détecte ces éléments en fonction d'un ensemble d'images avec des données d'apprentissage libellées que vous fournissez.
{: shortdesc}

La détection d'objet personnalisée (Custom Object Detection) est une fonction bêta privée pour laquelle {{site.data.keyword.IBM_notm}} doit vous donner les droits pour passer des appels au modèle. [Demandez l'accès à ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}. Pour plus d'informations sur les fonctions bêta, voir les [Notes sur l'édition](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Vous entraînez le modèle de détection d'objet à reconnaître des objets qui sont important pour votre flux de travaux ou votre domaine. Vous allez, par exemple, détecter des dégâts causés à un véhicule, rechercher des machines qui ont besoin d'une opération de maintenance, ou encore effectuer des inspections visuelles sur le terrain. Vous pouvez également utiliser la détection d'objet pour compter les objets ou générer le stock. 

## Comparaison de la détection d'objet et de la classification
{: #obj-detect-comparison}

Le modèle Custom Object Detection (détection d'objet personnalisée) constitue la fonction la plus récente du service {{site.data.keyword.visualrecognitionshort}}, lequel inclut la classification.

Classification et détection d'objet sont similaires mais ont un usage différent. En règle générale, si vous souhaitez prédire l'existence d'objets dans un image, vous utiliserez la classification. Si vous souhaitez localiser ou compter des objets dans une image, vous allez opter pour la détection d'objet. 

### Classification
{: #obj-detect-classify}

Lorsque vous classifiez une image, le service fournit une réponse de probabilité de la présence de certains objets dans l'image en question. Vous pouvez utiliser les modèles intégrés (General, Food ou Explicit), ou bien vous pouvez créer votre propre modèle personnalisé. 

Ainsi, lorsque vous classifiez une image de cookies comme dans l'image suivante, le service prédit que l'image comporte des cookies avec un niveau de fiabilité de 95 %. 

![Image de réponse de classification](images/cookies-tag.png "Image illustrant la classification")

### Détection d'objet
{: #obj-detect-detect}

La détection d'objet personnalisée est similaire à la classification personnalisée, à la différence près que le service identifie l'emplacement des éléments dans l'image. Comme pour la classification, la réponse inclut le libellé de chaque élément détecté, ainsi que le niveau de fiabilité dans son identification.

Les éléments sont détectés en fonction des informations que vous fournissez lors de l'entraînement d'un modèle de détection d'objet. 

Dans l'image suivante, la méthode **Analyze images** (analyser les images) de Custom Object Detection identifie l'emplacement des cookies dans l'image. Chaque objet détecté inclut le libellé (dans le cas présent, `Cookie`) avec son emplacement et un score de fiabilité. 

![Image de réponse de détection d'objet](images/cookies-bbox.png "Image illustrant la détection d'objet")

## Comment utiliser Custom Object Detection
{: #object-detection-sequence}

Pour utiliser {{site.data.keyword.visualrecognitionshort}} Custom Object Detection, suivez cette procédure afin de configurer un modèle de détection d'objet personnalisé :

1.  Créez une collection : Une collection est un conteneur pour vos images et données d'apprentissage. Voir [Create a collection ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} dans la référence d'API de la version 4. 
1.  Ajoutez vos images à la collection. Vous pouvez ajouter des images individuelles par URL ou par fichier, ou bien télécharger un fichier `.zip` d'images. Voir [Add images ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} dans la référence d'API de la version 4. 
1.  Ajoutez des données d'apprentissage à vos images. Voir [Préparation de vos données d'apprentissage](#object-detection-preparation).
1.  Entraînez votre collection. Une fois que vous disposez de suffisamment de données d'apprentissage, démarrez l'entraînement sur les images de la collection. Voir [Train a collection ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} dans la référence d'API de la version 4.

Une fois la procédure exécutée et la collection entraînée, vous pouvez analyser des images en fonction de votre collection. 

### Préparation de vos données d'apprentissage
{: #object-detection-preparation}

La partie la plus importante du processus de configuration consiste à préparer et assembler vos données d'apprentissage. Tout comme lorsque vous [créez un modèle personnalisé](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) pour la classification d'images, vous assemblez un ensemble d'images qui représentent les objets que vous souhaitez détecter.

Outre cet ensemble d'images, vous fournissez également des données d'apprentissage pour chaque image. Pour la détection d'objet, les données d'apprentissage correspondent à l'ensemble de libellés et d'emplacements d'objets dans l'image que {{site.data.keyword.visualrecognitionshort}} doit reconnaître. Vous pouvez avoir plusieurs objets par image.

Le libellé identifie l'objet. L'emplacement correspond à la position de l'objet dans l'image. Vous identifiez l'emplacement en traçant un _encadré englobant_ autour de l'objet et en indiquant les coordonnées des pixels supérieur et gauche de l'encadré, ainsi que la largeur et la hauteur en pixels.

L'exemple suivant montre les données d'apprentissage d'un objet libellé `BurntCookie`.

```json
{
  "objects": [{
    "object": "BurntCookie",
    "location": {
      "left": 33,
      "top": 8,
      "width": 163,
      "height": 119
    }
  }]
}
```
{: codeblock}

Dans cette édition bêta initiale, vous créez les informations d'emplacement à la main ou à l'aide d'un outil d'annotation d'image.

En général, plus vous fournissez d'images et d'encadrés englobants dans vos données d'apprentissage, meilleur sera le résultat. Voici quelques instructions concernant les données d'apprentissage pour vous aider à commencer : 

- Chaque image mesure au moins 500 pixels en hauteur et en largeur.
- Chaque objet libellé dans la collection possède au moins 100 emplacements (encadrés englobants).
- Chaque image de la collection ne comporte pas plus de 10 encadrés englobants.
- La taille de chaque encadré englobant représente plus de 15 % des dimensions de l'image.
- L'API lit les libellés d'orientation EXIF dans vos images. Assurez-vous que les coordonnées de `location` correspondent à cette orientation. Pour ajuster l'orientation, vous pouvez utiliser un outil comme ImageMagick pour _orienter automatiquement_ vos images avant d'ajouter des encadrés englobants. 

Pour plus d'informations sur la méthode d'**ajout de données d'apprentissage à une image**, voir [v4 API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}.

### Former la collection
{: #object-detection-train}

Après avoir ajouté les données d'apprentissage aux images de votre collection, l'étape finale de la configuration consiste à entraîner un modèle de détection d'objet. Un simple appel de l'API démarre l'entraînement, et la réponse inclut des informations de statut. Par exemple, le statut suivant indique que l'entraînement a débuté mais n'est pas encore terminé :

```json
"training_status": {
  "objects": {
    "ready": false,
    "in_progress": true,
    "data_changed": false,
    "latest_failed": false,
    "description": "Starting training"
  }
}
```
{: codeblock}

Vous pouvez entraîner à nouveau un modèle après une mise à jour des données d'apprentissage en relançant l'appel.

Pour plus d'informations, voir [Train a collection ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} dans la référence d'API de la version 4.

## Analyser des images
{: #object-detection-train}

Après avoir configuré un modèle de détection d'objet personnalisé et une fois l'entraînement terminé, vous pouvez détecter des objets dans d'autres images. Comme pour la classification, vous fournissez une image ou un fichier `.zip` d'images et un **seuil** facultatif pour définir le score minimal des objets détectés. Pour plus d'informations, voir la méthode **Analyze images** dans [v4 API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images).

## Etapes suivantes
{: #object-detection-next-steps}

- Familiarisez-vous avec l'API dans [v4 API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")][api-ref-v4]{: new_window}.
