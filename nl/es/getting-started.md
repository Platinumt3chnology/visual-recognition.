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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Guía de aprendizaje de iniciación

Esta guía de aprendizaje le explica cómo utilizar algunos de los clasificadores incorporados en {{site.data.keyword.visualrecognitionfull}} para clasificar una imagen y luego detectar caras en una imagen.
{: shortdesc}

## Antes de empezar
{: #prerequisites}

- Cree una instancia del servicio:
    - {: download} Si está viendo esto, ha creado la instancia de servicio. Ahora, obtenga las credenciales.
    - Cree un proyecto a partir de un servicio:
        1.  Vaya a la página [Servicios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/developer/watson/services){: new_window} de la consola del desarrollador de {{site.data.keyword.watson}}.
        1.  Seleccione {{site.data.keyword.visualrecognitionshort}}, pulse **Añadir servicios** y regístrese para obtener una cuenta gratuita de {{site.data.keyword.Bluemix_notm}} o inicie sesión.
        1.  Escriba `vision-tutorial` como nombre de proyecto y pulse **Crear proyecto**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    - {: download} Desde el panel de control del servicio (lo que está viendo):
        1.  Pulse el separador **Credenciales de servicio**.
        1.  Pulse **Ver credenciales** en **Acciones**.
        1.  Copie el valor de api-key.
        {: download}
    - Desde el proyecto **vision-tutorial** en la consola del desarrollador, copie el valor `api-key` de `"visual_recognition"` de la sección **Credenciales**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si utiliza {{site.data.keyword.Bluemix_dedicated_notm}}, cree la instancia de servicio desde la página de [{{site.data.keyword.visualrecognitionshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} en el catálogo. Para obtener información sobre cómo obtener sus credenciales de servicio, consulte [Credenciales de servicio para servicios de Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Paso 1: Clasificar una imagen
{: #classify}

1.  Descargue la imagen de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Emita el siguiente mandato para cargar la imagen y clasificarla contra todos los clasificadores incorporados:
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado anteriormente.
    - Modifique la ubicación de images\_file para que apunte adonde ha guardado la imagen.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Si tiene {{site.data.keyword.Bluemix_notm}} dedicado, el punto final `gateway-a.watsonplatform.net` podría no ser el punto final de servicio. Compruebe el `url` en la página **Credenciales de servicio** del panel de control del servicio.
    {: tip}

    La respuesta incluye el modelo o clasificador general (que utiliza el id de clasificador `default`), las clases identificadas en la imagen y una puntuación para cada clase.

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    Las puntuaciones de confianza oscilan entre 0 y 1; una puntuación mayor indica una mayor correlación. De forma predeterminada, las llamadas de `/v3/classify` no incluyen clases con una puntuación inferior a `0,5`.

## Paso 2: Detectar caras en una imagen
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} puede detectar caras en imágenes. La respuesta proporciona información como, por ejemplo, la ubicación de la cara en la imagen y el rango de edad estimado para cada cara.

El servicio también puede identificar a muchos personajes famosos por nombre, y puede proporcionar un *gráfico de conocimiento* para poder agregar conceptos de nivel superior.

1.  Descargue la imagen de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Emita el siguiente mandato en el método `POST /v3/detect_faces` para cargar y analizar la imagen. Si utiliza su propia imagen, el tamaño máximo es 2 MB:
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado anteriormente.
    - Modifique la ubicación de images\_file para que apunte adonde ha guardado la imagen.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    La respuesta incluye una ubicación, la edad estimada, el género, la identidad y la jerarquía de tipo (si el servicio reconoce la cara), y una puntuación para cada uno.

    Las puntuaciones oscilan entre 0-1; una puntuación mayor indica una mayor correlación. Se reconocen todas las caras, pero para las imágenes con más de 10 caras, las puntuaciones de confianza de edad y género pueden ser de 0.

    ```json
    {
      "images": [
        {
          "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Próximos pasos

Ya tiene un conocimiento básico de cómo utilizar el clasificador predeterminado incorporado con {{site.data.keyword.visualrecognitionshort}}. Ahora, profundice:

- Obtenga más información sobre cómo [crear un clasificador personalizado](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Consulte información sobre la API en la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Atribuciones
{: #attributions}

- [Cesta de fruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://flic.kr/p/JPHES){: new_window}, por el usuario de Flikr [Ryan Edwards-Crewe ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.flickr.com/photos/ryanec/){: new_window} se ha utilizado bajo [licencia Creative Commons Attribution 2.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No se han realizado cambios en esta imagen.
- [obama ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://bit.ly/1T0DCl9){: new_window}, por el usuario de Flikr [dcblog ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.flickr.com/photos/12863058@N08/){: new_window} se ha utilizado bajo [licencia Creative Commons Attribution 2.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No se han realizado cambios en esta imagen.
