---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# Sicurezza delle informazioni 
{: #information-security}

IBM si impegna a fornire ai nostri clienti e partner soluzioni innovative per la privacy, la sicurezza e la governance dei dati.
{: shortdesc}

**Avviso:**
è responsabilità dei clienti garantire la propria conformità alle varie leggi e normative, incluso il Regolamento generale sulla protezione dei dati (GDPR) dell'Unione europea. È responsabilità esclusiva dei clienti richiedere una consulenza legale qualificata per identificare e interpretare normative e regolamenti importanti che potrebbero influenzare le attività di business dei clienti ed eventuali azioni che i clienti dovranno intraprendere per rispettare la conformità a tali normative e regolamenti. 

I prodotti, i servizi e le altre funzionalità qui descritti non sono adatti per tutte le situazioni dei clienti e potrebbero avere una disponibilità limitata. IBM non fornisce consulenza legale, contabile o di controllo né dichiara o garantisce che i propri servizi o prodotti assicureranno che i clienti siano conformi ad eventuali norme di legge o regolamentari.
Se hai bisogno di richiedere il supporto GDPR per le risorse {{site.data.keyword.cloud}} {{site.data.keyword.watson}} che vengono create

- Nell'Unione europea, vedi [Requesting support for IBM Cloud Watson resources created in the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-EU).
- Fuori dall'Unione europea, vedi [Requesting support for resources outside the European Union](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU).

## Regolamento generale sulla protezione dei dati dell'Unione europea (GDPR)
{: #gdpr}

IBM si impegna a offrire ai nostri clienti e partner soluzioni innovative per la privacy, la sicurezza e la governance dei dati per assisterli nel loro percorso verso la conformità GDPR. 

È possibile trovare ulteriori informazioni sul percorso di preparazione verso la disponibilità GDPR e sulle nostre funzionalità e offerte GDPR che supportano il tuo percorso di conformità [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/gdpr){: new_window}.

## Etichettatura ed eliminazione dei dati in {{site.data.keyword.visualrecognitionshort}}
{: #gdpr-visrec}

### Migrazione della sicurezza del Regolamento generale sulla protezione dei dati (GDPR, General Data Protection Regulation)
{: #gdpr-visrec-update}

- Tutte le istanze del servizio {{site.data.keyword.visualrecognitionfull}} create prima del **22 maggio 2018** non sono adatte per i clienti che richiedono la conformità al Regolamento generale sulla protezione dei dati (GDPR, General Data Protection Regulation) dell'UE 2016/679.
- I clienti che sono soggetti al GDPR devono [eseguire la migrazione a una nuova istanza del servizio {{site.data.keyword.visualrecognitionshort}}](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) disponibile il **22 maggio 2018** e adottare il nuovo accordo per il servizio {{site.data.keyword.visualrecognitionshort}}.
- I clienti devono eseguire il provisioning di un nuovo servizio {{site.data.keyword.visualrecognitionshort}} e generare *nuove chiavi di autenticazione* per utilizzare il nuovo servizio {{site.data.keyword.visualrecognitionshort}}.
- Se un cliente non esegue il provisioning del nuovo servizio {{site.data.keyword.visualrecognitionshort}}, conferma che IBM non sta elaborando per suo conto dati personali che sono soggetti al GDPR.
- I dati dei clienti che non passano al nuovo servizio {{site.data.keyword.visualrecognitionshort}} tra il 22 maggio 2018 e il 1° ottobre 2018 verranno eliminati.

### Etichettatura dei dati

Se devi rimuovere i dati di un singolo cliente da un'istanza del servizio {{site.data.keyword.visualrecognitionshort}} con più clienti, devi prima associare tali dati a un ID cliente univoco per ciascuna persona che potrebbe aver fornito dati.

Per specificare l'ID cliente per eventuali dati inviati con il metodo **Create a classifier**, includi la proprietà **X-Watson-Metadata: customer_id** nell'intestazione della richiesta. Il seguente esempio associa l'ID cliente `my_ID` a una richiesta:

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

I caratteri a più byte sono supportati per la stringa ID cliente. I caratteri devono avere una codifica URL, sia nell'intestazione durante la formazione sia nel parametro query durante l'eliminazione. L'ID può contenere caratteri alfanumerici e di sottolineatura (``_``). Questi caratteri non sono supportati: ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + spazio``.

È tua responsabilità creare i valori ID cliente e garantire che ciascuno di essi sia univoco.
{: important}

### Eliminazione dei dati etichettati

Per eliminare tutti i dati associati all'ID cliente, utilizza il metodo **Delete labeled data**. Passi la stringa `customer_id={id}` come un parametro query con la richiesta. Il seguente esempio elimina tutti i dati per l'ID cliente `my_ID`:

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

Il metodo **Delete labeled data** elimina tutti i dati associati all'ID cliente specificato, indipendentemente dal metodo mediante il quale erano state aggiunte le informazioni. Il metodo non ha alcun effetto se non ci sono dati associati all'ID cliente.

Le richieste di eliminazione vengono elaborate in batch e il loro completamento potrebbe richiedere fino a 24 ore.
{: tip}

### Supporto
{: #gdpr-visrec-support}

Indirizza le domande al tuo rappresentante dell'account oppure contatta direttamente il supporto all'indirizzo [https://ibm.biz/ibmcloudsupport ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/ibmcloudsupport){: new_window}.
