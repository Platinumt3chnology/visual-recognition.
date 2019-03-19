---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition languages,language support,supported languages

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

# Langues prises en charge

## Classifier des images
{: #language-support}

La méthode **Classify images** d'{{site.data.keyword.visualrecognitionfull}} prend en charge l'anglais (`en`), l'arabe (`ar`), l'allemand (`de`), l'espagnol (`es`), le français (`fr`), l'italien (`it`), le japonais (`ja`), le coréen (`ko`), le portugais (Brazilian) (`pt-br`), le chinois simplifié (`zh-cn`) et le chinois traditionnel (`zh-tw`).

Les langues utilisent les classes de sortie de tous les modèles intégrés : `default` (également appelé modèle General), `food` et `explicit`.

Pour des détails sur l'appel d'API, voir la méthode **Classify images** dans [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

## Détecter des visages
{: #detect_faces}

Les méthodes **Detect faces** renvoient des traductions des mots anglais pour le sexe ("Male" et "Female") dans la réponse. Définissez la langue avec l'en-tête de requête **Accept-Language**.

Pour des détails, voir la méthode **Detect faces** dans [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.
