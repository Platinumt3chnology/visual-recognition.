---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

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

# Notas del release
{: #release-notes}

Están disponibles las siguientes nuevas características y cambios en el servicio.
{: shortdesc}

## Control de versiones de la API del servicio
{: version}

Las solicitudes de API requieren un parámetro de versión que adopta una fecha en el formato `version=AAAA-MM-DD`. Siempre que modificamos la API de forma que sea incompatible con versiones anteriores, ponemos a su disposición una versión menor de la API.

Envíe el parámetro version con cada solicitud de API. El servicio utiliza la versión de la API correspondiente a la fecha que especifique o la versión más reciente anterior a dicha fecha. No especifique como valor predeterminado la fecha actual. Especifique en su lugar una fecha que coincida con una versión que sea compatible con su app y no la modifique hasta que la app esté lista para una versión posterior.

La versión actual es `2018-03-19`.

## Características beta
{: #beta}

{{site.data.keyword.IBM_notm}} publica servicios, características y soporte de idioma clasificados como beta, para evaluarlos. Estas características pueden ser inestables, pueden cambiar con frecuencia y pueden dejar de recibir soporte tras un aviso con poca antelación. Las características beta también pueden no proporcionar el mismo nivel de rendimiento o compatibilidad que proporcionan las características con disponibilidad general, y no están pensadas para su uso en un entorno de producción. Las características beta solo reciben soporte en [IBM Developer Answers ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Cambios
{: #changelog}

Están disponibles las siguientes nuevas características y cambios en el servicio.

### 15 de enero de 2019
{: #15january2019}

- **Traducción para el sexo en el método Detect Faces**
    - Los métodos **Detect Faces** ahora devuelven ahora etiquetas traducidas correspondientes a "Male" y "Female" cuando se proporciona el idioma en la cabecera de la solicitud **Accept-Language**. Para obtener más información, examine la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}.

### 1 de octubre de 2018
{: #01october2018}

- **Las instancias de servicio creadas antes del 23 de mayo de 2018 se suprimen.**

    - Tal como se ha notificado anteriormente, todas las instancias de {{site.data.keyword.visualrecognitionshort}} creadas antes del 23 de mayo de 2018 han dejado de estar activas. Ahora los datos de las instancias se suprimen. Consulte [Migración](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) para ver detalles sobre cómo pasar a una nueva instancia de servicio.
    - Las instancias de servicio creadas después de esta fecha no se ven afectadas.
    - Si tiene alguna pregunta, póngase en contacto con el [equipo de soporte técnico de IBM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/ibmcloudsupport){: new_window}.

### 1 de agosto de 2018
{: #01august2018}

- **Disponibilidad general de los modelos Food y Explicit**

    Los modelos Food y Explicit han pasado de la versión beta a la de disponibilidad general (GA). El modelo Food reconoce más alimentos y comidas que el modelo General (predeterminado). El modelo Explicit identifica las que pueden considerarse imágenes pornográficas.

    No es necesario ningún cambio de código. Ambos modelos son gratuitos en el plan Lite y cuestan 0,002 $ por imagen en el plan Estándar.

    Para obtener más información, consulte [Actualizaciones de Watson Visual Recognition ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/visrec-price-reduction){: new_window} en el <em>blog de Watson</em>.

### 1 de julio de 2018
{: #01july2018}

- **Nuevos precios para los modelos personalizados**
    - A partir del 1 de Julio de 2018, la clasificación de una imagen con un modelo personalizado cuesta la mitad de la tarifa anterior (ahora el coste es de 0,002 $ por imagen). Para obtener más información y ver otra información importante, consulte [Actualizaciones de Watson Visual Recognition \- Reducción de precios para la clasificación personalizada ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/visrec-price-reduction){: new_window} en el <em>blog de Watson</em>.

### 21 de junio de 2018
{: #21june2018}

- **Soporte de idiomas adicionales**

    - Los métodos **Classify** ahora dan soporte al chino (simplificado y tradicional) y al portugués (de Brasil) en la salida de las clases de modelo `default` (General). Para ver la lista completa de idiomas, consulte [Idiomas admitidos](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).
    - Ahora también se admiten todos los idiomas en las respuestas procedentes de los modelos **Food** y **Explicit**.


### 22 de mayo de 2018
{: #22may2018}

- **Nuevo proceso de autenticación de API**:

    Ahora hay que identificarse con Identity and Access Management (IAM) en un nuevo punto final:

    - Utilice otro URL de punto final para las instancias nuevas. El punto final predeterminado es `https:/gateway.watsonplatform.net/visual-recognition/api/`. Para encontrar el URL correspondiente a su instancia de servicio, consulte las credenciales pulsando la instancia en el {{site.data.keyword.cloud_notm}} [panel de control ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps?watson){: new_window}.
    - Modifique el modo en que se autentica en la API. Puede proporcionar una clave de IAM o una señal de acceso para la instancia de servicio. Consulte el apartado sobre [Migración](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) para ver ejemplos.

    Para las instancias de servicio creadas antes del 23 de mayo de 2018, el proceso de autenticación y el punto final no se han modificado. Se debe autenticar proporcionando el parámetro de consulta `api_key`.

- **Actualizaciones en el plan Lite**

    Los planes Lite creados después del 22 de mayo de 2018 se han modificado:

    - Las instancias nuevas del plan Lite siguen estando disponibles transcurridos 30 días si las utiliza cada mes.
    - Puede crear y volver a entrenar dos modelos personalizados bajo el nuevo plan Lite.
    - Los planes Lite incluyen hasta 1.000 sucesos al mes. Cada imagen que envía para clasificación, detección o entrenamiento constituye un suceso. Descargar un modelo Core ML no cuenta en el límite de sucesos.

    Si sus necesidades exceden el plan Lite, actualice a una cuenta de pago. [Explore  ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} los planes de precios.

- **Seguridad de la información**:

    Hemos actualizado la documentación para que incluya algunos detalles nuevos sobre la privacidad de los datos. Lea los detalles en el apartado sobre [Seguridad de la información](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security).

### 12 de abril de 2018
{: #12april2018}

- **Soporte para volver a entrenar un modelo personalizado en el plan Lite**

    Bajo el plan Lite, ya no tiene que suprimir y crear otro modelo personalizado cuando desee actualizar o volver a entrenar el modelo. Ahora puede actualizar un modelo personalizado, siempre que permanezca bajo los [límites](https://console.bluemix.net/catalog/services/visual-recognition) diarios y mensuales del plan.

    Si necesita tener varios modelos o varias versiones del mismo modelo, actualice desde el plan Lite a una cuenta de pago.

- **Nueva versión menor con soporte para CORS**

    **Versión:** `2018-03-19`

    Ahora damos soporte a las cabeceras CORS (Cross-Origin Resource Sharing) cuando se especifica `version=2018-03-19` en las solicitudes.

### 5 de abril de 2018
{: #5april2018}

- **Solución para el problema de puntuación del modelo Face**

  Se ha restaurado el rango original de la puntuación de edad del modelo Face, que es el comprendido entre 0 y 1. Para obtener más información, consulte la sección [Problemas conocidos](#2april2018) correspondiente al 2 de abril de 2018.

- **Nuevo parámetro form-data**

    Los métodos para **Clasificar imágenes** y para **Detectar caras en imágenes** ahora dan soporte a los nuevos parámetros form-data. La clasificación de imágenes admite los parámetros `url`, `classifier_ids`, `threshold` y `owners`, y la función de detección de caras admite `url`.

    Anteriormente, debía codificar los valores en una serie JSON y pasar los **parámetros** form-data. Puede utilizar el nuevo método para pasar estos valores en parámetros form-data separados en todas las fases del desarrollo de la aplicación. Para obtener detalles, consulte la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### 2 de abril de 2018
{: #2april2018}

- **Disponibilidad general del modelo Face mejorado**

    El modelo actualizado de detección de caras ya está disponible a nivel general (GA).

    Este modelo mejorado utiliza conjuntos de datos de entrenamiento más amplios para aumentar la precisión de la detección facial en cuanto a edad y sexo. Por ejemplo, las predicciones de edad se han mejorado al reducir el rango entre `min` y `max`. El rango de edad fijo de 9 años del modelo anterior se ha sustituido por un rango menor y dinámico. Ahora el rango de edad promedio es de 4,9 años.

    - Cambios en la API

    Otras diferencias entre el modelo Face anterior y el mejorado:
        - El modelo mejorado admite los formatos de imagen .gif y .tif.
        - El modelo mejorado admite tamaños de archivo mayores: hasta 10 MB para archivos de imagen y hasta 100 MB para archivos .zip.
        - El modelo mejorado no incluye la información de `FaceIdentity` en la respuesta. La información de identidad hace referencia a los valores `name` (nombre) de la persona, `score` (puntuación) y `type_hierarchy` del gráfico de conocimiento.

    Para obtener más información sobre la API, examine la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

    - Problemas conocidos

        - Los parámetros de formato no pueden incluir el valor **Content-Type**. Por ejemplo, esta solicitud no analiza el parámetro **url** porque incluye `;type=text/plain`:

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - La puntuación de edad tienen un rango comprendido entre 0 y 0,3. Estamos trabajando para restaurar el rango original, comprendido entre 0 y 1.

    - Punto final beta en desuso

    El punto final beta de `/v3/detect_faces_beta` ha quedado en desuso y no se podrá acceder al mismo después del 17 de mayo de 2018. Asegúrese de que sus solicitudes apunten a `/v3/detect_faces`.

### 20 de marzo de 2018
{: #20march2018}

- **Integración con Apple Core ML**

    Ahora {{site.data.keyword.visualrecognitionshort}} incluye soporte para el formato del modelo Apple Core ML. Puede utilizar una versión Core ML de su modelo {{site.data.keyword.visualrecognitionshort}} en sus apps iOS.

    **Empezar a desarrollar**: para empezar a desarrollar con {{site.data.keyword.visualrecognitionshort}} y Core ML, consulte estos proyectos en GitHub:

    - Clasificar imágenes localmente: [{{site.data.keyword.visualrecognitionshort}} con Core ML ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - Integrar {{site.data.keyword.discoveryfull}} con los resultados: [{{site.data.keyword.visualrecognitionshort}} y Discovery con Core ML ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - Explorar el SDK: [Swift SDK ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **Cambios en la API**

    En la integración se incluyen los siguientes cambios compatibles con versiones anteriores de la API:

    - Un nuevo campo `core_ml_enabled` que indica si un modelo clasificador se puede descargar como un modelo Core ML. El campo se devuelve en la respuesta a llamadas a `GET y POST /v3/classifiers` y a `GET /v3/classifiers/{classifier_id}`.
    - Un nuevo método `GET /v3/classifiers/{classifier_id}/core_ml_model` para descargar el modelo Core ML como archivo .mlmodel.  Puede descargar archivos del modelo Core ML para los modelos personalizados creados después del 19 de marzo.
    - Un nuevo campo `updated` con la fecha del último entreno del modelo. El campo `updated` coincide con el campo `retrained` o con el campo `created`.

    Para obtener más información sobre los campos en la API para Core ML, examine la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}.

- **Nueva herramienta disponible: Watson Studio**

    [Watson Studio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} es el nuevo entorno integrado que incluye una sustitución de la herramienta {{site.data.keyword.visualrecognitionshort}} beta. Watson Studio admite no solo {{site.data.keyword.visualrecognitionshort}}, sino también otros recursos y servicios de {{site.data.keyword.cloud_notm}}. Puede utilizar Watson Studio con todas las instancias y los clasificadores existentes de {{site.data.keyword.visualrecognitionshort}}.

     Watson Studio proporciona un entorno de colaboración en la nube. Con Watson Studio, desarrolladores, expertos en la materia, científicos de datos y otros pueden crear y entrenar {{site.data.keyword.visualrecognitionshort}} y otros modelos de IA. También puede utilizar Watson Studio para acceder a los modelos integrados General y Face.

     Watson Studio también admite Core ML. Puede descargar un archivo del modelo Core ML para el modelo personalizado.

    [Iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} a Watson Studio.

- **Arquitectura de aprendizaje profundo actualizada para modelos personalizados**

    Ahora {{site.data.keyword.visualrecognitionshort}} utiliza una arquitectura de red de aprendizaje profundo más rápida y eficaz para la clasificación. Los modelos actualizados también pueden diferenciar con mayor precisión la clase principal y el resto de las clases. Este enfoque puede hacer que el tiempo de entrenamiento se alargue un poco. La nueva arquitectura se utiliza para entrenar los nuevos modelos personalizados. Si vuelve a entrenar modelos antiguos existentes, se utiliza la arquitectura original.

    En el siguiente ejemplo se muestra la diferencia con la nueva arquitectura:

    ![Arquero con arco y flecha. Foto de Annie Spratt en Unsplash](images/archery.jpg)

    <table>
      <tr>
        <th>Clase y clasificación originales</th>
        <th>Clase y clasificación actualizadas</th>
      </tr>
      <tr>
        <td>Archery</br>0,99 </td>
        <td><strong>archery<strong></br>0,9</td>
      </tr>
      <tr>
        <td>Auto Racing</br>0,996398</td>
        <td><strong>biking</strong></br>0,004</td>
      </tr>
      <tr>
        <td>Biking</br>0,0500174</td>
        <td><strong>fishing</strong></br>0,001</td>
      </tr>
      <tr>
        <td>Fishing</br>0,11029</td>
        <td><strong>golf</strong></br>0,031</td>
      </tr>
      <tr>
        <td>Golf</br>0,0980796</td>
        <td><strong>gymnastics</strong></br>0,029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0,964391</td>
        <td><strong>judo</strong></br>0,021</td>
      </tr>
      <tr>
        <td>Judo</br>0,339119</td>
        <td><strong>racing</strong></br>0,002</td>
      </tr>
      <tr>
        <td>Skating</br>0,0393602</td>
        <td><strong>skating</strong></br>0,061</td>
      </tr>
      <tr>
        <td>Skiing</br>0,0310527</td>
        <td><strong>skiing</strong></br>0,003</td>
      </tr>
      <tr>
        <td>Track and Field</br>0,208147</td>
        <td><strong>track</strong></br>0,035</td>
      </tr>
    </table>

- **Soporte del idioma francés**

    Los métodos **Classify** ahora dan soporte al francés en la salida de las clases del modelo `default`. Para ver la lista completa de idiomas, consulte [Idiomas admitidos](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).

### 23 de febrero de 2018
{: #23february2018}

- **Modelo Face mejorado disponible en beta**

    Hay disponible un modelo de detección de caras actualizado. Este modelo beta utiliza conjuntos de datos de entrenamiento más amplios para mejorar la precisión de la detección facial en cuanto a edad y sexo. Para obtener más información, consulte [Mejora de la precisión del servicio IBM Watson {{site.data.keyword.visualrecognitionshort}}![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} y [Migración de Bias en modelos de IA ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}.

    - Puede ver los resultados del modelo actualizado en la [demostración ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/services/visual-recognition/demo){: new_window} y en la versión beta de la [herramienta de reconocimiento visual ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}.
    - El modelo beta está disponible en `/v3/detect_faces_beta`.

    Diferencias entre los modelos beta y de disponibilidad general (GA):
    - El modelo beta admite los formatos de imagen .gif y .tif; se espera que esta mejora se aplique al modelo GA.
    - El modelo beta admite tamaños de archivo mayores: hasta 10 MB para archivos de imagen y hasta 100 MB para archivos .zip. Se espera que esta mejora se aplique al modelo GA.
    - La detección facial del modelo beta no incluye la información de `FaceIdentity` en la respuesta.
    - La solicitud POST del modelo beta necesita un nombre de archivo que no esté vacío. El modelo Face de la versión GA no impone esta restricción.
    - La solicitud POST del modelo beta da soporte a un parámetro de formato distinto llamado `url`. El modelo GA incluye esta información en el objeto JSON `parameters`. Para obtener más información, consulte el [Explorador de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-api-explorer.mybluemix){: new_window}.

- **Identidad en Face en desuso**

    La información de identidad en la respuesta del modelo Face de GA está en desuso y se eliminará de la API el **2 de abril de 2018.** La información de identidad hace referencia a los valores `name` (nombre) de la persona, `score` (puntuación) y `type_hierarchy` del gráfico de conocimiento.

### 16 de enero de 2018
{: #16january2018}

- **La cuenta y el plan Lite sustituyen al plan Gratuito**

    Una cuenta Lite es gratuita; no se requiere tarjeta de crédito. Sin embargo, las instancias de servicio de plan Lite se suprimen transcurridos 30 días.

    El número máximo de llamadas de API que puede realizar con el plan Lite es ligeramente distinto del que permite el plan gratuito. Puede realizar un máximo de 7.500 llamadas de API al mes a 250 llamadas al día en el plan Lite.

    Para actualizar a una cuenta de pago cuando tiene clasificadores personalizados, cree otra instancia de servicio y vuelva a crear los clasificadores personalizados.

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
      <img src="images/tree-flower.jpg" alt="Foto de planta de azaleas">
      <table>
        <tr>
          <th>Etiquetas originales</th>
          <th>Etiquetas adicionales</th>
        </tr>
        <tr>
          <td></td>
          <td>
          Etiqueta: tree<br/>
          Puntuación: 0,799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Etiqueta: flower<br/>
          Puntuación: 0,792</td>
        </tr>
        <tr>
          <td>
          Etiqueta: alpine azalea<br/>
          Puntuación: 0,696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Etiqueta: plant<br/>
          Puntuación: 0,868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Etiqueta: azalea<br/>
          Puntuación: 0,617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            Etiqueta: swamp azalea<br/>
          Puntuación: 0,5</td>
          </td>
          <td></td>
        <tr>
          <td>
            Etiqueta: reddish orange color<br/>
          Puntuación: 0,1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nuevo modelo explícito disponible en beta</strong>
      <p>
        El modelo Explicit, que se inicia en beta, clasifica si una imagen incluye contenido pornográfico y no es apropiada para el uso general. Puede incluir el modelo Explicit con otros modelos para un análisis combinado. Por ejemplo, incluya los ID de clasificador `default` y `explicit` en la solicitud para devolver etiquetas de imagen y saber si la imagen incluye contenido explícito.
      <p>
        Para ver detalles sobre la llamada de API, consulte el método para **Clasificar imágenes** en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
      </p>
    </li>
    <li>
      <strong>Soporte para tamaños de archivo grandes</strong>
      <p>
        El método para <strong>Clasificar imágenes</strong> ahora admite archivos de imagen de hasta 10 MB y archivos .zip de hasta 100 MB.
    </li>
    <li>
      <strong>Matriz necesaria al pasar ID de clasificador</strong>
      <p>
        La API ahora impone una matriz cuando se pasan `classifier_ids` como parte del objeto **parameters** en el método para **Clasificar imágenes**. Anteriormente, se podía pasar un ID de clasificador como una serie. Para obtener más información, consulte el archivo de ejemplo y la descripción de parámetros en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
      </p>
    </li>
</ul>

### 8 de septiembre de 2017
{: #8september2017}

- **La versión beta de las recopilaciones y la búsqueda de similitud ha finalizado**: a partir del 8 de septiembre de 2017, ha finalizado el periodo de la versión beta de la búsqueda de similitud. Para obtener más información, consulte [API de Visual Recognition: actualización de búsqueda de similitud ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30 de junio de 2017
{: #30june2017}

- **Mejora de etiquetas**: hemos aumentado el número de imágenes de entrenamiento para el clasificador predeterminado. Gracias a ese aumento, mejora la capacidad de reconocer con exactitud la escena general de una imagen. Para obtener detalles, consulte [Más mejoras de la función de etiquetado general ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **Otros idiomas**: el método para **Clasificar imágenes** ahora admite coreano, italiano y alemán, además de inglés, árabe, español y japonés.

    Para obtener más información sobre la llamada a la API, consulte el método **Clasificar una imagen** en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

### 16 de mayo de 2017
{: #16may2017}

- **Está disponible el nuevo clasificador de alimentos: Beta**

    Un nuevo modelo beta de reconocimiento de alimentos proporciona una mayor precisión y exactitud de las imágenes de alimentos. El método **Clasificar una imagen** permite añadir este nuevo clasificador, "food", al parámetro `classifier_ids`.

### 5 de abril de 2017
{: #5april2017}

- **Nueva {{site.data.keyword.visualrecognitionshort}} herramienta disponible: Beta**

    Hay disponible una nueva característica beta, la herramienta {{site.data.keyword.visualrecognitionshort}}, en [https://watson-visual-recognition.ng.bluemix.net/ ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Esta herramienta le facilita el trabajo con el servicio {{site.data.keyword.visualrecognitionshort}}. Al entrar la clave de API de {{site.data.keyword.cloud_notm}}, puede utilizar una GUI para acceder a las funciones de etiquetado general y detección de caras, y para crear, reentrenar y suprimir fácilmente clasificadores personalizados asociados con la clave de API, sin necesidad de utilizar código.

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

    {{site.data.keyword.IBM_notm}} ha bajado el precio de los clasificadores personalizados en el servicio de {{site.data.keyword.visualrecognitionshort}} y ha aumentado los disponibles en el plan gratuito. Para obtener más información, consulte la [página de precios de {{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 de octubre de 2016
{: #7october2016}

- **Mejoras de detección de caras**

    El servicio tiene un nuevo algoritmo de detección de caras que mejora las respuestas de los métodos `GET` y `POST /v3/detect_faces`. El servicio ha ajustado el filtrado de detecciones faciales de edad, nombre y género de poca fiabilidad. Como resultado, se encuentran más caras y se devuelve un rango mayor de fiabilidad.

### 8 de septiembre de 2016
{: #8september2016}

- **Búsqueda de similitud BETA**

    Los usuarios ahora pueden subir su propia colección de imágenes y utilizar una imagen para buscar imágenes similares en dicha colección, y el servicio devuelve los 100 imágenes más similares. La búsqueda de similitud se puede utilizar para cualquier propósito, y los usuarios pueden entrenar al servicio de forma personalizada con colecciones de hasta 1 millón de imágenes cada una. Para obtener más información sobre el uso de la nueva funcionalidad de búsqueda de similitud, consulte las páginas de la [Guía de aprendizaje](/docs/services/visual-recognition/tutorial-collections.html) y la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Ha finalizado la versión beta del reconocimiento de texto**

    Los métodos `POST` y `GET /v3/recognize_text` han finalizado su versión beta. {{site.data.keyword.IBM_notm}} espera seguir dando soporte para los clientes BETA que utilizan el servicio, pero no tiene planeado abrir otra versión beta.

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
- **Detección de caras:** utilice los métodos `POST` o `GET /v3/detect_faces` para detectar caras en imágenes y obtener información sobre ellas, como la ubicación de la cara en la imagen y el sexo y el rango de edad estimados de cada cara. El servicio también puede identificar a muchos personajes famosos por nombre, y puede proporcionar un gráfico de conocimiento para poder agregar conceptos interesantes de nivel general.
- **Clasificadores personalizados polifacéticos:** ahora puede crear y entrenar a clasificadores muy especializados definidos por varias clases. Por ejemplo, puede crear un clasificador "new\_red\_car" que se defina mediante las clases "new\_cars" y "red\_cars". Para obtener más información sobre cómo crear clasificadores polifacéticos, consulte [Estructura de los datos de entrenamiento](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure).
- **Entrenamiento asíncrono:** el entrenamiento de los clasificadores ahora es asíncrono, de modo que las llamadas de entrenamiento se realizan rápidamente mientras el clasificador personalizado sigue aprendiendo en segundo plano. Para comprobar el estado del entrenamiento del clasificador y saber cuándo estará disponible para su uso, llame al método `GET /v3/classifiers/{classifier_id}` y compruebe el parámetro de respuesta `status`.

### 2 de diciembre de 2015
{: #2december2015}

El release más reciente del servicio {{site.data.keyword.visualrecognitionshort}} es un cambio de última hora que introduce una nueva versión de la API de {{site.data.keyword.visualrecognitionshort}} (v2). La versión 1 del servicio {{site.data.keyword.visualrecognitionshort}} está disponible para su uso hasta que el servicio finalice la fase beta.

Para empezar a utilizar inmediatamente la versión 2 de la API, debe conocer y actualizar el código para reflejar estos cambios:

- En la versión 1 del servicio, se analizaban las imágenes por etiquetas. En la versión 2 del servicio, las etiquetas se denominan **clasificadores**. Los clasificadores tienen un ID de clasificador exclusivo indicado por el parámetro `classifier_id` y un nombre abreviado indicado por el parámetro `name`.
- El método `POST /v1/recognize` para analizar una imagen ahora es el método [`POST /v2/classify` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window}. El parámetro `labels_to_check` se ha renombrado a `classifier_ids`.
- El método `GET /v1/tag/labels` para recuperar una lista de etiquetas en V1 es ahora el método [`GET /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} para recuperar una lista de clasificadores.
- Además de recuperar una lista de clasificadores, también puede recuperar los detalles de un clasificador específico con el nuevo método [`GET /v2/classifiers/{classifier_id}` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window}.
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta le permite crear clasificadores personalizados con el nuevo método [`POST /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window}. Para obtener más información sobre cómo crear clasificadores personalizados, consulte [Creación de clasificadores personalizados](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta también le permite suprimir clasificadores personalizados con el nuevo método [`DELETE /v2/classifiers` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window}.
- La versión 2 de la API de {{site.data.keyword.visualrecognitionshort}} beta requiere el parámetro `version`. Especifique la fecha de release de la versión de la API que desea utilizar en formato `MM-DD-AAAA`.
