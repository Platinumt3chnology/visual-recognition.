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

# Creación de un clasificador personalizado

Después de clasificar una imagen en la "Guía de aprendizaje de iniciación", está listo para entrenar y crear un clasificador (o modelo) personalizado. Con un clasificador personalizado, puede entrenar al servicio {{site.data.keyword.visualrecognitionshort}} para clasificar imágenes para satisfacer sus necesidades de negocio.
{: shortdesc}

## Paso 1: Copiar sus credenciales
{: #copy-credentials}

Utilice las credenciales que ha copiado en la "Guía de aprendizaje de iniciación". Si no ha creado una instancia de servicio, ejecute estos pasos de la sección [Antes de empezar](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Paso 2: Creación de un clasificador personalizado
{: #create}

{{site.data.keyword.visualrecognitionshort}} puede aprender a crear un nuevo clasificador polifacético a partir de las imágenes de ejemplo subidas. Cada archivo de ejemplo se entrena contra los demás archivos de la llamada, y los ejemplos positivos se almacenan como clases. Estas clases se agrupan para definir un clasificador único y devolver sus propias puntuaciones. Los archivos de ejemplos negativos no se almacenan como clases.

1.  Descargue los archivos de entrenamiento de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> y <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Llame al método `POST /v3/classifiers` con el siguiente mandato, que sube los datos de entrenamiento y crea un clasificador `dogs`:
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado en el primer paso.
    - Modifique la ubicación de `{class}_positive_examples` para que apunte adonde ha guardado los archivos .zip.

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Los nombres de archivo de ejemplos positivos necesitan el sufijo `_positive_examples`. En este ejemplo, los nombres de archivo son `beagle_positive_examples`, `goldenretriever_positive_examples` y `husky_positive_examples`. El prefijo (beagle, goldenretriever y husky) se devuelve como el nombre de la clase.
    {:tip }

    La respuesta incluye un nuevo ID de clasificador y estado, por ejemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
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
      ]
    }
    ```
    {: codeblock}

1.  Compruebe el estado de entrenamiento de forma periódica hasta que vea el estado `ready`. El entrenamiento comienza inmediatamente y debe terminar antes de poder consultar el clasificador. Sustituya `{api  key}` y `{classifier_id}` con su información:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Paso 3: Actualización de un clasificador personalizado existente

No se puede actualizar un clasificador personalizado con una clave de API gratuita. Si tiene una clave gratuita, puede actualizar a un plan estándar. Para obtener más información, consulte [Cómo cambiar su plan](https://console.bluemix.net/docs/pricing/changing_plan.html).
{: tip}

Puede actualizar un clasificador personalizado añadiendo clases al clasificador o añadiendo imágenes a una clase existente. A continuación, puede mejorar el clasificador que ha creado en el paso 2 añadiendo una clase *Dalmatian* a los tipos de perro que se pueden clasificar. Puede también añadir imágenes de gatos al conjunto de ejemplos negativos para el clasificador de perros.

1.  Descargue los archivos de entrenamiento de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> y <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Llame al método `POST /v3/classifiers/{classifier_id}` con el siguiente mandato cURL, que sube los datos de entrenamiento y actualiza el clasificador "dogs\_1941945966":
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado en el primer paso.
    - Sustituya `{classifier_id}` con el ID del clasificador que desea actualizar.
    - Modifique la ubicación de `{class}_positive_examples` para que apunte adonde ha guardado los archivos .zip.

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    El clasificador actual "dogs" se sustituye por el reentrenado con el mismo id de clasificador. La respuesta muestra el nuevo conjunto de clases y el estado actual. Por ejemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    El entrenamiento comienza inmediatamente. Cuando el nuevo está disponible, el estado cambia a `ready`.

    No emita otra solicitud de reentrenamiento hasta que el estado actual sea `ready`. Varias solicitudes para reentrenar a un clasificador tienen como resultado que solo tiene efecto un reentrenamiento. Una indicación de fecha y hora denominada `retrained` muestra la última vez que se ha realizado el reentrenamiento del clasificador. Si llama al método `/classify` mientras se está reentrenando el clasificador, se utiliza la definición anterior del clasificador.
    {: tip}
1.  Compruebe el estado de entrenamiento de forma periódica hasta que vea el estado `ready`. Sustituya `{api  key}` y `{classifier_id}` con su información:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Paso 4: Clasificación de una imagen con un clasificador personalizado
{: #classify}

Cuando el nuevo clasificador está listo, llámelo para ver cómo actúa.

1.  Cree un archivo JSON denominado `myparams.json` que incluya los parámetros de la llamada, como el `classifier_id` para el nuevo clasificador y el clasificador de modelo general (que utiliza el id de clasificador `default`). Un archivo JSON simple puede tener este aspecto:

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  Descargue <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Utilice el método `POST /v3/classify` para probar el clasificador personalizado. El ejemplo siguiente clasifica la imagen `dogs.jpg` contra el clasificador "dogs\_1941945966":
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado en el primer paso.

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Para clasificar sólo contra el modelo general incorporado, omita el parámetro `parameters`.
    {: tip}

    La respuesta incluye clasificadores, sus clases y una puntuación para cada clase. Las puntuaciones oscilan entre 0-1; una puntuación mayor indica una mayor correlación. Las llamadas de `/v3/classify` omiten las clases de puntuación baja de forma predeterminada, si se identifican clases de puntuación alta. Puede establecer una puntuación mínima que visualizar especificando un valor de coma flotante para el parámetro `threshold` en la llamada.

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  Revise los resultados.

Ya ha acabado. Ha creado, entrenado y consultado un clasificador personalizado con {{site.data.keyword.visualrecognitionshort}}.

### Cómo suprimir el clasificador personalizado

Puede que desee suprimir el clasificador personalizado para empezar a desarrollar la aplicación con una instancia limpia.

Para suprimir el clasificador, llame al método `DELETE /v3/classifiers/{classifier_id}`. Sustituya `{api_key)` y `classifier_id` con su información:

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## Próximos pasos

Ahora que tiene un conocimiento básico de cómo utilizar los clasificadores personalizados, puede profundizar:

- Obtenga más información sobre las [Mejores prácticas para clasificadores personalizados ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Consulte información sobre la API en la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Atribuciones
{: #attributions}

Todas las imágenes utilizadas en esta página proceden de Flikr y se utilizan bajo [licencia Creative Commons Attribution 2.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No se han realizado cambios en estas imágenes.
