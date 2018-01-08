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

# Creazione di un classificatore personalizzato

Dopo aver classificato un'immagine nell'"Esercitazione introduttiva," sei pronto per formare e creare un classificatore personalizzato (o modello). Con un classificatore personalizzato, puoi formare il servizio {{site.data.keyword.visualrecognitionshort}} per classificare le immagini per soddisfare i tuoi bisogni di business.
{: shortdesc}

## Passo 1:  copia le tue credenziali
{: #copy-credentials}

Utilizza le credenziali copiate nell'"Esercitazione introduttiva." Se non hai creato un'istanza del servizio, esegui questi passi nella sezione [Prima di cominciare](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Passo 2: creazione di un classificatore personalizzato
{: #create}

{{site.data.keyword.visualrecognitionshort}} puoi utilizzare le immagini di esempio che hai caricato per creare un nuovo classificatore con più sfaccettature. Ogni file di esempio viene formato da altri file in tale chiamata e gli esempi positivi vengono archiviati come classi. Queste classi vengono raggruppate per definire un solo classificatore e restituiscono i propri punteggi. I file di esempio negativi non vengono archiviati come classi. 

1.  Scarica i file di formazione di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Richiama il metodo `POST /v3/classifiers` con il seguente comando, che carica i dati di formazione e crea un classificatore `dogs`:
    - Sostituisci `{api-key}` con le credenziali del servizio copiate nel primo passo. 
    - Modifica l'ubicazione di `{class}_positive_examples` in modo che punti a dove hai salvato i file .zip.

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    I nomi file di esempio positivi richiedono un suffisso `_positive_examples`. In questo esempio, i nomi file sono `beagle_positive_examples`, `goldenretriever_positive_examples` e `husky_positive_examples`. Il prefisso (beagle, goldenretriever e husky) viene restituito come nome della classe.
    {:tip }

    La risposta include un nuovo stato e ID del classificatore, ad esempio:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

1.  Controlla lo stato di formazione periodicamente finché non visualizzi uno stato di `ready`. La formazione inizia immediatamente e deve finire prima di poter eseguire una query del classificatore. Sostituisci `{api  key}` e `{classifier_id}` con le tue informazioni:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Passo 3: aggiornamento di un classificatore personalizzato esistente

Non puoi aggiornare un classificatore personalizzato con una chiave API gratuita. Se disponi di una chiave gratuita, puoi aggiornarla a un piano standard. Per i dettagli, consulta [Modifica del tuo piano](https://console.bluemix.net/docs/pricing/changing_plan.html).
{: tip}

Puoi aggiornare un classificatore personalizzato aggiungendo le classi al classificatore oppure aggiungendo le immagini a una classe esistente. Qui, migliori il classificatore che hai creato nel passo 2 aggiungendo una classe *Dalmatian* ai tipi di cani che possono essere classificati. Inoltre aggiungi le immagini di gatti alla serie di esempio negativa per il classificatore "dogs".

1.  Scarica i file di formazione di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Richiama il metodo `POST /v3/classifiers/{classifier_id}` con il seguente comando cURL, che carica i dati di formazione e aggiorna il classificatore "dogs\_1941945966":
    - Sostituisci `{api-key}` con le credenziali del servizio copiate nel primo passo. 
    - Sostituisci `{classifier_id}` con l'ID del classificatore che desideri aggiornare.
    - Modifica l'ubicazione di `{class}_positive_examples` in modo che punti a dove hai salvato i file .zip.

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Il classificatore "dogs" esistente vine sostituito da quello riaggiornato con lo stesso classifier_id. La risposta elenca la nuova serie di classi e lo stato corrente. Ad esempio: 

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    La formazione inizia immediatamente. Quando il nuovo classificatore è disponibile, lo stato viene modificato in `ready`.

    Non immettere altre richieste di riaggiornamento finché lo stato corrente non è diventato `ready`. Più richieste per riaggiornare una classificatore portano a che un solo riaggiornamento abbia effetto. Una data/ora denominata `retrained` mostra l'ultima volta in cui il classificatore ha completato il riaggiornamento. Se richiami il metodo `/classify` mentre il classificatore viene riaggiornato, viene utilizzata la vecchia definizione del classificatore.
    {: tip}
1.  Controlla lo stato di formazione periodicamente finché non visualizzi uno stato di `ready`. Sostituisci `{api  key}` e `{classifier_id}` con le tue informazioni:

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Passo 4: classificazione di un'immagine con un classificatore personalizzato
{: #classify}

Quando il nuovo classificatore è pronto, richiamalo per vederne l'esecuzione.

1.  Crea un file JSON denominato `myparams.json` che include i parametri della tua chiamata, come `classifier_id` sia per il nuovo classificatore che per il classificatore del modello generale (che utilizza il classifier_id `default`). Un file JSON semplice potrebbe essere simile a quanto segue:

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  Scarica <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Utilizza il metodo `POST /v3/classify` per verificare il tuo classificatore personalizzato. Il seguente esempio classifica l'immagine `dogs.jpg` nel classificatore "dogs\_1941945966":
    - Sostituisci `{api-key}` con le credenziali del servizio copiate nel primo passo. 

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Per classificare solo con il modello generale integrato, ometti il parametro `parameters`.
    {: tip}

    La risposta include i classificatori, le loro classi e un punteggio per ogni classe. I punteggi varano tra 0-1, con un punteggio più alto che indica una maggiore correlazione. Le chiamate `/v3/classify` omettono le classi con punteggio basso per impostazione predefinita se vengono identificate classi con punteggio alto. Puoi impostare un punteggio minimo da visualizzare specificando un valore con virgola mobile per il parametro `threshold` nella tua chiamata.

    ```json
    {
      "images": [
    {
          "classifiers": [
        {
              "classes": [
            {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [
            {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  Controlla i tuoi risultati.

Hai finito! Hai creato, formato ed eseguito le query di un classificatore personalizzato con {{site.data.keyword.visualrecognitionshort}}.

### Eliminazione del tuo classificatore personalizzato

Potresti voler eliminare il tuo classificatore personalizzato per iniziare a sviluppare la tua applicazione con un'istanza pulita.

Per eliminare il classificatore, richiama il metodo `DELETE /v3/classifiers/{classifier_id}`. Sostituisci `{api_key)` e `classifier_id` con le tue informazioni:

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## Passi successivi

Ora che hai una conoscenza di base di come utilizzare i classificatori personalizzati, puoi approfondire:

- Ulteriori informazioni su [Best practices for custom classifiers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Leggi le informazioni sull'API in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attribuzioni
{: #attributions}

Tutte le immagini utilizzate in questa pagina sono prese da Flikr e utilizzate con la [licenza Creative Commons Attribution 2.0 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Non sono state apportate modifiche a queste immagini. 
