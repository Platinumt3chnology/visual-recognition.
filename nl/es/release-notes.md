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

# Notas del release

Están disponibles las siguientes nuevas características y cambios en el servicio.
{: shortdesc}

## Características beta
{: #beta}

{{site.data.keyword.IBM_notm}} publica servicios, características y soporte de idioma clasificados como beta, para evaluarlos. Estas características pueden ser inestables, pueden cambiar con frecuencia y pueden dejar de recibir soporte tras un aviso con poca antelación. Las características beta también pueden no proporcionar el mismo nivel de rendimiento o compatibilidad que proporcionan las características con disponibilidad general, y no están pensadas para su uso en un entorno de producción. Las características beta solo tienen soporte en [developerWorks Answers ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Cambios
{: #changelog}

Están disponibles las siguientes nuevas características y cambios en el servicio.

### 11 de diciembre de 2017
{: #11december2017}

<ul>
  <li>
    <strong>Mayor precisión y salida con el modelo General</strong>
      <p>
        El modelo general, que contiene varios miles de etiquetas, ahora detecta más objetos secundarios y ha mejorado la detección de escena. Estas mejoras ayudan a reconocer los aspectos menos destacados de una imagen. Además, el número medio de etiquetas devueltas por imagen ha aumentado a 10.
      </p>
      <p>
        La siguiente imagen muestra un ejemplo de las etiquetas devueltas antes de la actualización y las etiquetas adicionales que se devuelven ahora.
      </p>
      <img src="images/antarctica-iceberg.jpg" alt="Iceberg en la Antártida">
      <table>
        <tr>
          <th>Etiquetas originales</th>
          <th>Etiquetas adicionales</th>
        </tr>
        <tr>
          <td>
          Etiqueta: iceberg<br/>
          Puntuación: 0,919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          Etiqueta: ice mass<br/>
          Puntuación: 0,801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Etiqueta: nature<br/>
          Puntuación: 0,770</td>
        </tr>
        <tr>
          <td>
          Etiqueta: blue color<br/>
          Puntuación: 0,975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Etiqueta: alabaster color<br/>
          Puntuación: 0,5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nuevo modelo explícito disponible en beta</strong>
      <p>
        El modelo Explicit, que se inicia en beta, clasifica si una imagen incluye contenido pornográfico y no es apropiada para el uso general. Puede incluir el modelo Explicit con otros modelos para un análisis combinado. Por ejemplo, incluya los ID de clasificador `default` y `explicit` en la solicitud para devolver etiquetas de imagen y saber si la imagen incluye contenido explícito.
      <p>
        Para obtener más información sobre la llamada a la API, consulte el método **Clasificar imágenes** en la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image), o pruebe el modelo en el [Explorador de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify).
      </p>
    </li>
    <li>
      <strong>Soporte para tamaños de archivo grandes</strong>
      <p>
        El método <strong>Clasificar imágenes</strong> ahora admite archivos de imagen de hasta 10 MB y archivos .zip de hasta 100 MB.
    </li>
    <li>
      <strong>Matriz necesaria al pasar ID de clasificador</strong>
      <p>
        La API ahora impone una matriz cuando se pasan `classifier_ids` como parte del objeto **parameters** en el método **Clasificar imágenes**. Anteriormente, se podía pasar un ID de clasificador como una serie. Para obtener más información, consulte el archivo de ejemplo y la descripción de parámetros en la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image).
      </p>
    </li>
</ul>

### 8 de septiembre de 2017
{: #8september2017}

- **La versión beta de las recopilaciones y la búsqueda de similitud ha finalizado**: a partir del 8 de septiembre de 2017, ha finalizado el periodo de la versión beta de la búsqueda de similitud. Para obtener más información, consulte [API de Visual Recognition: actualización de búsqueda de similitud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30 de junio de 2017
{: #30june2017}

- **Mejora de etiquetas**: hemos aumentado el número de imágenes de entrenamiento para el clasificador predeterminado. Gracias a ese aumento, mejora la capacidad de reconocer con exactitud la escena general de una imagen. Para obtener detalles, consulte [Más mejoras de la función de etiquetado general ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **Otros idiomas**: el método **Clasificar imágenes** ahora admite coreano, italiano y alemán, además de inglés, árabe, español y japonés.

    Para obtener más información sobre la llamada a la API, consulte el método **Clasificar una imagen** en el icono de enlace externo de la [API de referencia ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}.

### 16 de mayo de 2017
{: #16may2017}

- **Está disponible el nuevo clasificador de alimentos: Beta**

    Un nuevo modelo beta de reconocimiento de alimentos proporciona una mayor precisión y exactitud de las imágenes de alimentos. El método **Clasificar una imagen** permite añadir este nuevo clasificador, "food", al parámetro `classifier_ids`.

### 5 de abril de 2017
{: #5april2017}

- **Nueva {{site.data.keyword.visualrecognitionshort}} herramienta disponible: Beta**

    Hay disponible una nueva característica beta, la herramienta {{site.data.keyword.visualrecognitionshort}}, en [https://watson-visual-recognition.ng.bluemix.net/ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Esta herramienta le facilita el trabajo con el servicio {{site.data.keyword.visualrecognitionshort}}. Al entrar la clave de API de {{{site.data.keyword.cloud_notm}}, puede utilizar una GUI para acceder a las funciones de etiquetado general y detección de caras, y para crear, reentrenar y suprimir fácilmente clasificadores personalizados asociados con la clave de API, sin necesidad de utilizar código.

### 8 de marzo de 2017
{: #8march2017}

- **Actualizado el soporte de idiomas para las etiquetas del clasificador general**

    El clasificador general ahora devuelve etiquetas en todos los idiomas soportados.

- **Problemas conocidos**

    **ARREGLADO 13-04-2017**: llamar repetidamente a `GET /classifiers` mientras se realiza el entrenamiento o reentrenamiento, a fin de comprobar el estado, puede interrumpir el trabajo de entrenamiento. Para solucionar este problema, sondee el estado de un clasificador nuevo utilizando `GET /classifiers/{classifier_id}`. En otras palabras, utilice el clasificador `GET` para un ID de clasificador único, en lugar de `GET /classifiers`, que obtiene todos los clasificadores y puede desencadenar este problema. Tenga en cuenta que `GET /classifiers/{classifier_id}` también es más rápido.

### 15 de diciembre de 2016
{: #15december2016}

- **Mejores etiquetas del clasificador general**

    - Se han actualizado los algoritmos de aprendizaje profundo del clasificador general. Hay una mejora significativa en la calidad de las etiquetas, y un aumento significativo en el volumen de etiquetas en inglés que devuelve el servicio. Estos resultados de etiquetas de gran calidad también están disponibles cuando crea su propio clasificador personalizado.
    - Se han añadido etiquetas de color. El servicio ahora devuelve uno o dos colores principales de la imagen.

- **Problemas conocidos**

    - Las imágenes enviadas a la demostración con etiquetas de metadatos EXIF no especifican la orientación (horizontal o vertical) correctamente al servicio. Las imágenes cargadas con iPhone pueden contener etiquetas de metadatos EXIF. La solución para esto es actualizar los metadatos de imagen para que no se basen en etiquetas de metadatos EXIF para especificar la orientación de la imagen. A menudo, para hacerlo, basta con abrir la imagen en el sistema y guardarla. Por ejemplo, en un Mac, al abrir en vista previa y guardar la imagen, se establecen las etiquetas de orientación correctas.
    - Enviar imágenes al servicio {{site.data.keyword.visualrecognitionshort}} con los valores de [etiqueta EXIF ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://en.wikipedia.org/wiki/Exif){: new_window} 8, 3 o 6 puede añadir latencia. El servicio rota los píxeles de la imagen al punto de vista codificado. Puede ahorrar tiempo rotando previamente sus imágenes o eliminando las cabeceras EXIF si no son importantes para su tarea de {{site.data.keyword.visualrecognitionshort}}.

### 1 de diciembre de 2016
{: #1december2016}

- **Nuevos precios**

    IBM ha reducido el precio de los clasificadores personalizados en el servicio de {{site.data.keyword.visualrecognitionshort}} y ha aumentado los disponibles en el plan gratuito. Para obtener más información, consulte la [página de precios de {{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 de octubre de 2016
{: #7october2016}

- **Mejoras de detección de caras**

    El servicio tiene un nuevo algoritmo de detección de caras que mejora las respuestas de los métodos `GET` y `POST /v3/detect_faces`. El servicio ha ajustado el filtrado de detecciones faciales de edad, nombre y género de poca fiabilidad. Como resultado, se encuentran más caras y se devuelve un rango mayor de fiabilidad.

### 8 de septiembre de 2016
{: #8september2016}

- **Búsqueda de similitud BETA**

    Los usuarios ahora pueden subir su propia colección de imágenes y utilizar una imagen para buscar imágenes similares en dicha colección, y el servicio devuelve los 100 imágenes más similares. La búsqueda de similitud se puede utilizar para cualquier propósito, y los usuarios pueden entrenar al servicio de forma personalizada con colecciones de hasta 1 millón de imágenes cada una. Para obtener más información sobre el uso de la nueva funcionalidad de búsqueda de similitud, consulte las páginas de la [Guía de aprendizaje](/docs/services/visual-recognition/tutorial-collections.html) y la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Ha finalizado la versión beta del reconocimiento de texto**

    Los métodos `POST` y `GET /v3/recognize_text` han finalizado su versión beta. IBM espera seguir dando soporte para los clientes BETA que utilizan el servicio, pero no tiene planeado abrir otra versión beta.

### 1 de agosto de 2016

- **Finalización de los precios introductorios**

    El entrenamiento y reentrenamiento de clasificadores personalizados, la clasificación de imágenes personalizada y el almacenamiento de clasificadores personalizado ya no son gratuitos. Para obtener información sobre los precios, consulte la [página de precios](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) del servicio {{site.data.keyword.visualrecognitionshort}}.

### 5 de julio de 2016
{: #5july2016}

- **Actualización de clasificadores personalizados**

    Los clasificadores personalizados ya no están limitados a un conjunto fijo de datos de entrenamiento. Los usuarios pueden ahora actualizar clasificadores con nuevas imágenes, o añadir más clasificadores de ejemplos positivos o negativos a un clasificador ya entrenado. Al facilitar más imágenes de ejemplo para que Watson aprenda, el servicio puede mejorar la precisión de los clasificadores de los usuarios. Los clasificadores personalizados pueden ahora aprender a lo largo del tiempo, mejorando continuamente en la comprensión de información visual.

- **Problemas conocidos**

    **ARREGLADO 13-04-2017**: los usuarios pueden recibir un código de error 500 pasados 30 o 90 segundos al actualizar un clasificador. A pesar del error, es bastante probable que la solicitud de reentrenamiento se realice correctamente. Espere al menos 2 minutos y luego compruebe el estado del clasificador mediante el método `GET classifiers/{classifier\_id}`. Si el estado es "ready" y la indicación de fecha y hora "retrained" se ha actualizado, la solicitud de reentrenamiento que ha generado el código 500 se ha realizado correctamente. De lo contrario, si la indicación de fecha y hora "retrained" no se ha actualizado, hay una explicación añadida a la respuesta que dice por qué ha fallado el reentrenamiento, y el servicio devuelve el clasificador a la versión anterior a la solicitud de reentrenamiento.

### 20 de mayo de 2016
{: #20 may 2016}

Este es el release de disponibilidad general del servicio {{site.data.keyword.visualrecognitionshort}}. Este release presenta la versión 3 del servicio y es un cambio de última hora. Este release incorpora la funcionalidad del servicio AlchemyVision, que ha quedado en desuso.

Cualquier clasificador personalizado que se haya creado mientras el servicio estaba en versión beta se debe volver a crear en una instancia de GA del servicio.

Se han realizado los siguientes cambios y actualizaciones en el servicio {{site.data.keyword.visualrecognitionshort}}:

- **Fecha de versión:** para utilizar las características de este release, utilice `2016-05-20` como valor del parámetro `version`.
- **Clases y clasificadores:** los clasificadores individuales ahora se llaman "clases". En GA, un grupo de clases se denomina "clasificador".
- **Clasificación:** utilice los métodos `POST` o `GET /v3/classify` para identificar de forma rápida y precisa una variedad de temas y escenas con clases predeterminadas.
- **Detección de caras:** utilice los métodos `POST` o `GET /v3/detect_faces` para detectar caras en imágenes y obtener información sobre ellas, como la ubicación de la cara en la imagen y el rango de edad estimado para cada cara. El servicio también puede identificar a muchos personajes famosos por nombre, y puede proporcionar un gráfico de conocimiento para poder agregar conceptos interesantes de nivel superior.
- **Clasificadores personalizados polifacéticos:** ahora puede crear y entrenar a clasificadores muy especializados definidos por varias clases. Por ejemplo, puede crear un clasificador "new\_red\_car" que se defina mediante las clases "new\_cars" y "red\_cars". Para obtener más información sobre cómo crear clasificadores polifacéticos, consulte [Estructura de los datos de entrenamiento](/docs/services/visual-recognition/customizing.html#structure).
- **Entrenamiento asíncrono:** el entrenamiento de los clasificadores ahora es asíncrono, de modo que las llamadas de entrenamiento se realizan rápidamente mientras el clasificador personalizado sigue aprendiendo en segundo plano. Para comprobar el estado del entrenamiento del clasificador y saber cuándo estará disponible para su uso, llame al método `GET /v3/classifiers/{classifier_id}` y compruebe el parámetro de respuesta `status`.

### 2 de diciembre de 2015
{: #2december2015}

El release más reciente del servicio {{site.data.keyword.visualrecognitionshort}} es un cambio de última hora que introduce una nueva versión de la API de {{site.data.keyword.visualrecognitionshort}} (v2). La versión 1 del servicio {{site.data.keyword.visualrecognitionshort}} está disponible para su uso hasta que el servicio finalice la fase beta.

Para empezar a utilizar inmediatamente la versión 2 de la API, debe conocer y actualizar el código para reflejar estos cambios:

- En la versión 1 del servicio, se analizaban las imágenes por etiquetas. En la versión 2 del servicio, las etiquetas se denominan **clasificadores**. Los clasificadores tienen un ID de clasificador exclusivo indicado por el parámetro `classifier_id` y un nombre abreviado indicado por el parámetro `name`.
- El método `POST /v1/recognize` para analizar una imagen ahora es el método [`POST /v2/classify` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}. El parámetro `labels_to_check` se ha renombrado a `classifier_ids`.
- El método `GET /v1/tag/labels` para recuperar una lista de etiquetas en V1 es ahora el método [`GET /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} para recuperar una lista de clasificadores.
- Además de recuperar una lista de clasificadores, también puede recuperar los detalles de un clasificador específico con el nuevo método [`GET /v2/classifiers/{classifier_id}` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window}.
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta le permite crear clasificadores personalizados con el nuevo método [`POST /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window}. Para obtener más información sobre cómo crear clasificadores personalizados, consulte [Creación de clasificadores personalizados](/docs/services/visual-recognition/customizing.html).
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta también le permite suprimir clasificadores personalizados con el nuevo método [`DELETE /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window}.
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta requiere el parámetro `version`. Especifique la fecha de release de la versión de la API que desea utilizar en formato `MM-DD-AAAA`.
