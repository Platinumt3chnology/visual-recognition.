---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

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

<!-- Link definitions -->

[api-ref-text]: https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text

# Reconocimiento de texto en escenarios naturales (Beta)
{: #recognize-text}

Utilice el modelo de texto beta de {{site.data.keyword.visualrecognitionshort}} para detectar y reconocer texto en inglés en imágenes. El modelo de texto está diseñado para reconocer texto de escenas en imágenes, no el texto más denso que suele aparecer en los documentos.

El modelo de texto es una característica beta privada y debe tener el permiso de {{site.data.keyword.IBM_notm}} para realizar llamadas al modelo. [Solicite acceso ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Para obtener más información sobre las características beta, consulte las [Notas del release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

El modelo de texto funciona mejor en cadenas de texto cortas. Por ejemplo, un uso común del modelo de texto es leer señales de tráfico.

![Señal de tráfico con recuadros delimitadores alrededor de las palabras reconocidas. Foto de Ashim D’Silva en Unsplash](images/walk-signal-detection.png) ![Palabras y niveles de fiabilidad detectados en la imagen de señales de tráfico](images/walk-signal-response.png)

Los recuadros blancos ilustran cada palabra que el modelo reconoce en la imagen.

## La respuesta
{: #recognize-text-response}

La respuesta incluye la cadena detectada, y cada palabra de dicha cadena se identifica con la información siguiente:

- La palabra reconocida.
- Una puntuación que indica el grado de fiabilidad del reconocimiento de la palabra.
- La ubicación del recuadro delimitador alrededor de la palabra. El recuadro indica dónde se encuentra la palabra en la imagen.
- Un número de línea donde la palabra se ha detectado.

## Directrices para un buen reconocimiento de texto
{: #recognize-text-guidelines}

El texto en imágenes se reconoce mejor cuando cumple estas directrices:

- El texto es, principalmente, palabras completas, no series de letras como códigos de producto. El modelo reconoce palabras en lugar de caracteres individuales, y podría descartar "palabras" de una sola letra o números.
- El texto se imprime en una fuente estándar, no en una con mucho estilo. Por ejemplo, el texto de matrículas o carteles de cine podría no ser reconocido. Asimismo, el texto manuscrito puede no ser reconocido.
- El modelo de texto está entrenado principalmente con palabras en inglés. Es poco probable que se reconozca texto en otros idiomas.

## Pasos siguientes
{: #recognize-text-next-steps}

- [Realice una llamada](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text) para reconocer texto en una imagen.
- Familiarícese con la API en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window}.
