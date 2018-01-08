---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# Migrazione a {{site.data.keyword.visualrecognitionshort}} da {{site.data.keyword.alchemyvisionshort}}

Il 19 maggio 2016, il servizio {{site.data.keyword.alchemyvisionshort}} è diventato obsoleto e le sue funzionalità sono diventate parte di {{site.data.keyword.visualrecognitionshort}} (GA). Per migrare un'applicazione distribuita a {{site.data.keyword.Bluemix_notm}} dal servizio {{site.data.keyword.alchemyvisionshort}} al servizio {{site.data.keyword.visualrecognitionshort}}, aggiorna il tuo codice.
{: shortdesc}

Le seguenti differenze tra {{site.data.keyword.alchemyvisionshort}} e {{site.data.keyword.visualrecognitionshort}} potrebbero influenzare il tuo codice applicazione:

- **Classi e classificatori:** in {{site.data.keyword.alchemyvisionshort}}, le immagini analizzate con etichettate con "tags". In {{site.data.keyword.visualrecognitionshort}}, "tags" sono denominate "classes". I gruppi di classi sono denominati "classifiers". Tutte le tag predefinite di {{site.data.keyword.alchemyvisionshort}} sono ancora disponibili come classi in {{site.data.keyword.visualrecognitionshort}}.
- **Classificatori personalizzati:** {{site.data.keyword.visualrecognitionshort}} ti permette di formare e creare classi e classificatori personalizzati.
- **Input batch:** in {{site.data.keyword.visualrecognitionshort}}, puoi ora classificare i batch di immagini o gli URL dell'immagine inviando i file dell'immagine in un file compresso (.zip) o un solo URL dell'immagine in una stringa JSON.
- **Specifica lingua:** in {{site.data.keyword.alchemyvisionshort}}, specificavi la lingua di una chiamata contrassegnata con tag come un parametro di query. In {{site.data.keyword.visualrecognitionshort}}, specifichi la lingua di una chiamata di classificazione nell'intestazione `Accept-Language`.
- **Endpoint:** la seguente funzionalità {{site.data.keyword.alchemyvisionshort}} è inclusa nei nuovi endpoint nella release GA di {{site.data.keyword.visualrecognitionshort}}:

| Funzionalità| Endpoint {{site.data.keyword.alchemyvisionshort}} (obsoleto) | Endpoint {{site.data.keyword.visualrecognitionshort}} (GA) |
|---------------|--------------------|----------------|
| Contrassegna con tag le immagini con i classificatori integrati | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Rileva volti, intervallo di età e genere. | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Estrai l'immagine principale da HTML o da un URL del sito web | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | Puoi fornire un'immagine dall'URL ai metodi `/v3/classify` e `/v3/detect_faces`, non tramite un endpoint autonomo. |
