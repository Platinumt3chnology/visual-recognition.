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

# Custom Object Detection (Beta)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} Custom Object Detection (Beta) identifica elementos y su ubicación en una imagen. El servicio detecta estos elementos en función de un conjunto de imágenes con datos de entrenamiento etiquetados que proporciona el usuario.
{: shortdesc}

Custom Object Detection es una característica beta privada y debe tener el permiso de {{site.data.keyword.IBM_notm}} para realizar llamadas al modelo. [Solicite acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}. Para obtener más información sobre las características beta, consulte las [Notas del release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Debe entrenar el modelo de detección de objetos para que reconozca los objetos importantes para el flujo de trabajo o el dominio. Por ejemplo, lo puede entrenar para que detecte desperfectos en automóviles, para que busque máquinas que necesitan mantenimiento o para que realice inspecciones visuales sobre el campo. También puede utilizar la detección de objetos para contar objetos o para gestionar inventario.

## Comparación entre la clasificación y la detección de objetos
{: #obj-detect-comparison}

El modelo Custom Object Detection es la característica más reciente del servicio {{site.data.keyword.visualrecognitionshort}}, que incluye clasificación.

La clasificación y la detección de objetos son funciones parecidas, pero tienen distintas aplicaciones. En general, si desea predecir la existencia de objetos en una imagen, utilice la clasificación. Si desea localizar o contar los objetos de una imagen, utilice la detección de objetos.

### Clasificación
{: #obj-detect-classify}

Cuando se clasifica una imagen, el servicio responde con la probabilidad de que determinados objetos se encuentran en dicha imagen. Puede utilizar los modelos integrados (General, Food o Explicit), o puede crear su propio modelo personalizado.

Por ejemplo, cuando clasifica una imagen de galletas como la siguiente, el servicio predice que hay galletas en la imagen con una fiabilidad del 95 %.

![Imagen de respuesta de clasificación](images/cookies-tag.png "Una imagen para mostrar la clasificación")

### Detección de objetos
{: #obj-detect-detect}

La detección de objetos personalizados se parece a la clasificación personalizada, pero el servicio identifica la ubicación de los elementos en la imagen. Al igual que la clasificación, la respuesta también incluye la etiqueta de cada elemento que detecta y el grado de fiabilidad en su identificación.

Los elementos que se detectan se basan en la información que proporciona el usuario al entrenar un modelo de detección de objetos.

En la imagen siguiente, el método **Analizar imágenes** de Custom Object Detection identifica la ubicación de las galletas en la imagen. Cada objeto detectado incluye la etiqueta (en este caso `Cookie`) con su ubicación y su nivel de fiabilidad.

![Imagen de respuesta de la detección de objetos](images/cookies-bbox.png "Una imagen para mostrar la detección de objetos")

## Cómo utilizar Custom Object Detection
{: #object-detection-sequence}

Para utilizar {{site.data.keyword.visualrecognitionshort}} Custom Object Detection, siga estos pasos para configurar un modelo de detección de objetos personalizado:

1.  Cree una colección: una colección es un contenedor para las imágenes y los datos de entrenamiento. Consulte [Creación de una colección ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} en la Consulta de API v4.
1.  Añada sus imágenes a la colección. Puede añadir imágenes individuales por URL o por archivo, o bien puede cargar un archivo `.zip` de imágenes. Consulte [Adición de imágenes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} en la Consulta de API v4.
1.  Añada datos de entrenamiento a las imágenes. Consulte [Preparación de los datos de entrenamiento](#object-detection-preparation).
1.  Entrene la colección. Cuando ya disponga de suficientes datos de entrenamiento, comience a entrenar las imágenes de la colección. Consulte [Entrenamiento de una colección ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} en la Consulta de API v4.

Después de completar estos pasos y de entrenar la colección, puede analizar imágenes ante la misma.

### Preparación de los datos de entrenamiento
{: #object-detection-preparation}

La parte más importante del proceso de configuración es preparar y ensamblar los datos de entrenamiento. Al igual que hace cuando [crea un modelo personalizado](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) para clasificar las imágenes, debe ensamblar un conjunto de imágenes que representan los objetos que desea detectar.

Además de un conjunto de imágenes, también debe proporcionar datos de entrenamiento para cada imagen. Para la detección de objetos, los datos de entrenamiento son el conjunto de etiquetas y ubicaciones de los objetos de la imagen que desea que {{site.data.keyword.visualrecognitionshort}} reconozca. Puede tener más de un objeto en una imagen.

La etiqueta identifica qué es el objeto. La ubicación identifica dónde se encuentra en la imagen. Para identificar la ubicación, dibuje un _recuadro delimitador_ alrededor del objeto y proporcione las coordenadas de los píxeles superior e izquierdo de dicho recuadro, junto con la anchura y la altura en píxeles.

En el siguiente ejemplo se muestran los datos de entrenamiento de un objeto llamado `BurntCookie`.

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

En este release beta inicial, se crea la información de ubicación a mano o mediante una herramienta de anotación de imágenes.

En general, cuantas más imágenes y más recuadros delimitadores proporcione en los datos de entrenamiento, mejor. Para empezar, siga estas directrices de entrenamiento de datos:

- Cada imagen debe tener al menos 500 píxeles de altura y de anchura.
- Cada objeto etiquetado de la colección debe tener al menos 100 ubicaciones (recuadros delimitadores).
- Cada imagen de la colección debe tener como máximo 10 recuadros delimitadores.
- El tamaño de cada recuadro delimitador debe ser mayor que el 15 % de las dimensiones de la imagen.
- La API leer los códigos de orientación EXIF de las imágenes. Asegúrese de que las coordenadas de `ubicación` coinciden con dicha orientación. Para ajustar la orientación, puede utilizar una herramienta como ImageMagick para _orientar automáticamente_ las imágenes antes de añadir recuadros delimitares.

Para obtener más información sobre el método **Añadir datos de entrenamiento a una imagen**, repase la [Consulta de API v4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}.

### Entrenamiento de la colección
{: #object-detection-train}

Después de añadir los datos de entrenamiento a las imágenes de la colección, el paso de configuración final consiste en entrenar un modelo de detección de objetos. Una sola llamada a la API inicia el entrenamiento, y la respuesta incluye información de estado. Por ejemplo, el estado siguiente muestra que el entrenamiento ha comenzado pero aún no ha terminado:

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

Puede volver a entrenar un modelo después de actualizar los datos de entrenamiento emitiendo de nuevo la llamada.

Para obtener más información, consulte [Entrenamiento de una colección ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} en la Consulta de API v4.

## Análisis de imágenes
{: #object-detection-analyze}

Después de configurar un modelo de detección de objetos personalizado y de que finalice el entrenamiento, puede detectar objetos en otras imágenes. Al igual que sucede con la clasificación, debe proporcionar una imagen o un archivo `.zip` de imágenes y un **umbral** opcional para establecer la puntuación mínima de los objetos detectados. Para obtener más información, consulte el método **Analizar imágenes** en la [Consulta de API v4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images).

## Pasos siguientes
{: #object-detection-next-steps}

- Familiarícese con la API en la [Consulta de API v4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")][api-ref-v4]{: new_window}.
