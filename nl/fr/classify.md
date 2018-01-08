---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

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

# A propos des discriminants

Quand vous classifiez une image, Visual Recognition retourne un ensemble de classes trouvées dans l'image. Il tire ces informations des images sur lesquelles il est formé. Un discriminant est un groupe de classes.

Visual Recognition inclut plusieurs discriminants intégrés qui peuvent fournir des résultats extrêmement précis sans qu'un apprentissage ne soit nécessaire. Vous pouvez également former des discriminants personnalisés pour créer des classes spécialisées.

Initiation à Clarifai
> Le type de prédiction repose sur le modèle au travers du lequel vous exécutez l'entrée. Ainsi, si vous exécutez votre entrée via le modèle food, les prédictions qu'il retourne contiennent les concepts connus du modèle food. Si vous exécutez votre entrée via le modèle color, il retourne des prédictions sur les couleurs dominantes de votre image.
Clarifai
> Clarifai fournit divers modèles différents qui "voient" le monde différemment. Un modèle contient un groupe de concepts. Il ne voit que les concepts qu'il comporte.
>
> Il y a des moments où vous aimeriez avoir un modèle qui voit le monde de la même façon que vous. L'API vous permet d'obtenir ce résultat. Vous pouvez créer votre propre modèle et le former avec vos propres images et concepts. Une fois que vous l'avez entraîné à voir comme vous voulez qu'il voit, vous pouvez alors l'utiliser pour faire des prédictions.

## Discriminants intégrés

Visual Recognition inclut un ensemble de discriminants qui fournissent des résultats extrêmement précis sans apprentissage. Les discriminants intégrés actuels sont intitulés `default`, `food` et `explicit`.

### Discriminant default

Le discriminant default retourne des classes à partir de milliers d'étiquettes possibles organisées en catégories et sous-catégories. Les catégories de niveau supérieur suivantes peuvent être retournées :

- Animaux (incluant les oiseaux, les reptiles, les amphibiens, etc.)
- Personnes et informations relatives aux personnes et à leurs activités
- Nourriture (incluant les aliments cuisinés et les boissons)
- Plantes (incluant les arbres, arbustes, plantes aquatiques, légumes)
- Sports
- Nature (incluant de nombreux types de formations naturelles et de structures géologiques)
- Transport (terre, mer, air)
- Et bien d'autres catégories, incluant l'ameublement, les fruits, les instruments de musique, les outils, les couleurs, les gadgets, les appareils, les instruments, les armes, les bâtiments, les structures, les objets, vêtements et habits synthétiques ou les fleurs, par exemple.

### Discriminant food

Bien que le discriminant default soit en mesure d'identifier la nourriture et les boissons, vous pouvez utiliser le discriminant `food` intégré.

### Discriminant explicit

Visual Recognition peut classifier une image comme étant non adaptée à une utilisation générale. Le discriminant `explicit` identifie actuellement les images pouvant être considérées comme images à caractère pornographique. Une abréviation courante pour cette classification est _NSFW_, qui signifie _not safe for work._

Un score au-dessus ou au-dessous d'un certain chiffre n'indique pas de façon absolue que l'image n'est pas adaptée (ou est adaptée) à une utilisation générale. Toutefois, vous pouvez utiliser la réponse en tant que filtre initial de l'image et effectuer une analyse plus approfondie depuis ce point.

Réponse :
```json
{
  "images": [
    {
      "classifiers": [
        {
          "classes": [
            {
              "class": "not explicit",
              "score": 0.704
            }
          ],
          "classifier_id": "explicit",
          "name": "explicit"
        }
      ],
      "resolved_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png",
      "source_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png"
    }
  ],
  "images_processed": 1
}
```
{: codeblock}

## Combinaison de discriminants


## Hiérarchie de classes dans la réponse

La méthode `/v3/classify` classifie les images dans une hiérarchie de classes apparentées. Ainsi, l'image d'un beagle peut être classifiée en tant qu'"animal", mais aussi intégrée dans les classes apparentées "chien" ou "beagle". Une correspondance positive avec les classes apparentées, dans ce cas "chien" et "beagle", augmente le score de la réponse parent. Dans cet exemple, la réponse inclut les trois classes : "animal", "chien" et "beagle". Le score de la classe parent ("animal") est augmenté, car il correspond aux classes apparentées ("chien" et "beagle"). Le parent est aussi un élément "type\_hierarchy" pour montrer qu'il s'agit d'un parent de la hiérarchie.

## Instructions pour classifier de gros volumes d'images

Quand vous soumettez un grand nombre d'images, optimisez l'efficacité et les performances du service en procédant comme suit :

- Rognez ou redimensionnez vos images pour qu'elles atteignent une taille de 224 x 224 pixels. Le service est optimisé pour l'instant pour cette taille, même s'il est possible que cela change plus tard.
    - Rognez l'image si son rapport hauteur/largeur est supérieur à 2:1 ou inférieur à 1:2.
    - Envisagez une découpe de l'image en plusieurs images carrées différentes, ou n'incluez que le centre de l'image, selon ce qui est le plus important pour votre utilisation.
- Soumettez un maximum de 20 images dans un même fichier .zip. Vous n'avez pas besoin de les compresser, car les images JPEG et PNG sont déjà compressées.
- Utilisez le paramètre **classifier_ids** pour ne spécifier que les discriminants que vous voulez utiliser.
- Bien que le service soit capable de lire les étiquettes EXIF et de faire pivoter les images, pour optimiser la capacité de traitement, n'envoyez via le service que les images qui n'ont pas besoin de pivoter (l'étiquette EXIF **Orientation** est définie à `1`).
