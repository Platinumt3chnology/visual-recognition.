---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

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

# Reconnaissance de texte dans des scènes de la vie de tous les jours (version bêta)
{: #recognize-text}

Utilisez le modèle Text en version bêta de {{site.data.keyword.visualrecognitionshort}} pour détecter et reconnaître un texte en anglais dans des images. Ce modèle est conçu pour reconnaître du texte dans des images plutôt que du texte plus dense dans des documents.

Le modèle Text est une fonction bêta privée, et {{site.data.keyword.IBM_notm}} doit vous autoriser à envoyer des appels au modèle. [Demandez l'accès à ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Pour plus d'informations sur les fonctions bêta, voir les [Notes sur l'édition](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Le modèle Text fonctionne mieux sur les chaînes de texte court. Par exemple, la lecture de panneaux constitue une utilisation courante de ce modèle. 

![Panneau de signalisation avec des encadrés englobants autour des mots reconnus. Photo prise par Ashim D’Silva pour Unsplash](images/walk-signal-detection.png) ![Mots et scores de fiabilité détectés dans l'image de panneau de signalisation](images/walk-signal-response.png)

Les encadrés blancs signalent chaque mot que le modèle a reconnus dans l'image.

## Réponse
{: #recognize-text-response}

La réponse inclut la chaîne détectée et chaque mot de cette chaîne est identifiée avec les informations suivantes :

- Le mot reconnu.
- Un score indiquant la fiabilité du niveau de reconnaissance du mot.
- L'emplacement de l'encadré englobant le mot. Cet encadré indique où le mot se trouve dans l'image.
- Le numéro de la ligne où a été détecté le mot.

## Conseils pour la mise en oeuvre d'une reconnaissance de texte efficace
{: #recognize-text-guidelines}

Le texte inclus dans les images est mieux reconnu s'il respecte les règles suivantes :

- Le texte se compose principalement de mots complets et non pas de suites de lettres (codes produit, par exemple). Le modèle reconnaît des mots plutôt que des caractères individuels et risque de ne pas tenir compte de "mots" formés d'une lettre unique ou de nombres.
- Le texte est imprimé dans une police standard et non pas dans une police très stylisée. Ainsi, le texte figurant sur une plaque d'immatriculation ou une affiche de films peut ne pas être reconnu. De même, un texte écrit à la main peut ne pas être détecté.
- Le modèle Text est entraîné principalement sur les mots anglais. Un texte dans une autre langue que l'anglais risque de ne pas être reconnu.

## Etapes suivantes
{: #recognize-text-next-steps}

- [Faites un essai](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text) de reconnaissance de texte dans une image.
- Familiarisez-vous avec l'API dans la [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window}.
