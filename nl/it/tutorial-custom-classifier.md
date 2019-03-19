---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Creazione di un modello personalizzato
{: #tutorial-custom-classifier}

Dopo aver analizzato un'immagine nell'"Esercitazione introduttiva", sei pronto a formare e creare un modello personalizzato. Con un modello personalizzato, puoi formare il servizio {{site.data.keyword.visualrecognitionshort}} per classificare le immagini per soddisfare le tue esigenze di business.
{: shortdesc}

## Passo 1:  Copia le tue credenziali
{: #copy-credentials}

Utilizza le credenziali copiate nell'"Esercitazione introduttiva." Se non hai creato un'istanza del servizio, esegui questi passi nella sezione [Prima di cominciare](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites).

## Passo 2: Creazione di un modello personalizzato
{: #create}

{{site.data.keyword.visualrecognitionshort}} può apprendere dalle immagini di esempio che carichi per creare un nuovo modello con più sfaccettature. Ogni file di esempio viene formato da altri file in tale chiamata e gli esempi positivi vengono archiviati come classi. Queste classi vengono raggruppate per definire un solo modello e restituiscono i propri punteggi. I file di esempio negativi non vengono archiviati come classi.

1.  Scarica i file di formazione di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>.
1.  Richiama il metodo `POST /v3/classifiers` con il seguente comando, che carica i dati di formazione e crea un modello personalizzato `dogs`:
    - Sostituisci `{your_api_key}` con le credenziali del servizio che hai copiato nel primo passo.
    - Modifica l'ubicazione di `{class}_positive_examples` in modo che punti a dove hai salvato i file .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    I nomi file di esempio positivi richiedono un suffisso `_positive_examples`. In questo esempio, i nomi file sono `beagle_positive_examples`, `goldenretriever_positive_examples` e `husky_positive_examples`. Il prefisso (beagle, goldenretriever e husky) viene restituito come nome della classe.
    {:tip }

    La risposta include un nuovo stato e ID del classificatore, ad esempio:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
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
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  Controlla lo stato di formazione periodicamente finché non visualizzi uno stato di `ready`. La formazione inizia immediatamente e deve finire prima che tu possa eseguire una query del modello. Sostituisci `{your_api_key}` e `{classifier_id}` con le tue informazioni:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Passo 3: Aggiornamento di un modello personalizzato esistente
{: #tutorial-custom-classifier-update}

Puoi aggiornare un modello personalizzato aggiungendo classi al modello oppure aggiungendo immagini a una classe esistente. Qui, migliori il modello che hai creato nel passo 2 aggiungendo una classe *Dalmatian* ai tipi di cani che possono essere classificati. Inoltre aggiungi le immagini di gatti alla serie di esempio negativa per il modello personalizzato "dogs".

1.  Scarica i file di formazione di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>.
1.  Richiama il metodo `POST /v3/classifiers/{classifier_id}` con il seguente comando cURL, che carica i dati di formazione e aggiorna il modello personalizzato "dogs\_1941945966":
    - Sostituisci `{your_api_key}` con le credenziali del servizio che hai copiato nel primo passo.
    - Sostituisci `{classifier_id}` con l'ID del modello personalizzato che desideri aggiornare.
    - Modifica l'ubicazione di `{class}_positive_examples` in modo che punti a dove hai salvato i file .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    Il modello personalizzato "dogs" esistente viene sostituito da quello di cui è stata rieseguita la formazione con lo stesso classifier_id. La risposta elenca la nuova serie di classi e lo stato corrente. Ad esempio:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    La formazione inizia immediatamente. Quando il nuovo classificatore è disponibile, lo stato viene modificato in `ready`.

    Non immettere altre richieste di riesecuzione della formazione finché lo stato corrente non è diventato `ready`. Più richieste di riesecuzione della formazione di un modello producono l'esecuzione di una singola riesecuzione della formazione. Una data/ora denominata `updated` mostra la data/ora del più recente aggiornamento del modello. Se richiami il metodo `/classify` mentre viene rieseguita la formazione del modello, viene utilizzata la vecchia definizione del modello.
    {: tip}
1.  Controlla lo stato di formazione periodicamente finché non visualizzi uno stato di `ready`. Sostituisci `{your_api_key}` e `{classifier_id}` con le tue informazioni:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## Passo 4: Classificazione di un'immagine con un modello personalizzato
{: #tutorial-custom-classifier-classify}

Quando il nuovo modello è pronto, richiamalo per vedere come funziona.

1.  Scarica <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>.
1.  Utilizza il metodo `POST /v3/classify` per verificare il tuo modello personalizzato. Il seguente esempio classifica l'immagine `dogs.jpg` sia rispetto al modello personalizzato "dogs\_1941945966" sia rispetto al modello General `default` integrato.
    - Sostituisci `{your_api_key}` con le credenziali del servizio che hai copiato nel primo passo.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    Per classificare solo rispetto al modello General integrato, ometti il parametro `classifier_ids`.
    {: tip}

    La risposta include i classificatori (modelli), le loro classi e un punteggio per ogni classe. I punteggi varano tra 0-1, con un punteggio più alto che indica una maggiore correlazione. Le chiamate `/v3/classify` omettono le classi con punteggio basso per impostazione predefinita se vengono identificate classi con punteggio alto. Puoi impostare un punteggio minimo da visualizzare specificando un valore con virgola mobile per il parametro `threshold` nella tua chiamata.

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  Controlla i tuoi risultati.

Hai finito! Hai creato, formato ed eseguito le query di un modello personalizzato con {{site.data.keyword.visualrecognitionshort}}.

### Eliminazione del tuo modello personalizzato
{: #tutorial-custom-classifier-delete}

Potresti voler eliminare il tuo modello personalizzato per iniziare a sviluppare la tua applicazione con un'istanza pulita.

Per eliminare il modello , richiama il metodo `DELETE /v3/classifiers/{classifier_id}`. Sostituisci `{your_api_key)` e `classifier_id` con le tue informazioni:

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## Passi successivi
{: #tutorial-custom-classifier-next-steps}

Ora che hai una conoscenza di base di come utilizzare i modelli personalizzati, puoi approfondire:

- Ulteriori informazioni su [Best practices for custom classifiers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Leggi le informazioni sull'API nella [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Attribuzioni
{: #tutorial-custom-classifier-attributions}

Tutte le immagini utilizzate in questa pagina sono prese da Flikr e utilizzate con la [licenza Creative Commons Attribution 2.0 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Non sono state apportate modifiche a queste immagini.
