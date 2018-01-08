---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# Reconnaissance de texte dans des scènes de la vie de tous les jours

Utilisez le modèle Text en version bêta pour détecter et reconnaître un texte en anglais dans des images. Ce modèle est conçu pour reconnaître du texte dans un texte imprimé dans une image plutôt que du texte plus dense dans des documents.

Le modèle Text, qui est une fonction bêta, n'est pas destiné à être utilisé dans un environnement de production. Pour plus d'informations, voir "Fonctions bêta" dans [Notes sur l'édition](/docs/services/visual-recognition/release-notes.html#beta).
{: tip}

Le modèle Text fonctionne mieux sur les chaînes de texte court. Ainsi, une utilisation courante de ce modèle est la lecture des panneaux de signalisation.

![Panneau de signalisation avec des encadrés englobant les mots détectés](images/road-sign-text-detection.png)

![Mots détectées dans la photo d'un panneau de signalisation, avec les scores de confiance associés](images/road-sign-text-response.png)

Les encadrés blancs signalent chaque mot que le modèle a détecté dans l'image.

## Réponse

La réponse inclut la chaîne détectée et chaque mot de cette chaîne est identifiée avec les informations suivantes :

- Le mot détecté
- Un score qui indique la confiance dans l'exactitude du mot détecté.
- L'emplacement de l'encadré englobant le mot. Cet encadré indique où le mot se trouve dans l'image.
- Le numéro de la ligne où a été détecté le mot.

## Conseils pour la mise en oeuvre d'une reconnaissance de texte efficace

Le texte inclus dans les images est mieux reconnu s'il respecte les règles suivantes :

- Le texte se compose principalement de mots complets et non pas de suites de lettres (codes produit, par exemple). Le modèle reconnaît des mots plutôt que des caractères individuels et risque de ne pas tenir compte de "mots" formés d'une lettre unique ou de nombres.
- Le texte est imprimé dans une police standard et non pas dans une police très stylisée. Ainsi, le texte figurant sur une plaque d'immatriculation ou une affiche de films peut ne pas être reconnu. De même, un texte écrit à la main peut ne pas être détecté.
- Le texte prend au moins 5 %  de l'image.
- Le texte n'est pas écrit à plus de 45 degrés de l'horizontal. Le modèle Text en version bêta lit les étiquettes EXIF et fait pivoter les images. Toutefois, pour optimiser la capacité de traitement, n'envoyez via le service que les images qui n'ont pas besoin de pivoter (l'étiquette EXIF **Orientation** est définie à `1`).
- Le modèle Text est entraîné sur les mots anglais. Un texte dans une autre langue que l'anglais ne sera pas reconnu.

## Etapes suivantes

Familiarisez-vous avec l'API dans [Watson API Explorer ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window}

Si vous avez des questions ou des commentaires sur le modèle Text, contactez Kevin Gong à l'adresse kgong@us.ibm.com.

---

Retournez aux [documentations](/docs/services/visual-recognition/index.html) principales.
