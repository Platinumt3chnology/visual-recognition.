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

# Migración a {{site.data.keyword.visualrecognitionshort}} desde {{site.data.keyword.alchemyvisionshort}}

El 19 de mayo de 2016, el servicio {{site.data.keyword.alchemyvisionshort}} dejó de estar en uso y su funcionalidad pasó a formar parte de {{site.data.keyword.visualrecognitionshort}} (GA). Para migrar una aplicación desplegada en {{site.data.keyword.Bluemix_notm}} desde el servicio {{site.data.keyword.alchemyvisionshort}} al servicio {{site.data.keyword.visualrecognitionshort}}, actualice el código.
{: shortdesc}

Las siguientes diferencias entre {{site.data.keyword.alchemyvisionshort}} y {{site.data.keyword.visualrecognitionshort}} pueden afectar al código de aplicación:

- **Clases y clasificadores:** en {{site.data.keyword.alchemyvisionshort}}, las imágenes analizadas se etiquetaban con "etiquetas". En {{site.data.keyword.visualrecognitionshort}}, las "etiquetas" se llaman "clases". Los grupos de clases se denominan "clasificadores". Todas las etiquetas predeterminadas de {{site.data.keyword.alchemyvisionshort}} están todavía disponibles como clases en {{site.data.keyword.visualrecognitionshort}}.
- **Clasificadores personalizados:** {{site.data.keyword.visualrecognitionshort}} le permite entrenar y crear clases y clasificadores personalizados.
- **Entrada por lotes:** en {{site.data.keyword.visualrecognitionshort}}, ahora puede clasificar lotes de imágenes o URL de imágenes enviando archivos de imagen en un archivo comprimido (.zip) o un URL de imagen único en una serie JSON.
- **Especificar idioma:** en {{site.data.keyword.alchemyvisionshort}}, se especifica el idioma de una llamada de etiquetado como un parámetro de consulta. En {{site.data.keyword.visualrecognitionshort}}, se especifica el idioma de una llamada de clasificación en la cabecera `Accept-Language`.
- **Puntos finales:** la siguiente funcionalidad de {{site.data.keyword.alchemyvisionshort}} se incluye en nuevos puntos finales en el release GA de {{site.data.keyword.visualrecognitionshort}}:

| Funcionalidad | Punto final de {{site.data.keyword.alchemyvisionshort}} (en desuso) | Punto final de {{site.data.keyword.visualrecognitionshort}} (GA) |
|---------------|--------------------|----------------|
| Etiquetar imágenes con clasificadores incorporados | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Detectar caras, rango de edad y género | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Extraer imagen principal de HTML o de un URL de sitio web | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | Puede proporcionar una imagen por URL a los métodos `/v3/classify` y `/v3/detect_faces`, no a través de un punto final autónomo. |
