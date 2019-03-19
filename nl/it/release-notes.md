---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

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

[watson-studio-reg]: https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs
[demo]: https://www.ibm.com/watson/services/visual-recognition/demo

# Note sulla release
{: #release-notes}

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.
{: shortdesc}

## Controllo versioni delle API del servizio
{: version}

Le richieste API richiedono un parametro di versione che prende una data nel formato `version=YYYY-MM-DD`. Ogni volta che modifichiamo l'API in un modo non compatibile con le versioni precedenti, rilasciamo una nuova versione secondaria della API.

Invia il parametro di versione con ogni richiesta API. Il servizio utilizza la versione API per la data che specifichi oppure la versione più recente prima di tale data. Non utilizzare, per impostazione predefinita, la data attuale.Specifica invece una data che corrisponde a una versione compatibile con la tua applicazione e non modificarla finché la tua applicazione non è pronta per una versione successiva.

La versione corrente è `2018-03-19`.

## Funzioni beta
{: #beta}

{{site.data.keyword.IBM_notm}} rilascia i servizi, le funzioni e il supporto lingua per la tua valutazione che sono classificati come beta. Queste funzioni potrebbero non essere stabili, venire modificate frequentemente ed essere sospese con un breve preavviso. Le funzioni beta inoltre potrebbero non fornire lo stesso livello di prestazioni o compatibilità fornito generalmente dalle funzioni disponibili e non sono pensate per l'utilizzo in un ambiente di produzione. Le funzioni beta sono supportate solo in [IBM Developer Answers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Modifiche
{: #changelog}

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.

### 15 gennaio 2019
{: #15january2019}

- **Traduzione per il sesso in Detect Faces**
    - I metodi **Detect Faces** ora restituiscono delle stringhe tradotte per "Male" e "Female" quando fornisci la lingua nell'intestazione della richiesta **Accept-Language**. Per i dettagli, vedi la [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}.

### 1° ottobre 2018
{: #01october2018}

- **Le istanze del servizio create prima del 23 maggio 2018 vengono eliminate.**

    - Come segnalato in precedenza, tutte le istanze {{site.data.keyword.visualrecognitionshort}} create prima del 23 maggio 2018 non sono più attive. I dati dalle istanze sono ora eliminati. Vedi [Migrazione](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) per i dettagli su come passare a una nuova istanza del servizio.
    - Le istanze del servizio create dopo questa data non sono interessate.
    - Se hai delle domande, contatta il [Supporto IBM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/ibmcloudsupport){: new_window}.

### 1° agosto 2018
{: #01august2018}

- **GA (General Availability) dei modelli Food ed Explicit**

    I modelli Food ed Explicit sono passati da Beta a GA (General Availability). Il modello Food riconosce più cibo e pasti del modello General (predefinito). Il modello Explicit identifica quelle che potrebbero essere considerate immagini pornografiche.

    Non è richiesta alcuna modifica al codice. Entrambi i modelli sono gratuiti nel piano Lite e costano $0,002 per ogni immagine nel piano Standard.

    Per ulteriori informazioni, vedi [Updates to Watson Visual Recognition ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/visrec-price-reduction){: new_window} nel <em>blog di Watson</em>.

### 1° luglio 2018
{: #01july2018}

- **Nuovi prezzi per i modelli personalizzati**
    - A partire dal 1° luglio 2018, la classificazione di un'immagine con un modello personalizzato costa la metà della tariffa precedente ed è ora pari a $0,002 per ogni immagine. Per i dettagli e altre importanti informazioni, vedi [Updates to Watson Visual Recognition \- Price reduction for Custom Classification ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/visrec-price-reduction){: new_window} nel <em>blog di Watson</em>.

### 21 giugno 2018
{: #21june2018}

- **Supporto per ulteriori lingue**

    - I metodi **Classify** ora supportano il cinese (semplificato e tradizionale) e il portoghese (Brasile) nell'output delle classi di modello `default` (General). Per l'elenco completo delle lingue, vedi [Lingue supportate](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).
    - Tutte le lingue sono ora supportate anche nelle risposte dai modelli **Food** ed **Explicit**,


### 22 maggio 2018
{: #22may2018}

- **Nuovo processo di autenticazione API**:

    Puoi ora eseguire l'autenticazione con IAM (Identity and Access Management) su un nuovo endpoint:

    - Utilizza un URL dell'endpoint differente per le nuove istanze. L'endpoint predefinito è `https:/gateway.watsonplatform.net/visual-recognition/api/`. Per trovare l'URL per la tua istanza del servizio, controlla le credenziali facendo clic sull'istanza dal {{site.data.keyword.cloud_notm}} [Dashboard ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/apps?watson){: new_window}.
    - Modifica la tua modalità di autenticazione presso l'API. Fornisci una chiave IAM oppure un token di accesso per la tua istanza del servizio. Per degli esempi, vedi [Migrazione](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating).

    Per le istanze del servizio create prima del 23 maggio 2018, il processo di autenticazione e l'endpoint non sono cambiati. Esegui l'autenticazione fornendo il parametro di query `api_key`.

- **Aggiornamenti al piano Lite**

    I piani Lite creati dopo il 22 maggio 2018 stanno cambiando:

    - Le nuove istanze del piano Lite continuano a essere disponibili dopo 30 giorni, se le usi ogni mese.
    - Puoi creare e rieseguire la formazione di due modelli personalizzati con il nuovo piano Lite.
    - I piani Lite includono fino a 1.000 eventi al mese. Ogni immagine che invii per la classificazione, il rilevamento o la formazione è un evento. Il download di un modello Core ML non viene conteggiato ai fini del limite di eventi.

    Se le tue esigenze superano quanto offerto dal piano Lite, esegui l'aggiornamento a un account a pagamento. [Esplora ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} i piani dei prezzi.

- **Sicurezza delle informazioni**:

    Abbiamo aggiornato la documentazione per includere alcuni nuovi dettagli sulla privacy dei dati. Leggi i dettagli in [Sicurezza delle informazioni](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security).

### 12 aprile 2018
{: #12april2018}

- **Supporto per la riesecuzione della formazione di un modello personalizzato in un piano Lite**

    Con il piano Lite, non devi più eliminare e creare un altro modello personalizzato quando vuoi aggiornare il modello o rieseguirne la formazione. Puoi ora aggiornare un modello personalizzato purché tu rimanga al di sotto dei [limiti](https://console.bluemix.net/catalog/services/visual-recognition) giornalieri e mensili del piano.

    Se hai bisogno di disporre di più modelli o più versioni dello stesso modello, esegui l'aggiornamento dal piano Lite a un account a pagamento.

- **Nuova versione secondaria con supporto per CORS**

    **Versione:** `2018-03-19`

    Ora supportiamo le intestazioni CORS (Cross-Origin Resource Sharing) quando specifichi `version=2018-03-19` nelle richieste.

### 5 aprile 2018
{: #5april2018}

- **Correzione per il problema relativo ai punteggi del modello Face**

  L'intervallo per il punteggio di età nel modello Face è stato ripristinato all'intervallo originale compreso tra 0 e 1. Per i dettagli, vedi i [Problemi noti](#2april2018) per il 2 aprile 2018.

- **Nuovi parametri form-data**

    I metodi **Classify images** e **Detect faces in images** supportano dei nuovi parametri form-data. Classify images supporta dei parametri `url`, `classifier_ids`, `threshold` e `owners` separati e Detect faces supporta `url`.

    In passato, codificavi i valori in una stringa JSON e passavi il parametro form-data **parameters**. Puoi utilizzare il nuovo metodo per passare questi valori in parametri form-data separati per tutto lo sviluppo di applicazioni. Per i dettagli, vedi la [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### 2 aprile 2018
{: #2april2018}

- **GA (General Availability) del modello Face migliorato**

    Il modello di rilevamento volti aggiornato è ora in GA (General Availability).

    Questo modello migliorato utilizza delle serie di dati di formazione più ampie per una maggiore accuratezza del rilevamento volti per l'età e il sesso. Ad esempio, le previsioni dell'età sono migliorate riducendo l'intervallo tra `min` e `max`. L'intervallo di età fisso di 9 anni nel modello precedente è stato sostituito con un intervallo dinamico e più piccolo. L'intervallo di età medio è ora di 4,9 anni.

    - Modifiche all'API 

    Altre differenze tra il modello Face migliorato e quello precedente:
        - Il modello migliorato supporta i formati immagine .gif e .tif.
        - Il modello migliorato supporta dimensioni file maggiori: fino a 10 MB per i file immagine e fino a 100 MB per i file .zip.
        - Il modello migliorato non include le informazioni `FaceIdentity` nella risposta. Le informazioni sull'identità fanno riferimento al nome (`name`) della persona, al punteggio (`score`) e al grafo della conoscenza `type_hierarchy`.

    Per i dettagli sull'API, vedi la [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

    - Problemi noti

        - I parametri form non possono includere il **Content-Type**. Ad esempio, questa richiesta non riesce ad analizzare il parametro **url** perché include `;type=text/plain`:

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - Il punteggio dell'età ha un intervallo compreso tra 0 e 0,3. Stiamo lavorando per ripristinare l'intervallo originale compreso tra 0 e 1.

    - Endpoint beta dichiarato obsoleto

    L'endpoint beta a `/v3/rivelt_faces_beta` è stato dichiarato obsoleto e non sarà accessibile dopo il 17 maggio 2018. Assicurati che le tue richieste puntino a `/v3/detect_faces`.

### 20 marzo 2018
{: #20march2018}

- **Integrazione con Apple Core ML**

    {{site.data.keyword.visualrecognitionshort}} ora include il supporto per il formato di modello Apple Core ML. Puoi utilizzare una versione Core ML del tuo modello {{site.data.keyword.visualrecognitionshort}} sulle tue applicazioni iOS.

    **Inizia l'attività di sviluppo**: per iniziare l'attività di sviluppo con {{site.data.keyword.visualrecognitionshort}} e Core ML, consulta questi progetti su GitHub:

    - Classifica le immagini localmente: [{{site.data.keyword.visualrecognitionshort}} con Core ML ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - Integra {{site.data.keyword.discoveryfull}} con i risultati: [{{site.data.keyword.visualrecognitionshort}} e Discovery con Core ML ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - Esplora l'SDK: [Swift SDK ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **Modifiche all'API **

    Nell'integrazione sono incluse le seguenti modifiche all'API compatibili con le versioni precedenti:

    - Un nuovo campo `core_ml_enabled` che indica se un modello del classificatore può essere scaricato come un modello Core ML. Il campo viene restituito nella risposta per le chiamate a `GET e POST /v3/classifiers` e `GET /v3/classifiers/{classifier_id}`.
    - Un nuovo metodo `GET /v3/classifiers/{classifier_id}/core_ml_model` per scaricare un modello Core ML come un file .mlmodel. Puoi scaricare i file modello Core ML per i modelli personalizzati creati dopo il 19 marzo.
    - Un nuovo campo `updated` con i dati di formazione più recenti del modello. Il campo `updated` corrisponde al campo `retrained` o al campo `created`.

    Per i dettagli sulle modifiche dell'API per Core ML, vedi la [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}.

- **Disponibilità di un nuovo strumento: Watson Studio**

    [Watson Studio ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")][watson-studio-reg]{: new_window} è il nuovo ambiente integrato che include una sostituzione per lo strumento {{site.data.keyword.visualrecognitionshort}} beta. Watson Studio supporta non solo {{site.data.keyword.visualrecognitionshort}} ma anche molti altri servizi e molte altre risorse {{site.data.keyword.cloud_notm}}. Puoi utilizzare Watson Studio con tutte le tue istanze e tutti i classificatori {{site.data.keyword.visualrecognitionshort}}.

     Watson Studio fornisce un ambiente collaborativo nel cloud. Con Watson Studio, gli sviluppatori, gli esperti in materia, i data scientist e altri possono creare e formare {{site.data.keyword.visualrecognitionshort}} e altri modelli di intelligenza artificiale. Puoi anche utilizzare Watson Studio per accedere ai modelli General e Face integrati.

     Watson Studio supporta anche Core ML. Puoi scaricare un file modello Core ML per il tuo modello personalizzato.

    [Introduzione a ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")][watson-studio-reg]{: new_window} con Watson Studio.

- **Architettura di apprendimento approfondito (deep learning) aggiornata per i modelli personalizzati**

    {{site.data.keyword.visualrecognitionshort}} ora utilizza un'architettura di rete di apprendimento approfondito (deep learning) più rapida ed efficiente per la classificazione. I modelli aggiornati possono anche operare una differenziazione più netta tra la classe superiore e il resto delle classi. Questo approccio potrebbe avere come esito dei tempi di formazione un po' più lunghi. La nuova architettura viene utilizzata per formare nuovi modelli personalizzati. Quando riesegui la formazione di modelli esistenti meno recenti, viene utilizzata l'architettura originale.

    Il seguente esempio mostra la differenziazione con la nuova architettura:

    ![Uomo che tira con l'arco. Foto di Annie Spratt on Unsplash](images/archery.jpg)

    <table>
      <tr>
        <th>Classe originale e punteggio</th>
        <th>Classe aggiornata e punteggio</th>
      </tr>
      <tr>
        <td>Archery</br>0,99 </td>
        <td><strong>archery<strong></br>0.9</td>
      </tr>
      <tr>
        <td>Auto Racing</br>0,996398</td>
        <td><strong>biking</strong></br>0,004</td>
      </tr>
      <tr>
        <td>Biking</br>0,0500174</td>
        <td><strong>fishing</strong></br>0,001</td>
      </tr>
      <tr>
        <td>Fishing</br>0,11029</td>
        <td><strong>golf</strong></br>0,031</td>
      </tr>
      <tr>
        <td>Golf</br>0,0980796</td>
        <td><strong>gymnastics</strong></br>0,029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0,964391</td>
        <td><strong>judo</strong></br>0,021</td>
      </tr>
      <tr>
        <td>Judo</br>0,339119</td>
        <td><strong>racing</strong></br>0,002</td>
      </tr>
      <tr>
        <td>Skating</br>0,0393602</td>
        <td><strong>skating</strong></br>0,061</td>
      </tr>
      <tr>
        <td>Skiing</br>0,0310527</td>
        <td><strong>skiing</strong></br>0,003</td>
      </tr>
      <tr>
        <td>Track and Field</br>0,208147</td>
        <td><strong>track</strong></br>0.035</td>
      </tr>
    </table>

- **Supporto lingua per il francese**

    I metodi **Classify** ora supportano il francese nell'output delle classi modello `default`. Per l'elenco completo delle lingue, vedi [Lingue supportate](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).

### 23 febbraio 2018
{: #23february2018}

- **Modello Face migliorato disponibile in beta**

    È disponibile un modello di rilevamento volti aggiornato. Questo modello beta utilizzata delle serie di dati di formazione più ampie per una maggiore accuratezza del rilevamento volti per l'età e il sesso. Per ulteriori informazioni, vedi [Increasing the Accuracy of IBM’s Watson {{site.data.keyword.visualrecognitionshort}} service ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} e [Mitigating Bias in AI Models ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}.

    - Puoi visualizzare i risultati del modello aggiornato nella [demo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")][demo]{: new_window} e nel [Visual Recognition Tool ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} beta.
    - Il modello beta è disponibile in `/v3/detect_faces_beta`.

    Differenze tra i modelli beta e GA (General Availability):
    - Il modello beta supporta i formati immagine .gif e .tif; l'applicazione di questo miglioramento è prevista nel modello GA.
    - Il modello beta supporta dimensioni file maggiori: fino a 10 MB per i file immagine e fino a 100 MB per i file .zip. L'applicazione di questo miglioramento è prevista nel modello GA.
    - Il rilevamento volti beta non include le informazioni `FaceIdentity` nella risposta.
    - La richiesta POST del modello beta richiede un nome file non vuoto. Il modello Face GA non implementa questo vincolo.
    - La richiesta POST del modello beta supporta un parametro form separato denominato `url`. Il modello GA racchiude tali informazioni nell'oggetto JSON `parameters`.Per i dettagli, vedi la [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-api-explorer.mybluemix){: new_window}.

- **Identità di Face dichiarata obsoleta**

    Le informazioni sull'identità nella risposta del modello Face GA sono state dichiarate obsolete e verranno rimosse dall'API il **2 aprile 2018.** Le informazioni sull'identità fanno riferimento al nome (`name`) della persona, al punteggio (`score`) e al grafo della conoscenza `type_hierarchy`.

### 16 gennaio 2018
{: #16january2018}

- **L'account e il piano Lite sostituiscono il piano Gratuito**

    Un account Lite è gratuito; non è richiesta alcuna carta di credito. Tuttavia, le istanze di servizio del piano Lite vengono eliminate dopo 30 giorni.

    Il numero massimo di chiamate API che puoi effettuare con il piano Lite è leggermente diverso dal piano Gratuito. Puoi effettuare un massimo di 7.500 chiamate API al mese a 250 chiamate al giorno nel piano Lite.

    Per eseguire un aggiornamento a un account a pagamento quando hai dei classificatori personalizzati, crea un'altra istanza del servizio e crea nuovamente i tuoi classificatori personalizzati.

### 11 dicembre 2017
{: #11december2017}

<ul>
  <li>
    <strong>Aumento dell'accuratezza e dell'output con il modello General</strong>
      <p>
        Il modello General, che contiene diverse migliaia di tag, ora rileva più oggetti secondari e ha migliorato il rilevamento della scena. Questi miglioramenti aiutano a riconoscere gli aspetti meno importanti di un'immagine. In aggiunta, il numero medio di tag restituite per immagine è stato incrementato di 10.
      </p>
      <p>
        La seguente immagine illustra un esempio di tag restituite prima dell'aggiornamento e le tag aggiuntive che vengono ora restituite.
      </p>
      <img src="images/tree-flower.jpg" alt="Foto di un'azalea">
      <table>
        <tr>
          <th>Tag originali</th>
          <th>Tag aggiuntive</th>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: tree<br/>
          Punteggio: 0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: flower<br/>
          Punteggio: 0.792</td>
        </tr>
        <tr>
          <td>
          Tag: alpine azalea<br/>
          Punteggio: 0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: plant<br/>
          Punteggio: 0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: azalea<br/>
          Punteggio: 0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            Tag: swamp azalea<br/>
          Punteggio: 0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            Tag: reddish orange color<br/>
          Punteggio: 0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nuovo modello Explicit nella beta</strong>
      <p>
        Il modello Explicit, che viene avviato nella beta, classifica se un'immagine contiene contenuto pornografico ed è inappropriata per l'utilizzo generale. Puoi includere il modello Explicit con altri modelli per analisi combinate. Ad esempio, includi gli ID del classificatore `default` e `explicit` nella tua richiesta in modo che vengano restituite le tag dell'immagine e se contiene contenuto esplicito.
      <p>
        Per i dettagli sulla chiamata API, vedi il metodo **Classify images** nella [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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
        L'API ora impone un array quando passi gli `classifier_ids` come parte dell'oggetto **parameters** nel metodo **Classify images**. Precedentemente, potevi passare un ID del classificatore come una stringa. Per ulteriori informazioni, consulta la descrizione dei parametri e il file di esempio nella [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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

    Per i dettagli sulla chiamata API, vedi il metodo **Classify an image** nella [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

### 16 maggio 2017
{: #16may2017}

- **Nuovo classificatore food disponibile: Beta**

    Un nuovo modello di riconoscimento food beta fornisce specificità e accuratezza migliorate per le immagini degli elementi cibo. Il metodo **Classify an image** ti consente di aggiungere questo nuovo classificatore, "food", al parametro `classifier_ids`.

### 5 aprile 2017
{: #5april2017}

- **Nuovo strumento {{site.data.keyword.visualrecognitionshort}} disponibile: Beta**

    Una nuova funzione beta, lo strumento {{site.data.keyword.visualrecognitionshort}}, è disponibile all'indirizzo [https://watson-visual-recognition.ng.bluemix.net/ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Questo strumento ti aiuta ad utilizzare più facilmente il servizio {{site.data.keyword.visualrecognitionshort}}. Immettendo la tua chiave API {{site.data.keyword.cloud_notm}}, puoi utilizzare una GUI per accedere alle funzioni di contrassegno tramite tag generale e di rilevamento volti, così come la creazione, la riesecuzione della formazione e l'eliminazione senza interruzioni dei classificatori personalizzati associati alla tua chiave API, senza il bisogno di codifica.

### 8 marzo 2017
{: #8march2017}

- **Supporto lingua aggiornato per il contrassegno tramite tag del classificatore generale**

    Il classificatore generale ora restituisce le tag in tutte le lingue supportate.

- **Problemi noti**

    **RISOLTO 13-04-2017**: richiamare ripetutamente `GET /classifiers` mentre la formazione o la riesecuzione della formazione sono in corso, per poter controllare lo stato, può provocare la disabilitazione del lavoro di formazione. Per risolvere temporaneamente questo problema, esegui il polling di un nuovo stato del classificatore utilizzando `GET /classifiers/{classifier_id}`. In altre parole, utilizza il classificatore `GET` per un solo ID del classificatore, invece di `GET /classifiers`, che richiama tutti i classificatori e può attivare questo problema. Inoltre tieni presente che `GET /classifiers/{classifier_id}` è più veloce.

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

    {{site.data.keyword.IBM_notm}} ha abbassato i prezzi dei classificatori personalizzati nel servizio {{site.data.keyword.visualrecognitionshort}} e aumentato quanto disponibile nel piano gratuito. Per ulteriori informazioni, consulta la[pagina dei prezzi di {{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 ottobre 2016
{: #7october2016}

- **Miglioramenti nel rilevamento volti**

    Il servizio ha un nuovo algoritmo di rilevamento volti che migliora le risposte dei metodi `GET` e `POST /v3/detect_faces`. Il servizio ha regolato il filtro per i rilevamenti dei volti con bassa attendibilità di età, nome e genere. Di conseguenza, vengono trovati più volti e viene restituito un intervallo di attendibilità maggiore.

### 8 settembre 2016
{: #8september2016}

- **Similarity Search BETA**

    Gli utenti possono ora caricare la propria raccolta di immagini, utilizzarne una per ricercare in tale raccolta immagini simili, dopodiché il servizio restituisce le prime 100 immagini più simili. La ricerca per somiglianza può essere utilizzata per qualsiasi scopo e gli utenti possono personalizzare la formazione del servizio per le raccolte fino a 1 milione di immagini ognuna. Per ulteriori informazioni sull'utilizzo della nuova funzionalità di ricerca per somiglianza, consulta l'[Esercitazione](/docs/services/visual-recognition/tutorial-collections.html) e le pagine della [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Il riconoscimento del testo è ora una beta chiusa**

    I metodi `POST` e `GET /v3/recognize_text` sono tornati nella beta chiusa. {{site.data.keyword.IBM_notm}} intende continuare a fornire il supporto ai client BETA che utilizzano il servizio, senza al momento piani per altre beta aperte.

### 1 agosto 2016

- **Fine dei piani introduttivi**

    La riesecuzione della formazione e la formazione del classificatore personalizzato, la classificazione delle immagini personalizzata e l'archivio del classificatore personalizzato, non sono più gratuiti. Per informazioni sui prezzi, vedi la [pagina dei prezzi ](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) del servizio {{site.data.keyword.visualrecognitionshort}}.

### 5 luglio 2016
{: #5july2016}

- **Aggiornamento dei classificatori personalizzati**

    I classificatori personalizzati non sono più limitati a una serie prestabilita di dati di formazione. Un utente può aggiornare i classificatori esistenti con nuove immagini o aggiungere i classificatori di esempio positivo o negativo a un classificatore preparato esistente. Fornendo ulteriori immagini di esempio per Watson, il servizio può rendere un classificatore dell'utente più accurato. I classificatori personalizzati possono ora imparare nel tempo, migliorandosi continuamente nella comprensione delle informazioni visive.

- **Problemi noti**

    **RISOLTO 13-04-2017**: gli utenti potrebbero ricevere un codice di errore 500 dopo 30 o 90 secondi quando aggiornano un classificatore esistente. Nonostante l'errore, c'è una buona probabilità che la richiesta di riesecuzione della formazione venga completata correttamente. Attendi almeno 2 minuti e quindi controlla lo stato del classificatore utilizzando il metodo `GET classifiers/{classifier\_id}`. Se lo stato è "ready" e la data/ora per "retrained" è stata aggiornata, la richiesta di riesecuzione della formazione che ha generato il codice 500 ha avuto esito positivo. Altrimenti, se la data/ora di "retrained" non è stata aggiornata, è stata aggiunta una spiegazione alla risposta con il motivo per cui la riesecuzione della formazione non è riuscita e il servizio riporterà il classificatore alla versione a cui era prima dell'immissione della richiesta di riesecuzione della formazione.

### 20 maggio 2016
{: #20 may 2016}

Questa è una release GA (General Availability) del servizio {{site.data.keyword.visualrecognitionshort}}. Questa release introduce la versione 3 del servizio ed è una modifica alle informazioni. Questa release incorpora la funzionalità dal servizio AlchemyVision, che è diventato obsoleto.

Ogni classificatore personalizzato che è stato creato mentre il servizio era nella beta deve essere ricreato in un'istanza GA del servizio.

I seguenti aggiornamenti e modifiche sono stati effettuati al servizio {{site.data.keyword.visualrecognitionshort}}:

- **Data versione:** per utilizzare le funzioni di questa release, utilizza `2016-05-20` come valore per il parametro `version`.
- **Classi e classificatori:** le classi singole sono ora denominate "classes". In GA, un gruppo di classi è denominato "classifier".
- **Classificazione:** utilizza i metodi `POST` o `GET /v3/classify` per identificare in modo veloce e accurato molti soggetti e scene come le classi predefinite.
- **Rilevamento volti:** utilizza i metodi `POST` o `GET /v3/detect_faces` per rilevare i volti nelle immagini e ottenere le informazioni su di essi, come dove si trova il volto nell'immagine e il genere e l'intervallo di età stimati per ogni volto. Il servizio può anche identificare molte celebrità per nome e può fornire un grafo della conoscenza in modo da consentirti di effettuare aggregazioni interessanti in concetti di livello superiore.
- **Classificatori personalizzati con più sfaccettature:** puoi ora creare e formare classificatori altamente specializzati definiti da molte classi. Ad esempio, puoi creare un classificatore "new\_red\_car" definito dalle classi "new\_cars" e "red\_cars". Per ulteriori informazioni sulla creazione di classificatori con più sfaccettature, consulta [Struttura dei dati di formazione](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure).
- **Formazione asincrona:** la formazione di classificatori personalizzati è ora asincrona, per cui le chiamate di formazione si completano più velocemente mentre il tuo classificatore personalizzato continua a ricevere informazioni in background. Per controllare lo stato di formazione del tuo classificatore personalizzato e trovare quando è disponibile per l'utilizzo, richiama il metodo `GET /v3/classifiers/{classifier_id}` e controlla il parametro della risposta `status`.

### 2 dicembre 2015
{: #2december2015}

L'ultima release del servizio {{site.data.keyword.visualrecognitionshort}} è una modifica delle informazioni che introduce una nuova versione dell'API {{site.data.keyword.visualrecognitionshort}}(v2). La versione 1 del servizio {{site.data.keyword.visualrecognitionshort}} è disponibile per l'utilizzo finché il servizio non esce dalla beta.

Per iniziare ad utilizzare immediatamente la versione 2 dell'API, devi aggiornare il tuo codice per riflettere queste modifiche:

- Nella versione 1 del servizio, analizzavi le immagini per etichette. Nella versione 2 del servizio, le etichette sono chiamate **classificatori**. I classificatori hanno un ID del classificatore univoco indicato dal parametro `classifier_id` e un nome breve indicato dal parametro `name`.
- Il metodo `POST /v1/recognize` per l'analisi di un'immagine è ora il metodo [`POST /v2/classify` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window}. Il parametro `labels_to_check` è stato ridenominato con `classifier_ids`.
- Il metodo `GET /v1/tag/labels` per il richiamo di un elenco di etichette nella V1 è ora il metodo [`GET /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} per il richiamo di un elenco di classificatori.
- In aggiunta al richiamo di un elenco di classificatori, puoi anche richiamare i dettagli di un classificatore specifico con il nuovo metodo [`GET /v2/classifiers/{classifier_id}` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window}.
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta ti permette di creare classificatori personalizzati con il nuovo metodo [`POST /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window}. Per ulteriori informazioni sulla creazione di classificatori personalizzati, consulta [Creazione dei classificatori personalizzati](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta ti abilita anche ad eliminare i classificatori personalizzati con il nuovo metodo [`DELETE /v2/classifiers` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window}.
- La versione 2 dell'API {{site.data.keyword.visualrecognitionshort}} beta richiede il parametro `version`. Specifica la data di release della versione dell'API che desideri utilizzare nel formato `MM-DD-YYYY`.
