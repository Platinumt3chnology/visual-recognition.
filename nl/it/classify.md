---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

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

# Informazioni sui classificatori

Quando classifichi un'immagine, Visual Recognition restituisce una serie di classi trovate nell'immagine. Ricava queste informazioni dalle immagini su cui è preparato. Un classificatore è un gruppo di classi.

Visual Recognition include molti classificatori integrati che possono fornire risultati molto accurati senza dover fare la formazione. Puoi anche preparare classificatori personalizzati per creare classi specializzate.

Introduzione a Clarifai
> Il tipo di previsione si basa su quale modello esegui l'input. Ad esempio, se esegui l'input tramite il modello 'food', le previsioni restituite conterranno i concetti a conoscenza del modello 'food'. Se esegui il tuo input tramite il modello 'color', restituirà le previsioni sui colori dominanti nella tua immagine.

Clarifai
> Clarifai fornisce molti differenti modelli che 'vedono' il mondo in modo diverso. Un modello contiene un gruppo di concetti. Un modello visualizzerà solo i concetti che contiene.
>
> Alcune volte desideri avere un modello che vede il mondo nel tuo stesso modo. L'API ti consente di farlo. Puoi creare il tuo proprio modello e prepararlo con i tuoi propri concetti e immagini. Dopo averlo preparato per vedere come desideri, puoi utilizzarlo per prendere decisioni.

## Classificatori integrati

Visual Recognition include una serie di classificatori che forniscono risultati molto accurati senza la preparazione. I classificatori integrati correnti si chiamano `default`, `food` e `explicit`.

### Classificatore predefinito

Il classificatore predefinito restituisce le classi da migliaia di tag possibili organizzate in categorie e sottocategorie. Possono essere restituite le seguenti categorie di livello superiore: 

- Animali (inclusi uccelli, rettili, anfibi, ecc.)
- Persone e attività e informazioni orientate sulle persone
- Cibo (inclusi cibo cotto e bevande)
- Piante (inclusi alberi, arbusti, piante acquatiche, verdure)
- Sport
- Natura (inclusi vari tipi di formazioni naturali, strutture geologiche)
- Trasporti (terra, acqua, aria)
- E molto altro, inclusi arredi, frutti, strumenti musicali, strumenti, colori, gadget, dispositivi, strumenti, armi, costruzioni, strutture e oggetti sintetici, vestiti e indumenti e fiori, tra gli altri.

### Classificatore food

Sebbene il classificatore predefinito possa identificare i cibi e le bevande, puoi specificare il classificatore `food` integrato per...

### Classificatore explicit

Visual Recognition può classificare se un'immagine è inappropriata per l'utilizzo generale. Il classificatore `explicit` al momento identifica cosa può essere considerato come immagini pornografiche. Un'abbreviazione comune per questa classificazione viene denominata _NSFW_, che significa _non sicuro da utilizzare._

Un tratto sopra o sotto un certo numero non è una garanzia che l'immagine sia esplicita o meno. Tuttavia, puoi utilizzare la risposta come un filtro iniziale di un'immagine e effettuare ulteriore analisi da questo punto.

Risposta:
```json
{
  "images": [
    {
      "classifiers": [
        {
          "classes": [
            {
              "class": "not explicit",
              "score": 0.704
            }
          ],
          "classifier_id": "explicit",
          "name": "explicit"
        }
      ],
      "resolved_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png",
      "source_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png"
    }
  ],
  "images_processed": 1
}
```
{: codeblock}

## Combinazione dei classificatori


## Gerarchia della classe nella risposta

Il metodo `/v3/classify` classifica le immagini in una gerarchia di classi correlate. Ad esempio, una foto di un beagle potrebbe essere classificata come "animal" così correlata a "dog" e "beagle". Una corrispondenza positiva delle classi correlate, in questo caso "dog" e "beagle", rafforza il punteggio della risposta principale. In questo esempio, la risposta include tutte e tre le classi: "animal", "dog" e "beagle". Il punteggio della classe principale ("animal") viene rafforzato perché corrisponde alle classi correlate ("dog" e "beagle"). La classe principale è anche un "type\_hierarchy" per mostrare che è una classe principale della gerarchia.

## Linee guida per la classificazione di volume elevato

Ottimizza l'efficienza e le prestazioni del servizio nei seguenti modi quando invii molte immagini:

- Taglia o ridimensiona le tue immagini in 224 x 224 pixel. Il servizio è al momento ottimizzato per questa dimensione anche se potrebbe cambiare.
    - Taglia l'immagine se ha le proporzioni maggiori di 2:1 o inferiori di 1:2.
    - Prendi in considerazione di tagliare l'immagine in più immagini quadrate o includi solo il centro dell'immagine, a seconda di cosa sia più importante per l'utilizzo.
- Invia fino a 20 immagini in un solo file .zip. Non devi utilizzare alcuna compressione perché le immagini JPEG e PNG sono già file compressi.
- Utilizza il parametro **classifier_ids** per specificare solo i classificatori che desideri utilizzare.
- Sebbene il servizio legga le tag EXIF e ruoti le immagini, per una migliore velocità di trasmissione, invia le immagini che non devono essere ruotate dal servizio (la tag **Orientation** EXIF è impostata su `1`).
