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

# Note sulla release

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.
{: shortdesc}

## Funzioni beta
{: #beta}

{{site.data.keyword.IBM_notm}} rilascia i servizi, le funzioni e il supporto lingua per la tua valutazione che sono classificati come beta. Queste funzioni potrebbero non essere stabili, venire modificate frequentemente ed essere sospese con un breve preavviso. Le funzioni beta inoltre potrebbero non fornire lo stesso livello di prestazioni o compatibilità fornito generalmente dalle funzioni disponibili e non sono pensate per l'utilizzo in un ambiente di produzione. Le funzioni beta sono supportate solo in [developerWorks Answers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Modifiche
{: #changelog}

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio. 

### 11 dicembre 2017
{: #11december2017}

<ul>
  <li>
    <strong>Aumento dell'accuratezza e dell'output con il modello generale</strong>
      <p>
        Il modello generale, che contiene diverse migliaia di tag, ora rileva più oggetti secondari e ha migliorato il rilevamento della scena. Questi miglioramenti aiutano a riconoscere gli aspetti meno importanti di un'immagine. In aggiunta, il numero medio di tag restituite per immagine è stato incrementato di 10.
      </p>
      <p>
        La seguente immagine illustra un esempio di tag restituite prima dell'aggiornamento e le tag aggiuntive che vengono ora restituite.
      </p>
      <img src="images/antarctica-iceberg.jpg" alt="Iceberg in Antartide">
      <table>
        <tr>
          <th>Tag originali </th>
          <th>Tag aggiuntive</th>
        </tr>
        <tr>
          <td>
          Tag: iceberg<br/>
          Punteggio: 0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: ice mass<br/>
          Punteggio: 0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: nature<br/>
          Punteggio: 0.770</td>
        </tr>
        <tr>
          <td>
          Tag: blue color<br/>
          Punteggio: 0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: alabaster color<br/>
          Punteggio: 0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nuovo modello Explicit nella beta</strong>
      <p>
        Il modello Explicit, che viene avviato nella beta, classifica se un'immagine contiene contenuto pornografico ed è inappropriata per l'utilizzo generale. Puoi includere il modello Explicit con altri modelli per analisi combinate. Ad esempio, includi gli ID del classificatore `default` e `explicit` nella tua richiesta in modo che vengano restituite le tag dell'immagine e se contiene contenuto esplicito.
      <p>
        Per i dettagli sulla chiamata API, vedi il metodo **Classify images** in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image) o prova il modello in [API explorer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify).
      </p>
    </li>
    <li>
      <strong>Supporto per dimensioni di file molto grandi</strong>
      <p>
        I metodi <strong>Classify images</strong> ora supportano file di immagini fino a 10 MB e file .zip fino a 100 MB.
    </li>
    <li>
      <strong>Array obbligatorio quando si trasmettono gli ID del classificatore</strong>
      <p>
        L'API ora impone un array quando passi gli `classifier_ids` come parte dell'oggetto **parameters** nel metodo **Classify images**. Precedentemente, potevi passare un ID del classificatore come una stringa. Per ulteriori informazioni, consulta la descrizione dei parametri e il file di esempio in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image).
      </p>
    </li>
</ul>

### 8 settembre 2017
{: #8september2017}

- **Beta Similarity Search e raccolte chiusa**: Il giorno 8 settembre 2017, il periodo beta per Similarity Search è stato chiuso. Per ulteriori informazioni, consulta [Visual Recognition API – Similarity Search Update ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30 giugno 2017
{: #30june2017}

- **Contrassegno tramite tag migliorato**: abbiamo aumentato il numero di immagini di formazione per il classificatore predefinito. Questo aumento migliora la capacità di riconoscere in modo accurato la ‘scena’ generale di un'immagine. Per i dettagli, consulta [Further Enhancements for General Tagging Feature ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **Lingue aggiuntive**: il metodo **Classify images** ora supporta coreano, italiano e tedesco in aggiunta a inglese, arabo, spagnolo e giapponese.

    Per i dettagli sulla chiamata API, vedi il metodo **Classify an image** in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} Icona link esterno.

### 16 maggio 2017
{: #16may2017}

- **Nuovo classificatore food disponibile: Beta**

    Un nuovo modello di riconoscimento food beta fornisce specificità e accuratezza migliorate per le immagini degli elementi cibo. Il metodo **Classify an image** ti consente di aggiungere questo nuovo classificatore, "food", al parametro `classifier_ids`.

### 5 aprile 2017
{: #5april2017}

- **Nuovo strumento {{site.data.keyword.visualrecognitionshort}} disponibile: Beta**

    Una nuova funzione beta, lo strumento {{site.data.keyword.visualrecognitionshort}}, è disponibile all'indirizzo [https://watson-visual-recognition.ng.bluemix.net/ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Questo strumento ti aiuta ad utilizzare più facilmente il servizio {{site.data.keyword.visualrecognitionshort}}. Immettendo la tua chiave API {{{site.data.keyword.cloud_notm}}, puoi utilizzare una GUI per accedere alle funzioni di contrassegno tramite tag generale e di rilevamento volti, così come la creazione, il riaggiornamento e l'eliminazione senza interruzioni dei classificatori personalizzati associati alla tua chiave API, senza il bisogno di codifica.

### 8 marzo 2017
{: #8march2017}

- **Supporto lingua aggiornato per il contrassegno tramite tag del classificatore generale**

    Il classificatore generale ora restituisce le tag in tutte le lingue supportate.

- **Problemi noti**

    **RISOLTO 13-04-2017**: richiamare ripetutamente `GET /classifiers` mentre la formazione o il riaggiornamento sono in corso, per poter controllare lo stato, può provocare la disabilitazione del lavoro di formazione. Per risolvere temporaneamente questo problema, esegui il polling di un nuovo stato del classificatore utilizzando `GET /classifiers/{classifier_id}`. In altre parole, utilizza il classificatore `GET` per un solo ID del classificatore, invece di `GET /classifiers`, che richiama tutti i classificatori e può attivare questo problema. Inoltre tieni presente che `GET /classifiers/{classifier_id}` è più veloce.

### 15 dicembre 2016
{: #15december2016}

- **Contrassegno tramite tag del classificatore generale migliorato**

    - Gli algoritmi di apprendimento approfondito del classificatore generale sono stati aggiornati. C'è un significante miglioramento nella qualità del contrassegno tramite tag per tutte le lingue e un significativo aumento nel volume di tag inglesi restituite dal servizio. Questo output di tag di alta qualità è disponibile anche quando crei il tuo proprio classificatore personalizzato.
    - È stato aggiunto il contrassegno tramite tag per il colore. Il servizio ora restituisce il primo o primi due colori nell'immagine.

- **Problemi noti**

    - Le immagini inviate alla demo con le tag dei metadati EXIF non specificano correttamente l'orientamento (orizzontale e verticale) al servizio. Le immagini caricate da un iPhone possono contenere le tag dei metadati EXIF. La soluzione temporanea per questo problema è di caricare i tuoi metadati dell'immagine che non si affidano a tag di metadati EXIF per specificare l'orientamento della tua immagine. Spesso, puoi farlo semplicemente aprendo l'immagine sul tuo computer e salvandola. Ad esempio, su un Mac, l'apertura nell'anteprima e quindi il salvataggio dell'immagine, impostano le tag di orientamento corrette.
    - L'invio delle immagini al servizio {{site.data.keyword.visualrecognitionshort}} con i valori [tag EXIF ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://en.wikipedia.org/wiki/Exif){: new_window} di 8, 3 o 6 può aggiungere latenza. Il servizio ruota i pixel dell'immagine da un punto di vista codificato. Puoi risparmiare tempo pre-ruotando le tue immagini o rimuovendo le intestazioni EXIF se non sono importanti per la tua attività {{site.data.keyword.visualrecognitionshort}}.

### 1 dicembre 2016
{: #1december2016}

- **Nuovi prezzi**

    IBM ha abbassato i prezzi del classificatori personalizzati per il servizio {{site.data.keyword.visualrecognitionshort}} e aumentato la disponibilità per i piani gratuiti. Per ulteriori informazioni, consulta [{{site.data.keyword.visualrecognitionshort}} pricing page](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 ottobre 2016
{: #7october2016}

- **Miglioramenti nel rilevamento volti**

    Il servizio ha un nuovo algoritmo di rilevamento volti che migliora le risposte dei metodi `GET` e `POST /v3/detect_faces`. Il servizio ha regolato il filtro per i rilevamenti facciali con bassa attendibilità di età, nome e genere. Di conseguenza, vengono trovati più volti e viene restituito un intervallo di confidenza maggiore.

### 8 settembre 2016
{: #8september2016}

- **Similarity Search BETA**

    Gli utenti possono ora caricare la propria raccolta di immagini, utilizzarne una per ricercare in tale raccolta immagini simili, dopodiché il servizio restituisce le prime 100 immagini più simili. La ricerca per somiglianza può essere utilizzata per qualsiasi scopo e gli utenti possono personalizzare la formazione del servizio per le raccolte fino a 1 milione di immagini ognuna. Per ulteriori informazioni sull'utilizzo della nuova funzionalità di ricerca per somiglianza, consulta l'[Esercitazione](/docs/services/visual-recognition/tutorial-collections.html) e le pagine [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Il riconoscimento del testo è ora una beta chiusa**

    I metodi `POST` e `GET /v3/recognize_text` sono tornati nella beta chiusa. IBM continuerà a fornire il supporto ai client BETA che utilizzano il servizio, senza al momento piani per altre beta aperte.

### 1 agosto 2016

- **Fine dei piani introduttivi**

    Il riaggiornamento e la formazione del classificatore personalizzato, la classificazione delle immagini personalizzata e l'archivio del classificatore personalizzato, non sono più gratuiti. Per informazioni sui prezzi, consulta {{site.data.keyword.visualrecognitionshort}} service [pricing page](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 5 luglio 2016
{: #5july2016}

- **Aggiornamento dei classificatori personalizzati**

    I classificatori personalizzati non sono più limitati a una serie prestabilita di dati di formazione. Un utente può aggiornare i classificatori esistenti con nuove immagini o aggiungere i classificatori di esempio positivo o negativo a un classificatore preparato esistente. Fornendo ulteriori immagini di esempio per Watson, il servizio può rendere un classificatore dell'utente più accurato. I classificatori personalizzati possono ora imparare nel tempo, migliorandosi continuamente nella comprensione delle informazioni visive.

- **Problemi noti**

    **RISOLTO 13-04-2017**: gli utenti potrebbero ricevere un codice di errore 500 dopo 30 o 90 secondi quando aggiornano un classificatore esistente. Nonostante l'errore, c'è una buona probabilità che la richiesta di riaggiornamento venga completata correttamente. Attendi almeno 2 minuti e quindi controlla lo stato del classificatore utilizzando il metodo `GET classifiers/{classifier\_id}`. Se lo stato è "ready" e la data/ora per "retrained" è stata aggiornata, la richiesta di riaggiornamento che ha generato il codice 500 ha avuto esito positivo. Altrimenti, se la data/ora di "retrained" non è stata aggiornata, è stata aggiunta una spiegazione alla risposta con il motivo per cui il riaggiornamento non è riuscito e il servizio riporterà il classificatore alla versione a cui era prima dell'immissione della richiesta di riaggiornamento.

### 20 maggio 2016
{: #20 may 2016}

Questa è una release di disponibilità generale del servizio {{site.data.keyword.visualrecognitionshort}}. Questa release introduce la versione 3 del servizio ed è una modifica alle informazioni. Questa release incorpora la funzionalità dal servizio AlchemyVision, che è diventato obsoleto.

Ogni classificatore personalizzato che è stato creato mentre il servizio era nella beta deve essere ricreato in un'istanza GA del servizio.

I seguenti aggiornamenti e modifiche sono stati effettuati al servizio {{site.data.keyword.visualrecognitionshort}}:

- **Data versione:** per utilizzare le funzioni di questa release, utilizza `2016-05-20` come valore per il parametro `version`.
- **Classi e classificatori:** le classi singole sono ora denominate "classes". In GA, un gruppo di classi è denominato "classifier".
- **Classificazione:** utilizza i metodi `POST` o `GET /v3/classify` per identificare in modo veloce e accurato molti soggetti e scene come le classi predefinite.
- **Rilevamento volti:** utilizza i metodi `POST` o `GET /v3/detect_faces` per rilevare i volti nelle immagini e ottenere le informazioni su di essi, come dove si trova il volto nell'immagine e il genere e l'intervallo di età stimati per ogni volto. Il servizio può anche identificare molte celebrità per nome e può fornire un grafo della conoscenza in modo che puoi effettuare aggregazioni interessanti in concetti di livello superiore.
- **Classificatori personalizzati con più sfaccettature:** puoi ora creare e formare classificatori altamente specializzati definiti da molte classi. Ad esempio, puoi creare un classificatore "new\_red\_car" definito dalle classi "new\_cars" e "red\_cars". Per ulteriori informazioni sulla creazione di classificatori con più sfaccettature, consulta [Struttura dei dati di formazione](/docs/services/visual-recognition/customizing.html#structure).
- **Formazione asincrona:** la formazione di classificatori personalizzati è ora asincrona, per cui le chiamate di formazione si completano più velocemente mentre il tuo classificatore personalizzato continua a ricevere informazioni in background. Per controllare lo stato di formazione del tuo classificatore personalizzato e trovare quando è disponibile per l'utilizzo, richiama il metodo `GET /v3/classifiers/{classifier_id}` e controlla il parametro della risposta `status`.

### 2 dicembre 2015
{: #2december2015}

L'ultima release del servizio {{site.data.keyword.visualrecognitionshort}} è una modifica delle informazioni che introduce una nuova versione dell'API {{site.data.keyword.visualrecognitionshort}}(v2). La versione 1 del servizio {{site.data.keyword.visualrecognitionshort}} è disponibile per l'utilizzo finché il servizio non esce dalla beta.

Per iniziare ad utilizzare immediatamente la versione 2 dell'API, devi aggiornare il tuo codice per riflettere queste modifiche:

- Nella versione 1 del servizio, analizzavi le immagini per etichette. Nella versione 2 del servizio, le etichette sono chiamate **classificatori**. I classificatori hanno un ID del classificatore univoco indicato dal parametro `classifier_id` e un nome breve indicato dal parametro `name`.
- Il metodo `POST /v1/recognize` per l'analisi di un'immagine è ora il metodo [`POST /v2/classify` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}. Il parametro `labels_to_check` è stato ridenominato con `classifier_ids`.
- Il metodo `GET /v1/tag/labels` per il richiamo di un elenco di etichette nella V1 è ora il metodo [`GET /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} per il richiamo di un elenco di classificatori.
- In aggiunta al richiamo di un elenco di classificatori, puoi anche richiamare i dettagli di un classificatore specifico con il nuovo metodo [`GET /v2/classifiers/{classifier_id}` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window}.
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta ti permette di creare classificatori personalizzati con il nuovo metodo [`POST /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window}. Per ulteriori informazioni sulla creazione di classificatori personalizzati, consulta [Creazione dei classificatori personalizzati](/docs/services/visual-recognition/customizing.html).
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta ti abilita anche ad eliminare i classificatori personalizzati con il nuovo metodo [`DELETE /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window}.
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta richiede il parametro `version`. Specifica la data di release della versione dell'API che desideri utilizzare nel formato `MM-DD-YYYY`.
