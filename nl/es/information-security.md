---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# Seguridad de la información
{: #information-security}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos.
{: shortdesc}

**Aviso:**
Los clientes son responsables de garantizar su propio cumplimiento con diversas leyes y reglamentos, incluido el Reglamento General de Protección de Datos de la Unión Europea. Los clientes son los únicos responsables de obtener asesoramiento legal competente referente a la identificación y la interpretación de cualquier ley relevante que pudiera afectar a su negocio, así como cualquier medida que debieran tomar para cumplir con dichas leyes y normativas.

Los productos, los servicios y otras prestaciones descritas en este documento no son adecuados para todas las situaciones de los clientes y su disponibilidad puede estar restringida. IBM no proporciona recomendaciones legales, contables o de auditoría ni garantiza que sus servicios o productos garantizarán que los clientes cumplan ninguna legislación o normativa.
Si tiene que solicitar soporte de GDPR para los recursos de {{site.data.keyword.cloud}} {{site.data.keyword.watson}} que se crean

- En la Unión Europea, consulte [Solicitud de soporte para los recursos de IBM Cloud Watson creados en la Unión Europea](/docs/services/watson?topic=watson-gdpr-sar#request-EU).
- Fuera de la Unión Europea, consulte [Solicitud de soporte para recursos fuera de la Unión Europea](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU).

## Reglamento General de Protección de Datos de la Unión Europea (GDPR)
{: #gdpr}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos para ayudarles a cumplir con el GDPR.

Obtenga más información sobre la implantación del GDPR en IBM y las prestaciones y las ofertas de GDPR para ayudarle a cumplirlo [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/gdpr){: new_window}.

## Cómo etiquetar y suprimir datos en {{site.data.keyword.visualrecognitionshort}}
{: #gdpr-visrec}

### Migración de seguridad de GDPR
{: #gdpr-visrec-update}

- Todas las instancias del servicio {{site.data.keyword.visualrecognitionfull}} creadas antes del **22 de mayo de 2018** no resultan adecuadas para clientes que deban cumplir con el Reglamento general de protección de datos (GDPR) 2016/679 de la Unión Europea.
- Los clientes que estén sujetos a GDPR tienen que [migrar a la instancia del servicio {{site.data.keyword.visualrecognitionshort}}](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) disponible el **22 de mayo de 2018** y adoptar el nuevo acuerdo para el servicio {{site.data.keyword.visualrecognitionshort}}.
- Los clientes deben suministrar un nuevo servicio {{site.data.keyword.visualrecognitionshort}} y generar *nuevas claves de autenticación* para poder utilizar el nuevo servicio {{site.data.keyword.visualrecognitionshort}}.
- Si un cliente no suministra el nuevo servicio {{site.data.keyword.visualrecognitionshort}}, confirma que IBM no está procesando datos personales en nombre del cliente sujeto a GDPR.
- Se suprimirán los datos de los clientes que no migren al nuevo servicio {{site.data.keyword.visualrecognitionshort}} entre el 22 de mayo de 2018 y el 1 de octubre de 2018.

### Etiquetado de datos

Si tiene que eliminar datos de un cliente individual de una instancia del servicio {{site.data.keyword.visualrecognitionshort}} con varios clientes, primero debe asociar dichos datos a un ID de cliente exclusivo para cada individuo que pueda haber suministrado datos.

Para especificar el ID de cliente para los datos que se envían con el método **Crear un clasificador**, incluya la propiedad **X-Watson-Metadata: customer_id** en la cabecera de la solicitud. En el siguiente ejemplo se asocia el ID de cliente `my_ID` a una solicitud:

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

Se da soporte a caracteres de varios bytes para la serie de ID de cliente. Los caracteres deben estar codificados en URL, tanto en la cabecera durante el entrenamiento como en el parámetro de consulta durante la supresión. El ID puede contener caracteres alfanuméricos y el signo de subrayado (``_``). Estos caracteres no reciben soporte: ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + espacio``.

Usted es el responsable de crear valores de ID de cliente y de asegurarse de que cada uno sea exclusivo.
{: important}

### Supresión de datos etiquetados

Para suprimir todos los datos que están asociados a un ID de cliente, utilice el método **Suprimir datos etiquetados**. Debe pasar la serie `customer_id={id}` como parámetro de consulta con la solicitud. En el ejemplo siguiente se suprimen todos los datos correspondientes al ID de cliente `my_ID`:

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

El método **Suprimir datos etiquetados** suprime todos los datos asociados al ID de cliente especificado, independientemente del método por el que se ha añadido la información. El método no tiene ningún efecto si no hay datos asociados al ID de cliente.

Las solicitudes de supresión se procesan en lotes y pueden tardar hasta 24 horas en completarse.
{: tip}

### Soporte
{: #gdpr-visrec-support}

Pregunte directamente al representante de su cuenta o bien póngase en contacto directamente en [https://ibm.biz/ibmcloudsupport ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/ibmcloudsupport){: new_window}.
