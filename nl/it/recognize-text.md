---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# Riconoscimento del testo in scene naturali

Utilizza il modello di testo beta per rilevare e riconoscere il testo in inglese nelle immagini. Il modello di testo è progettato per riconoscere il testo nella scena stampato nelle immagini invece del testo denso nei documenti.

Il modello di testo è una funzione beta e non è pensato per l'utilizzo in un ambiente di produzione. Per ulteriori informazioni, consulta "Funzioni beta" nelle [Note sulla release](/docs/services/visual-recognition/release-notes.html#beta).
{: tip}

Il modello di testo funziona in modo migliore su stringhe di testo brevi. Ad esempio, un utilizzo comune del modello di testo è di leggere i segnali stradali.

![Segnale stradale con riquadri di delimitazione intorno a parole rilevate](images/road-sign-text-detection.png)

![Parole e punteggi di confidenza rilevati nell'immagine del segnale stradale](images/road-sign-text-response.png)

I riquadri bianchi illustrano ogni parola che il modello ha rilevato nell'immagine.

## La risposta

La risposta include la stringa rilevata e ogni parola all'interno di questa stringa vene identificata con le seguenti informazioni:

- La parola rilevata
- Un punteggio che indica la confidenza nell'accuratezza della parola rilevata.
- L'ubicazione del riquadro di delimitazione intorno alla parola. Il riquadro indica dove la parola viene posizionata nell'immagine.
- Un numero di riga in cui è stata rilevata la parola.

## Linee guida per un buon riconoscimento del testo 

Il testo nelle immagini viene riconosciuto in modo migliore quando si rispettano queste linee guida:

- Il testo è formato principalmente da parole complete, non da stringhe di lettere come i codici prodotti. Il modello riconosce le parole invece dei caratteri individuali e potrebbe scartare le singole lettere delle "parole" o i numeri.
- Il testo è stampato con un font standard, non con uno altamente stilizzato. Ad esempio, il testo nelle targhe o nei titoli dei poster dei film potrebbe non venire riconosciuto. Allo stesso modo, il testo scritto a mano potrebbe non essere riconosciuto.
- Il testo occupa almeno il 5% dell'immagine.
- Il testo è inclinato a non più di 45 gradi dall'orizzontale. Il modello di testo beta legge le tag EXIF e ruota le immagini. Tuttavia, per una migliore velocità di trasmissione, invia le immagini che non devono essere ruotate dal servizio (la tag **Orientation** EXIF è impostata su `1`).
- Il modello di testo viene formato su parole in lingua inglese. Il testo in altre lingue probabilmente non sarà riconosciuto.

## Passi successivi

Prendi familiarità con l'API in [API explorer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window}

Se hai domande o commenti sul modello di testo, contatta Kevin Gong all'indirizzo kgong@us.ibm.com.

---

Vai alla [documentazione](/docs/services/visual-recognition/index.html) principale.
