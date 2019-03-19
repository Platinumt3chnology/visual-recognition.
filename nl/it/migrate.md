---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Migrazione
{: #migrating}

Per eseguire la migrazione dei tuoi modelli correnti (classificatori), esegui il provisioning di una nuova istanza del servizio {{site.data.keyword.visualrecognitionshort}}. Per i modelli personalizzati, riesegui la formazione del modello creando un altro modello (classificatore) con le immagini dal modello precedente.
{: shortdesc}

Le istanze del servizio {{site.data.keyword.visualrecognitionfull}} create **prima** del 23 maggio 2018 hanno un URL host `gateway-a.watsonplatform.net`. Devi eseguire la migrazione di queste istanze a una nuova istanza del servizio {{site.data.keyword.visualrecognitionshort}} per continuare a utilizzarle.
{: deprecated}

1.  Crea un'altra istanza del servizio {{site.data.keyword.visualrecognitionshort}}:
    1.  Vai alla pagina [{{site.data.keyword.visualrecognitionshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/visual-recognition){: new_window} nel catalogo.
    1.  Seleziona un piano e fai clic su **Crea**.
1.  Copia le nuove credenziali per autenticarti presso la tua istanza del servizio:
    1.  Nella pagina **Gestisci**, fai clic su **Visualizza credenziali**.
    1.  Copia il valore `Chiave API`.
1.  [Crea nuovamente e forma i tuoi modelli personalizzati](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) nella tua istanza del servizio {{site.data.keyword.visualrecognitionshort}}.
1.  Modifica il modo in cui richiami il tuo servizio.

    Fornisci una token di accesso o una chiave IAM (Identity and Access Management) per la tua istanza del servizio. I token forniscono una sicurezza maggiore perché devono essere rinnovati periodicamente e supportano le richieste senza le tue credenziali del servizio integrate in ogni chiamata. Le chiavi API utilizzano l'autenticazione di base e non scadono.

    - Per ulteriori informazioni sui token, vedi [Authenticating with IAM tokens](/docs/services/watson?topic=watson-iam#iam).
    - Per ulteriori informazioni sull'utilizzo di una chiave API, vedi la [guida di riferimento API](https://{DomainName}/apidocs/visual-recognition/#authentication).
