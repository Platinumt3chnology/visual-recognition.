---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# Migration vers {{site.data.keyword.visualrecognitionshort}} depuis {{site.data.keyword.alchemyvisionshort}}

Le 19 mai 2016, le service {{site.data.keyword.alchemyvisionshort}} a été déprécié et ses fonctionnalités ont été intégrées dans {{site.data.keyword.visualrecognitionshort}} (GA). Pour migrer une application, déployée sur {{site.data.keyword.Bluemix_notm}}, entre le service {{site.data.keyword.alchemyvisionshort}} et le service {{site.data.keyword.visualrecognitionshort}}, mettez à jour votre code.
{: shortdesc}

Les différences ci-après entre {{site.data.keyword.alchemyvisionshort}} et {{site.data.keyword.visualrecognitionshort}} peuvent affecter votre code d'application :

- **Classes et discriminants :** dans {{site.data.keyword.alchemyvisionshort}}, les images étaient identifiées avec des "étiquettes". Dans {{site.data.keyword.visualrecognitionshort}}, ces "étiquettes" sont appelées "classes". Les groupes de classes sont appelés "discriminants". Toutes les étiquettes par défaut provenant d'{{site.data.keyword.alchemyvisionshort}} sont toujours disponibles en tant que classes dans {{site.data.keyword.visualrecognitionshort}}.
- **Discriminants personnalisés : ** {{site.data.keyword.visualrecognitionshort}} vous permet d'entraîner et de créer des classes et discriminants personnalisés.
- **Entrées par lot :** dans {{site.data.keyword.visualrecognitionshort}}, vous pouvez maintenant classifier des lots ou des URL d'images en soumettant des fichiers image dans un fichier (.zip) compressé ou une URL d'image unique dans une chaîne JSON.
- **Spécification d'une langue :** dans {{site.data.keyword.alchemyvisionshort}}, vous spécifiiez la langue d'un appel d'étiquetage en tant que paramètre de requête. Dans {{site.data.keyword.visualrecognitionshort}}, vous spécifiez la langue dans un appel classify de l'en-tête `Accept-Language`.
- **Noeuds finaux :** les fonctionnalités {{site.data.keyword.alchemyvisionshort}} ci-après sont incluses dans de nouveaux noeuds finaux de l'édition GA (General Availability) de {{site.data.keyword.visualrecognitionshort}} :

| Fonctionnalité | Noeud final {{site.data.keyword.alchemyvisionshort}} (déprécié) | Noeud final {{site.data.keyword.visualrecognitionshort}} (GA) |
|---------------|--------------------|----------------|
| Etiqueter les images avec des discriminants intégrés | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Détecter les visages, la tranche d'âge et le sexe | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Extraire une image principale depuis HTML ou une URL de site Web | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | Vous pouvez fournir une image par URL aux méthodes `/v3/classify` et `/v3/detect_faces`, et non via un noeud final unique. |
