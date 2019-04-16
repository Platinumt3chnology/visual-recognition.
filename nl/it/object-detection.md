---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

keywords: custom object detection,object detection,bounding boxes,visual inspection
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

# Custom Object Detection (Beta)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} Custom Object Detection (Beta) identifica gli elementi e la loro posizione in un'immagine. Il servizio rileva questi elementi sulla base di una serie di immagini con i dati di formazione etichettati da te forniti.
{: shortdesc}

Custom Object Detection è una funzione beta privata e devi avere l'autorizzazione da {{site.data.keyword.IBM_notm}} per effettuare le chiamate al modello. [Richiedi l'accesso ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}. Per ulteriori informazioni sulle funzioni beta, vedi le [Note sulla release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Formi il modello di rilevamento degli oggetti per riconoscere gli oggetti importanti per il tuo flusso di lavoro o il tuo dominio. Degli esempi possono essere il rilevamento di danni a un'autovettura, la ricerca di macchine che hanno bisogno di manutenzione o l'esecuzione di ispezioni visive sul campo. Puoi anche utilizzare il rilevamento degli oggetti per contare gli oggetti o gestire l'inventario.

## Confronto tra rilevamento e classificazione degli oggetti
{: #obj-detect-comparison}

Il modello Custom Object Detection è la funzione più recente nel servizio {{site.data.keyword.visualrecognitionshort}}, che include la classificazione.

La classificazione e il rilevamento degli oggetti sono simili ma hanno usi diversi. In generale, se desideri prevedere l'esistenza di oggetti in un'immagine, utilizza la classificazione. Se vuoi individuare o contare gli oggetti in un'immagine, usa il rilevamento degli oggetti.

### Classificazione
{: #obj-detect-classify}

Quando classifichi un'immagine, il servizio risponde con la probabilità che specifici oggetti siano in quell'immagine. Puoi utilizzare i modelli integrati (General, Food o Explicit) oppure puoi creare un tuo modello personalizzato.

Ad esempio, quando classifichi un'immagine di cookie, come ad esempio la seguente immagine, il servizio prevede che ci sono cookie nell'immagine con un'attendibilità del 95% .

![Immagine della risposta di classificazione](images/cookies-tag.png "Un'immagine per mostrare la classificazione")

### Rilevamento degli oggetti
{: #obj-detect-detect}

Custom Object Detection è simile alla classificazione personalizzata, ma il servizio identifica l'ubicazione degli elementi nell'immagine. Analogamente alla classificazione, la risposta include anche l'etichetta di ciascun elemento che ha rilevato e l'attendibilità per quanto riguarda la sua identificazione.

Gli articoli rilevati sono basati sulle informazioni che fornisci quando formi un modello di rilevamento degli oggetti.

Nella seguente immagine, il metodo **Analyze images** di Custom Object Detection identifica l'ubicazione dei cookie nell'immagine. Ogni oggetto rilevato include l'etichetta (in questo caso, `Cookie`) con la sua ubicazione e un punteggio di attendibilità.

![Immagine della risposta di rilevamento degli oggetti](images/cookies-bbox.png "Un'immagine per mostrare il rilevamento degli oggetti")

## Come utilizzare Custom Object Detection
{: #object-detection-sequence}

Per utilizzare {{site.data.keyword.visualrecognitionshort}} Custom Object Detection, attieniti a questa sequenza di passi per configurare un modello di rilevamento degli oggetti personalizzato:

1.  Crea una raccolta: una raccolta è un contenitore per le tue immagini e i tuoi dati di formazione. Vedi [Create a collection ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} nella guida di riferimento API v4.
1.  Aggiungi le tue immagini alla raccolta. Puoi aggiungere singole immagini in base all'URL o al file oppure puoi caricare un file `.zip` di immagini. Vedi [Add images ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} nella guida di riferimento API v4.
1.  Aggiungi i dati di formazione alle tue immagini. Vedi [Preparazione dei tuoi dati di formazione](#object-detection-preparation).
1.  Forma la tua raccolta. Una volta che disponi di una quantità sufficiente di dati di formazione, avvia la formazione sulle immagini nella raccolta. Vedi [Train a collection ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} nella guida di riferimento API v4.

Dopo che hai completato questi passi e formato la tua raccolta, puoi analizzare le immagini rispetto ad essa.

### Preparazione dei tuoi dati di formazione
{: #object-detection-preparation}

La parte più importante del processo di configurazione è la preparazione e l'assemblaggio dei tuoi dati di formazione. Come succede quando [crei un modello personalizzato](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) per la classificazione delle immagini, assembli un insieme di immagini che rappresentano gli oggetti che vuoi rilevare.

Oltre ad un insieme di immagini, fornisci anche i dati di formazione per ciascuna immagine. Per il rilevamento degli oggetti, i dati di formazione sono l'insieme di etichette e ubicazioni per gli oggetti nell'immagine che vuoi che {{site.data.keyword.visualrecognitionshort}} riconosca. Puoi avere più di un oggetto in un'immagine.

L'etichetta identifica ciò che l'oggetto è. L'ubicazione identifica dove si trova nell'immagine. Identifichi l'ubicazione tracciando una _casella di delimitazione_ intorno all'oggetto e fornendo le coordinate in pixel della parte superiore e di quella di sinistra di tale casella, insieme alla larghezza e all'altezza in pixel.

Il seguente esempio mostra i dati di formazione per un oggetto con l'etichetta `BurntCookie`.

```json
{
  "objects": [{
    "object": "BurntCookie",
    "location": {
      "left": 33,
      "top": 8,
      "width": 163,
      "height": 119
    }
  }]
}
```
{: codeblock}

In questa release beta iniziale, crei le informazioni sull'ubicazione manualmente oppure utilizzando uno strumento di annotazione dell'immagine.

In generale, più immagini e caselle di delimitazione fornisci nei tuoi dati di formazione e meglio è. Sono di seguito riportate, a titolo introduttivo, alcune linee guida per i dati di formazione:

- Ogni immagine è di almeno 500 pixel sia per l'altezza che per la larghezza.
- Ogni oggetto etichettato nella raccolta ha almeno 100 ubicazioni (caselle di delimitazione).
- Ogni immagine nella raccolta ha non più di 10 caselle di delimitazione.
- La dimensione di ciascuna casella di delimitazione è pari a più del 15% delle dimensioni dell'immagine.
- L'API legge le tag di orientamento EXIF nelle tue immagini. Assicurati che le coordinate `location` corrispondano a tale orientamento. Per regolare l'orientamento, puoi utilizzare uno strumento come ImageMagick per _orientare automaticamente_ le tue immagini prima di aggiungere caselle di delimitazione.

Per ulteriori informazioni sul metodo **Add training data to an image**, vedi la [guida di riferimento API v4 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}.

### Forma la raccolta
{: #object-detection-train}

Dopo che hai aggiunto i dati di formazione alle immagini nella tua raccolta, il passo di configurazione finale consiste nel formare un modello di rilevamento degli oggetti. Una singola chiamata all'API avvia la formazione e la risposta include le informazioni sullo stato. Ad esempio, il seguente stato mostra che la formazione è stata avviata ma che non è ancora stata completata:

```json
"training_status": {
  "objects": {
    "ready": false,
    "in_progress": true,
    "data_changed": false,
    "latest_failed": false,
    "description": "Starting training"
  }
}
```
{: codeblock}

Puoi rieseguire la formazione di un modello dopo che hai aggiornato i dati di formazione immettendo nuovamente la chiamata.

Per ulteriori informazioni, vedi [Train a collection ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} nella guida di riferimento API v4.

## Analizza le immagini
{: #object-detection-analyze}

Dopo che hai configurato un modello di rilevamento degli oggetti personalizzato e dopo che la formazione è stata completata, puoi rilevare gli oggetti in altre immagini. Come per la classificazione, fornisci un'immagine o un file `.zip` di immagini e una **soglia** facoltativa per impostare il punteggio massimo degli oggetti rilevati. Per ulteriori informazioni, vedi il metodo **Analyze images** nella [guida di riferimento API v4 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images).

## Passi successivi
{: #object-detection-next-steps}

- Acquisisci dimestichezza con l'API nella [guida di riferimento API v4 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition-v4){: new_window}.
