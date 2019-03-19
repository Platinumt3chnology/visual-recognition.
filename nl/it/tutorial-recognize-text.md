---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Riconoscimento del testo in un'immagine
{: #tutorial-recognize-text}

Questa esercitazione ti spiega come effettuare la tua prima chiamata con il modello Text beta {{site.data.keyword.visualrecognitionshort}} beta per rilevare e riconoscere il testo in inglese in un'immagine.
{: shortdesc}

Il modello Text è una funzione beta privata e devi avere l'autorizzazione da {{site.data.keyword.IBM_notm}} per effettuare le chiamate al modello. [Richiedi l'accesso![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Per ulteriori informazioni sulle funzioni beta, vedi [Note sulla release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Prima di iniziare
{: #tutorial-recognize-text-prerequisites}

1.  Vai alla pagina [{{site.data.keyword.visualrecognitionshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/visual-recognition){: new_window} nel catalogo {{site.data.keyword.Bluemix_notm}}.
    1.  Registrati per un account {{site.data.keyword.Bluemix_notm}} gratuito o accedi.
    1.  Fai clic su **Crea**.
- Copia le credenziali per autenticarti con la tua istanza del servizio:
    1.  Fai clic su **Mostra** per visualizzare le tue credenziali.
    1.  Copia il valore **Chiave API**.

## Passo 1: Riconosci il testo in un'immagine
{: #tutorial-recognize-text-recognize-text}

1.  Immetti la seguente chiamata per riconoscere il testo in [un'immagine
![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}. Sostituisci {your_api_key} con il valore di chiave API che hai copiato in precedenza.

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    La risposta include il testo riconosciuto e le ubicazioni delle parole nel testo, con un punteggio di attendibilità per ciascuna parola. Le informazioni sull'ubicazione possono essere utilizzate per tracciare delle caselle di delimitazione intorno alle parole.

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## Passi successivi

Hai una conoscenza di base di come riconoscere il testo in un'immagine. Esplora ulteriormente.

- Leggi la [panoramica](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-).
- Esplora i metodi del modello Text nella [guida di riferimento API
![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Attribuzioni
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} di [Lubo Minar ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://unsplash.com/@bubo){: new_window} su [Unsplash ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}.  Non sono state apportate modifiche a questa immagine.
