---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Creación de un modelo personalizado
{: #tutorial-custom-classifier}

Después de analizar una imagen en la "Guía de aprendizaje de iniciación", está listo para entrenar y crear un modelo personalizado. Con un modelo personalizado, puede entrenar al servicio {{site.data.keyword.visualrecognitionshort}} para que clasifique imágenes para satisfacer sus necesidades de negocio.
{: shortdesc}

## Paso 1: Copiar sus credenciales
{: #copy-credentials}

Utilice las credenciales que ha copiado en la "Guía de aprendizaje de iniciación". Si no ha creado una instancia de servicio, ejecute estos pasos de la sección [Antes de empezar](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites).

## Paso 2: Crear un modelo personalizado
{: #create}

{{site.data.keyword.visualrecognitionshort}} puede aprender a crear un nuevo modelo polifacético a partir de las imágenes de ejemplo que cargue. Cada archivo de ejemplo se entrena contra los demás archivos de la llamada, y los ejemplos positivos se almacenan como clases. Estas clases se agrupan para definir un modelo único y devolver sus propias puntuaciones. Los archivos de ejemplos negativos no se almacenan como clases.

1.  Descargue los archivos de entrenamiento de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a> y <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>.
1.  Llame al método `POST /v3/classifiers` con el siguiente mandato, que carga los datos de entrenamiento y crea el modelo personalizado `dogs`:
    - Sustituya `{your_api_key}` por las credenciales de servicio que ha copiado en el primer paso.
    - Modifique la ubicación de `{class}_positive_examples` para que apunte adonde ha guardado los archivos .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    Los nombres de archivo de ejemplos positivos necesitan el sufijo `_positive_examples`. En este ejemplo, los nombres de archivo son `beagle_positive_examples`, `goldenretriever_positive_examples` y `husky_positive_examples`. El prefijo (beagle, goldenretriever y husky) se devuelve como el nombre de la clase.
    {:tip }

    La respuesta incluye un nuevo ID de clasificador y estado, por ejemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  Compruebe el estado de entrenamiento de forma periódica hasta que vea el estado `ready`. El entrenamiento comienza inmediatamente y debe terminar para poder consultar el modelo. Sustituya `{your_api_key}` y `{classifier_id}` por su información:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Paso 3: Actualizar un modelo personalizado existente
{: #tutorial-custom-classifier-update}

Puede actualizar un modelo personalizado añadiendo clases al modelo o añadiendo imágenes a una clase existente. A continuación, puede mejorar el modelo que ha creado en el paso 2 añadiendo la clase *Dalmatian* a los tipos de perro que se pueden clasificar. Puede también añadir imágenes de gatos al conjunto de ejemplos negativos para el personalizado "dogs".

1.  Descargue los archivos de entrenamiento de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a> y <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>.
1.  Llame al método `POST /v3/classifiers/{classifier_id}` con el siguiente mandato cURL, que carga los datos de entrenamiento y actualiza el modelo "dogs\_1941945966":
    - Sustituya `{your_api_key}` por las credenciales de servicio que ha copiado en el primer paso.
    - Sustituya `{classifier_id}` por el ID del modelo personalizado que desea actualizar.
    - Modifique la ubicación de `{class}_positive_examples` para que apunte adonde ha guardado los archivos .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    El modelo personalizado "dogs" existente se sustituye por el modelo reentrenado con el mismo id de clasificador. La respuesta muestra el nuevo conjunto de clases y el estado actual. Por ejemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    El entrenamiento comienza inmediatamente. Cuando el nuevo está disponible, el estado cambia a `ready`.

    No emita otra solicitud de reentrenamiento hasta que el estado actual sea `ready`. Si se emiten varias solicitudes para reentrenar
un modelo, tiene efecto un solo reentrenamiento. Una indicación de fecha y hora llamada `updated` muestra el momento de la última actualización del modelo. Si llama al método `/classify` mientras se está reentrenando el modelo, se utiliza la definición anterior del modelo.
    {: tip}
1.  Compruebe el estado de entrenamiento de forma periódica hasta que vea el estado `ready`. Sustituya `{your_api_key}` y `{classifier_id}` por su información:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Paso 4: Clasificar una imagen con un modelo personalizado
{: #tutorial-custom-classifier-classify}

Cuando el nuevo modelo esté listo, llámelo para ver cómo actúa.

1.  Descargue <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>.
1.  Utilice el método `POST /v3/classify` para probar el modelo personalizado. El siguiente ejemplo clasifica la imagen `dogs.jpg` frente al modelo personalizado "dogs\_1941945966" y al modelo general integrado `default`:
    - Sustituya `{your_api_key}` por las credenciales de servicio que ha copiado en el primer paso.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    Para clasificar solo frente al modelo general incorporado, omita el parámetro `classifier_ids`.
    {: tip}

    La respuesta incluye clasificadores (modelos), sus clases y una puntuación para cada clase. Las puntuaciones oscilan entre 0-1; una puntuación mayor indica una mayor correlación. Las llamadas de `/v3/classify` omiten las clases de puntuación baja de forma predeterminada, si se identifican clases de puntuación alta. Puede establecer una puntuación mínima que visualizar especificando un valor de coma flotante para el parámetro `threshold` en la llamada.

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  Revise los resultados.

Ya ha acabado. Ha creado, entrenado y consultado un modelo personalizado con {{site.data.keyword.visualrecognitionshort}}.

### Supresión del modelo personalizado
{: #tutorial-custom-classifier-delete}

Puede que desee suprimir el modelo personalizado para empezar a desarrollar la aplicación con una instancia limpia.

Para suprimir el modelo, llame al método `DELETE /v3/classifiers/{classifier_id}`. Sustituya `{your_api_key)` y `classifier_id` por su información:

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## Pasos siguientes
{: #tutorial-custom-classifier-next-steps}

Ahora que tiene un conocimiento básico de cómo utilizar los modelos personalizados, puede profundizar:

- Obtenga más información sobre las [Mejores prácticas para clasificadores personalizados ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Consulte información sobre la API en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Atribuciones
{: #tutorial-custom-classifier-attributions}

Todas las imágenes utilizadas en esta página proceden de Flikr y se utilizan bajo [licencia Creative Commons Attribution 2.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No se han realizado cambios en estas imágenes.
