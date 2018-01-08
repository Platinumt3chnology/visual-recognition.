---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# Riconoscimento del testo in un'immagine

{: shortdesc}

## Prima di iniziare
{: #copy-credentials}

Utilizza le credenziali copiate nell'"Esercitazione introduttiva" per questa esercitazione. Se non hai creato un'istanza del servizio, esegui questi passi nella sezione [Prima di cominciare](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Passo 1: riconosci il testo in un'immagine
{: #recognize-text}

1.  Scarica l'immagine di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a> 
1.  Immetti il seguente comando nel metodo `POST /v3/recognize_text` e carica e analizza l'immagine. Se utilizzi la tua propria immagine, la dimensione massima è 2 MB:
    - Sostituisci `{api-key}` con le credenziali del servizio copiate precedentemente.
    - Modifica l'ubicazione di images\_file in modo che punti a dove hai salvato l'immagine.

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    La risposta include un'ubicazione, un'età stimata, il genere, l'identità e la gerarchia del tipo (se il servizio rileva tale volto) e un punteggio per ognuno.

    I punteggi varano tra 0-1, con un punteggio più alto che indica una maggiore correlazione. Vengono rilevati tutti i volti, ma per le immagini con più di 10 volti, i punteggi di confidenza di genere e età potrebbero restituire punteggi di 0.


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## Fasi successive

Hai una conoscenza di base di come utilizzare i classificatori predefiniti con {{site.data.keyword.visualrecognitionshort}}. Ora approfondisci:

- Leggi le informazioni sull'API in [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Attribuzioni
{: #attributions}

Tutte le immagini utilizzate in questa pagina sono prese da Flikr e utilizzate con la [licenza Creative Commons Attribution 2.0 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Non sono state apportate modifiche a queste immagini. 
