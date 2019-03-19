---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition languages,language support,supported languages

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

# Idiomas admitidos
{: #language-support-top}

## Clasificación de imágenes
{: #language-support}

El método para **Clasificar imágenes** de {{site.data.keyword.visualrecognitionfull}} da soporte a los idiomas inglés (`en`), árabe (`ar`), alemán (`de`), español (`es`), francés (`fr`), italiano (`it`), japonés (`ja`), coreano (`ko`), portugués (de Brasil) (`pt-br`), chino (simplificado) (`zh-cn`) y chino (tradicional) (`zh-tw`).

Los idiomas funcionan con las clases de salida de todos los modelos incorporados: `default` (también denominado modelo general), `food` y `explicit`.

Para ver detalles sobre la llamada de API, consulte el método para **Clasificar imágenes** en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

## Detectar caras
{: #detect_faces}

El método **Detectar caras** devuelve la traducción de las palabras inglesas correspondientes a sexo ("Male" y "Female") en la respuesta. Establezca el idioma con la cabecera de solicitud **Accept-Language**.

Para obtener más información, consulte los métodos para **Detectar caras** en la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.
