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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Esercitazione introduttiva

Questa esercitazione ti guida attraverso l'utilizzo si alcuni classificatori integrati in {{site.data.keyword.visualrecognitionfull}} per classificare un immagine e poi rilevare i volti in essa.
{: shortdesc}

## Prima di iniziare 
{: #prerequisites}

- Crea un'istanza del servizio: 
    - {: download} Se stai visualizzando questo, hai creato la tua istanza del servizio. Ora ottieni le tue credenziali.
    - Crea un progetto da un servizio: 
        1.  Vai alla pagina {{site.data.keyword.watson}} Developer Console [Services ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Seleziona {{site.data.keyword.visualrecognitionshort}}, fai clic su **Add Services** e registrati per un account gratuito di {{site.data.keyword.Bluemix_notm}} o accedi.
        1.  Immetti `vision-tutorial` come nome del progetto e fai clic su **Create Project**.
- Copia le credenziali per autenticarti con la tua istanza del servizio:
    - {: download} Dal dashboard del servizio (che stai guardando):
        1.  Fai clic sulla scheda **Service credentials**.
        1.  Fai clic su **View credentials** in **Actions**.
        1.  Copia il valore api-key.
        {: download}
    - Dal tuo progetto **vision-tutorial**nella Developer Console, copia il valore `api-key` per `"visual_recognition"` dalla sezione **Credentials**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se utilizzi {{site.data.keyword.Bluemix_dedicated_notm}}, crea la tua istanza del servizio dalla pagina [{{site.data.keyword.visualrecognitionshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} nel catalogo. Per i dettagli su come trovare le tue credenziali del servizio, consulta [Credenziali del servizio per i servizi Watson ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Passo 1: classifica un'immagine
{: #classify}

1.  Scarica l'immagine di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Immetti il seguente comando per caricare l'immagine e classificarla con tutti i classificatori integrati:
    - Sostituisci `{api-key}` con le credenziali del servizio copiate precedentemente.
    - Modifica l'ubicazione di images\_file in modo che punti a dove hai salvato l'immagine.

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Se hai {{site.data.keyword.Bluemix_notm}} dedicato, questo endpoint `gateway-a.watsonplatform.net` potrebbe non essere quello del tuo servizio. Verifica l'`url` nella pagina **Service credentials** del tuo dashboard del servizio.
    {: tip}

    La risposta include il classificatore o il modello generale (che utilizza il classifier_id `default`), le classi identificate nell'immagine e un punteggio per ogni classe.

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
        {
              "classes": [
            {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    I punteggi di confidenza sono compresi nell'intervallo tra 0 e 1, con un punteggio più alto che indica una maggiore correlazione. Per impostazione predefinita, le chiamate `/v3/classify` non includono le classi con un punteggio inferiore a `0.5`.

## Passo 2: rileva i volti in un'immagine.
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}} può rilevare i volti nelle immagini. La risposta fornisce informazioni come l'ubicazione del volto nell'immagine e il genere e l'intervallo di età stimati per ogni volto.

Il servizio può anche identificare molte celebrità per nome e può fornire un *grafo della conoscenza* in modo che puoi aggregare concetti di livello superiore.

1.  Scarica l'immagine di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Immetti il seguente comando nel metodo `POST /v3/detect_faces` e carica e analizza l'immagine. Se utilizzi la tua propria immagine, la dimensione massima è 2 MB:
    - Sostituisci `{api-key}` con le credenziali del servizio copiate precedentemente.
    - Modifica l'ubicazione di images\_file in modo che punti a dove hai salvato l'immagine.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    La risposta include un'ubicazione, un'età stimata, il genere, l'identità e la gerarchia del tipo (se il servizio rileva tale volto) e un punteggio per ognuno.

    I punteggi varano tra 0-1, con un punteggio più alto che indica una maggiore correlazione. Vengono rilevati tutti i volti, ma per le immagini con più di 10 volti, i punteggi di confidenza di genere e età potrebbero restituire punteggi di 0.

    ```json
    {
      "images": [
    {
          "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Passi successivi

Hai una conoscenza di base di come utilizzare il classificatore predefinito integrato con {{site.data.keyword.visualrecognitionshort}}. Ora approfondisci:

- Ulteriori informazioni su come [creare un classificatore personalizzato](/docs/services/visual-recognition/tutorial-custom-classifier.html).
- Leggi le informazioni sull'API in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attribuzioni
{: #attributions}

- [Fruit basket ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://flic.kr/p/JPHES){: new_window} dall'utente Flikr [Ryan Edwards-Crewe ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.flickr.com/photos/ryanec/){: new_window} utilizzato in [Creative Commons Attribution 2.0 license ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Non sono state apportate modifiche a questa immagine. 
- [obama ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://bit.ly/1T0DCl9){: new_window} dall'utente Flikr [dcblog ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.flickr.com/photos/12863058@N08/){: new_window} utilizzato in [Creative Commons Attribution 2.0 license ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Non sono state apportate modifiche a questa immagine. 
