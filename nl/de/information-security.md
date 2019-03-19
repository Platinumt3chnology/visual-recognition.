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

# Informationssicherheit
{: #information-security}

IBM ist bestrebt, unseren Kunden und Partnern innovative Datenschutz-, Sicherheits- und Governance-Lösungen zur Verfügung zu stellen.
{: shortdesc}

**Hinweis:**
Jeder Kunde ist für die Einhaltung der geltenden Gesetze und Vorschriften, einschließlich der Datenschutz-Grundverordnung (DSGVO) der Europäischen Union selbst verantwortlich. Es obliegt allein den Kunden, sich von kompetenter juristischer Stelle zu Inhalt und Auslegung aller relevanten Gesetze und Vorschriften beraten zu lassen, die ihre Geschäftstätigkeit und die von ihnen eventuell einzuleitenden Maßnahmen zur Einhaltung dieser Gesetze und Vorschriften betreffen.

Die hierin beschriebenen Produkte, Services und sonstigen Funktionen eignen sich nicht für alle Kundensituationen und sind möglicherweise nur eingeschränkt verfügbar. IBM erteilt keine Rechts- oder Steuerberatung und gibt keine Garantie bezüglich der Konformität von IBM Produkten oder Services mit den geltenden Gesetzen und Vorschriften. Sie benötigen GDPR-Unterstützung für erstellte {{site.data.keyword.cloud}} {{site.data.keyword.watson}}-Ressourcen?

- Innerhalb der Europäischen Union: Siehe [Unterstützung für in der Europäischen Union erstellte IBM Cloud Watson-Ressourcen anfordern](/docs/services/watson?topic=watson-gdpr-sar#request-EU).
- Außerhalb der Europäischen Union: Siehe [Unterstützung für Ressourcen außerhalb der Europäischen Region anfordern](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU).

## EU-Datenschutz-Grundverordnung (DSGVO)
{: #gdpr}

IBM ist bestrebt, unseren Kunden und Partnern innovative Datenschutz-, Sicherheits- und Governance-Lösungen zur Verfügung zu stellen, um sie auf ihrem Weg zur Einhaltung der DSGVO zu unterstützen.

Erfahren Sie mehr zu den Bestrebungen von IBM zur Umsetzung der DSGVO und unseren eigenen DSGVO-Funktionen und -Angeboten für Ihre Compliance-Bemühungen, indem Sie [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/gdpr) klicken.{: new_window}.

## Daten in {{site.data.keyword.visualrecognitionshort}} kennzeichnen und löschen
{: #gdpr-visrec}

### DSGVO-Sicherheitsmigration
{: #gdpr-visrec-update}

- Keine {{site.data.keyword.visualrecognitionfull}}-Serviceinstanz, die vor dem **22. Mai 2018** erstellt wurde, eignet sich für Kunden, die die Datenschutz-Grundverordnung (Verordnung (EU) 2016/679 ("DSGVO") einhalten müssen.
- Kunden mit der Anforderung zur Einhaltung der DSGVO müssen [auf eine neue {{site.data.keyword.visualrecognitionshort}}-Serviceinstanz](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) migrieren, die ab dem **22. Mai 2018** zur Verfügung steht, und der neuen Vereinbarung für den {{site.data.keyword.visualrecognitionshort}}-Service zustimmen.
- Kunden müssen einen neuen {{site.data.keyword.visualrecognitionshort}}-Service bereitstellen und *neue Authentifizierungsschlüssel* generieren, um den neuen {{site.data.keyword.visualrecognitionshort}}-Service nutzen zu können.
- Stellt ein Kunde den neuen {{site.data.keyword.visualrecognitionshort}}-Service nicht bereit, bestätigen Sie, dass IBM keine personenbezogenen Daten im Auftrag des Kunden verarbeitet, die der DSGVO unterliegen.
- Daten von Kunden, die nicht zwischen dem 22. Mai 2018 und dem 1. Oktober zum neuen {{site.data.keyword.visualrecognitionshort}}-Service wechseln, werden gelöscht.

### Daten kennzeichnen

Wenn Sie die Daten eines einzelnen Kunden aus einer {{site.data.keyword.visualrecognitionshort}}-Serviceinstanz mit mehreren Kunden löschen müssen, müssen Sie zuerst diese Daten mit einer eindeutigen Kunden-ID verknüpfen, und zwar für jede Einzelperson, die Daten zur Verfügung gestellt haben könnte.

Zur Angabe der Kunden-ID für jegliche Daten, die mit der Methode **Create a classifier** (Klassifikationsmerkmal erstellen) gesendet werden, schließen Sie die Eigenschaft **X-Watson-Metadata: customer_id** in den Anforderungsheader ein. Im folgenden Beispiel wird die Kunden-ID `my_ID` mit einer Anforderung verknüpft:

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

Mehrbytezeichen für die Zeichenfolge der Kunden-ID werden unterstützt. Die Zeichen müssen sowohl während des Trainings in der Kopfzeile als auch während des Löschvorgangs im Abfrageparameter URL-codiert sein. Die ID kann alphanumerische Zeichen und Unterstreichungszeichen (``_``) enthalten. Folgende Zeichen werden nicht unterstützt: ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : .  + Leerzeichen``.

Für die Erstellung von Werten für die Kunden-ID sind Sie verantwortlich, ebenso dafür, dass jede ID eindeutig ist.
{: important}

### Gekennzeichnete Daten löschen

Zum Löschen sämtlicher Daten, die mit einer Kunden-ID verknüpft sind, verwenden Sie die Methode **Delete labeled data** (Gekennzeichnete Daten löschen). Übergeben Sie die Zeichenfolge `customer_id={id}` als Abfrageparameter mit der Anforderung. Im folgenden Beispiel werden alle Daten für die Kunden-ID `my_ID` gelöscht:

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

Die Methode **Delete labeled data** (Gekennzeichnete Daten löschen) löscht alle Daten, die mit der angegebenen Kunden-ID verknüpft sind, unabhängig von der Methode, mit der die Informationen hinzugefügt wurden. Die Methode hat keine Auswirkungen, wenn mit der Kunden-ID keine Daten verknüpft sind.

Löschanforderungen werden im Stapelbetrieb verarbeitet, der Vorgang kann bis zu 24 Stunden dauern.
{: tip}

### Unterstützung
{: #gdpr-visrec-support}

Bei Fragen wenden Sie sich an Ihren Kundenbeauftragten oder suchen Sie direkte Unterstützung bei [https://ibm.biz/ibmcloudsupport ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") ](https://ibm.biz/ibmcloudsupport){: new_window}.
