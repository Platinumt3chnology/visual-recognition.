---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# Reconocimiento de texto en una imagen

{: shortdesc}

## Antes de empezar
{: #copy-credentials}

Utilice las credenciales que ha copiado en la "Guía de aprendizaje de iniciación" para esta guía de aprendizaje. Si no ha creado una instancia de servicio, ejecute estos pasos de la sección [Antes de empezar](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Paso 1: Reconocer texto en una imagen
{: #recognize-text}

1.  Descargue la imagen de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>
1.  Emita el siguiente mandato en el método `POST /v3/recognize_text` para cargar y analizar la imagen. Si utiliza su propia imagen, el tamaño máximo es 2 MB:
    - Sustituya `{api-key}` con las credenciales de servicio que ha copiado anteriormente.
    - Modifique la ubicación de images\_file para que apunte adonde ha guardado la imagen.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    La respuesta incluye una ubicación, la edad estimada, el género, la identidad y la jerarquía de tipo (si el servicio reconoce la cara), y una puntuación para cada uno.

    Las puntuaciones oscilan entre 0-1; una puntuación mayor indica una mayor correlación. Se reconocen todas las caras, pero para las imágenes con más de 10 caras, las puntuaciones de confianza de edad y género pueden ser de 0.


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## Pasos siguientes

Ya tiene un conocimiento básico de cómo utilizar los clasificadores predeterminados con {{site.data.keyword.visualrecognitionshort}}. Ahora, profundice:

- Consulte información sobre la API en la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Atribuciones
{: #attributions}

Todas las imágenes utilizadas en esta página proceden de Flikr y se utilizan bajo [licencia Creative Commons Attribution 2.0 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. No se han realizado cambios en estas imágenes.
