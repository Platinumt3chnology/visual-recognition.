---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-17"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Reconocimiento de texto en una imagen
{: #tutorial-recognize-text}

En esta guía de aprendizaje se muestra cómo realizar la primera llamada con el modelo de texto beta de {{site.data.keyword.visualrecognitionshort}} para detectar y reconocer texto en inglés en una imagen.
{: shortdesc}

El modelo de texto es una característica beta privada y debe tener el permiso de {{site.data.keyword.IBM_notm}} para realizar llamadas al modelo. [Solicite acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Para obtener más información sobre las características beta, consulte las [Notas del release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Antes de empezar
{: #tutorial-recognize-text-prerequisites}

1.  Vaya a la página [{{site.data.keyword.visualrecognitionshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/visual-recognition){: new_window} en el catálogo de {{site.data.keyword.Bluemix_notm}}.
    1.  Regístrese para obtener una cuenta de {{site.data.keyword.Bluemix_notm}} gratuita o inicie una sesión.
    1.  Pulse **Crear**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    1.  Pulse **Mostrar** para ver sus credenciales.
    1.  Copie el valor de **Clave de API**.

## Paso 1: Reconocer texto en una imagen
{: #tutorial-recognize-text-recognize-text}

1.  Emita la siguiente llamada para reconocer texto en [una imagen ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}. Sustituya `{your_api_key}` por el valor de clave de API que ha copiado antes.

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    La respuesta incluye el texto reconocido y la ubicación de las palabras en el texto con una puntuación de fiabilidad para cada palabra. La información de ubicación se puede utilizar para dibujar los recuadros delimitadores alrededor de las palabras.

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Pasos siguientes

Ya tiene un conocimiento básico de cómo reconocer texto en una imagen. Siga explorando.

- Lea la [visión general](/docs/services/visual-recognition?topic=visual-recognition-recognize-text#recognize-text).
- Explore los métodos del modelo de texto en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Atribuciones
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} de [Lubo Minar ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://unsplash.com/@bubo){: new_window} en [Unsplash ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}.  No se han realizado cambios en esta imagen.
