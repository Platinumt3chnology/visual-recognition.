---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# Reconocimiento de texto en escenas naturales

Utilice el modelo de texto beta para detectar y reconocer texto en inglés en las imágenes. El modelo de texto está diseñado para reconocer el texto de escena impreso en imágenes en lugar del texto más denso en documentos.

El modelo de texto es una característica beta y no está pensado para su uso en un entorno de producción. Para obtener más información, consulte "Características beta" en las [Notas del release](/docs/services/visual-recognition/release-notes.html#beta).
{: tip}

El modelo de texto funciona mejor en cadenas de texto cortas. Por ejemplo, un uso común del modelo de texto es leer las señales de tráfico.

![Señal de tráfico con recuadros delimitadores alrededor de las palabras detectadas](images/road-sign-text-detection.png)

![Imagen de palabras y puntuaciones de confianza detectadas en la señal de tráfico](images/road-sign-text-response.png)

Los recuadros blancos ilustran cada palabra que el modelo ha detectado en la imagen.

## La respuesta

La respuesta incluye la cadena detectada, y cada palabra de dicha cadena se identifica con la información siguiente:

- La palabra detectada
- Una puntuación que indica la confianza en la precisión de la palabra detectada.
- La ubicación del recuadro delimitador alrededor de la palabra. El recuadro indica dónde se encuentra la palabra en la imagen.
- Un número de línea donde la palabra se ha detectado.

## Directrices para un buen reconocimiento de texto

El texto en imágenes se reconoce mejor cuando cumple estas directrices:

- El texto es, principalmente, palabras completas, no series de letras como códigos de producto. El modelo reconoce palabras en lugar de caracteres individuales, y podría descartar "palabras" de letras sueltas o números.
- El texto se imprime en una fuente estándar, no en una con mucho estilo. Por ejemplo, el texto de matrículas o carteles de cine podría no ser reconocido. Asimismo, el texto manuscrito puede no ser reconocido.
- El texto ocupa al menos el 5 % de la imagen.
- El texto no se inclina más de 45 grados en horizontal. El modelo de texto beta lee etiquetas EXIF y rota imágenes. Sin embargo, para un mejor rendimiento, envíe imágenes que no sea necesario que gire el servicio (la etiqueta **Orientation** EXIF definida en `1`).
- El modelo de texto está entrenado con palabras en inglés. El texto en otros idiomas seguramente no se reconocerá.

## Próximos pasos

Familiarícese con la API en el [Explorador de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window}

Si tiene preguntas o comentarios sobre el modelo de texto, póngase en contacto con Kevin Gong en kgong@us.ibm.com.

---

Vaya a los [documentos](/docs/services/visual-recognition/index.html) principales.
