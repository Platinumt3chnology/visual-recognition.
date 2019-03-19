---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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

# Migración
{: #migrating}

Para migrar los modelos actuales (clasificadores), suministre una nueva instancia del servicio {{site.data.keyword.visualrecognitionshort}}. Para los modelos personalizados, vuelva a entrenar el modelo creando otro modelo (clasificador) con las imágenes del modelo anterior.
{: shortdesc}

Las instancias del servicio {{site.data.keyword.visualrecognitionfull}} creadas **antes** del 23 de mayo de 2018 tienen el URL de host `gateway-a.watsonplatform.net`. Debe migrar dichas instancias a una nueva instancia del servicio {{site.data.keyword.visualrecognitionshort}} para poder seguir utilizándolas.
{: deprecated}

1.  Cree otra instancia del servicio {{site.data.keyword.visualrecognitionshort}}:
    1.  Vaya a la página [{{site.data.keyword.visualrecognitionshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/visual-recognition){: new_window} del catálogo.
    1.  Seleccione un plan y pulse **Crear**.
1.  Copie las nuevas credenciales para autenticarse en la instancia de servicio:
    1.  En la página **Gestionar**, pulse **Mostrar credenciales**.
    1.  Copie el valor de `Clave de API`.
1.  [Vuelva a crear y a entrenar los modelos personalizados](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) en la nueva instancia del servicio {{site.data.keyword.visualrecognitionshort}}.
1.  Modifique la forma en que llama al servicio.

    Puede proporcionar una clave de Identity and Access Management (IAM) o una señal de acceso para la instancia de servicio. Las señales proporcionan una mayor seguridad porque deben renovarse periódicamente y dan soporte a solicitudes sin que tenga que incluir credenciales de servicio en cada llamada. Las claves de API utilizan la autenticación básica y no caducan.

    - Para obtener más información sobre las señales, consulte [Autenticación con señales IAM](/docs/services/watson?topic=watson-iam#iam).
    - Para obtener más información sobre cómo utilizar una clave de API de IAM, revise la [Consulta de API](https://{DomainName}/apidocs/visual-recognition/#authentication).
