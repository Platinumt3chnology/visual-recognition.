---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

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

# Riconoscimento del testo in scene naturali (Beta)
{: #recognize-text}

Utilizza il modello Text beta {{site.data.keyword.visualrecognitionshort}} per rilevare e riconoscere il testo in inglese nelle immagini. Il modello Text è progettato per riconoscere il testo della scena nelle immagini invece del testo più denso nei documenti.

Il modello Text è una funzione beta privata e devi avere l'autorizzazione da {{site.data.keyword.IBM_notm}} per effettuare le chiamate al modello. [Richiedi l'accesso![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Per ulteriori informazioni sulle funzioni beta, vedi [Note sulla release](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Il modello Text funziona in modo migliore su stringhe di testo brevi. Ad esempio, un utilizzo comune del modello Text è per leggere i segnali stradali.

![Segnale stradale con riquadri di delimitazione intorno alle parole riconosciute. Foto di Ashim D’Silva su Unsplash](images/walk-signal-detection.png) ![Parole e punteggi di attendibilità rilevati nell'immagine di segnale stradale](images/walk-signal-response.png)

Le caselle bianche illustrano ciascuna parola che il modello riconosce nell'immagine.

## La risposta
{: #recognize-text-response}

La risposta include la stringa rilevata e ogni parola all'interno di questa stringa vene identificata con le seguenti informazioni:

- La parola riconosciuta.
- Un punteggio che indica l'attendibilità nel riconoscimento della parola.
- L'ubicazione del riquadro di delimitazione intorno alla parola. Il riquadro indica dove la parola viene posizionata nell'immagine.
- Un numero di riga in cui è stata rilevata la parola.

## Linee guida per un buon riconoscimento del testo
{: #recognize-text-guidelines}

Il testo nelle immagini viene riconosciuto in modo migliore quando si rispettano queste linee guida:

- Il testo è formato principalmente da parole complete, non da stringhe di lettere come i codici prodotti. Il modello riconosce le parole invece dei caratteri individuali e potrebbe scartare "parole" o numeri di una sola lettera.
- Il testo è stampato con un font standard, non con uno altamente stilizzato. Ad esempio, il testo nelle targhe o nei titoli dei poster dei film potrebbe non venire riconosciuto. Allo stesso modo, il testo scritto a mano potrebbe non essere riconosciuto.
- Il modello Text viene formato principalmente su parole in lingua inglese. Il testo in altre lingue probabilmente non sarà riconosciuto.

## Passi successivi
{: #recognize-text-next-steps}

- [Effettua una chiamata](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text) per riconoscere il testo in un'immagine.
- Acquisisci dimestichezza con l'API nella [guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window}.
