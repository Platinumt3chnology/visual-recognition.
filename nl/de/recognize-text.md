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

# Texterkennung in natürlichen Szenen (Beta)
{: #recognize-text}

Mit dem {{site.data.keyword.visualrecognitionshort}} Beta-Textmodell können Sie englischen Text in Bildern erkennen. Das Textmodell dient zur Erkennung von Szenentext in Bildern, nicht der Erkennung von umfangreicherem Text in Dokumenten.

Das Textmodell ist eine Privat-Betafunktion. Sie müssen über die Berechtigung von {{site.data.keyword.IBM_notm}} verfügen, um Aufrufe an das Modell durchzuführen.[Fordern Sie Zugriff an ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Weitere Informationen zu Beta-Funktionen finden Sie in den [Releaseinformationen](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Das Textmodell ist am besten für die Verarbeitung kurzer Textfolgen geeignet. Eine häufige Verwendung des Textmodells ist beispielsweise das Lesen von Schildern.

![Straßenschild mit Rahmen um die erkannten Wörter. Foto von Ashim D’Silva in Unsplash](images/walk-signal-detection.png) ![Bilder mit Wörtern, die auf einem Straßenschild erkannt wurden, und Konfidenzscores](images/walk-signal-response.png)

Die weißen Felder stellen alle Wörter dar, die das Modell im Bild erkannt hat.

## Antwort
{: #recognize-text-response}

Die Antwort enthält die erkannte Zeichenfolge und jedes Wort in der Zeichenfolge wird mit folgenden Informationen identifiziert:

- Das erkannte Wort.
- Ein Score für die Konfidenz der Worterkennung.
- Die Position des Rahmens um das Wort. Der Rahmen gibt an, wo sich das Wort im Bild befindet.
- Eine Zeilennummer, die angibt, wo das Wort erkannt wurde.

## Richtlinien für bessere Ergebnisse bei der Texterkennung
{: #recognize-text-guidelines}

Text in Bildern wird besser erkannt, wenn er den folgenden Richtlinien entspricht:

- Der Text besteht primär aus vollständigen Wörtern und nicht aus beliebigen Buchstabenfolgen (z. B. Produktcodes). Das Modell erkennt Wörter, nicht einzelne Zeichen, und verwirft u. U. "Wörter" aus Einzelbuchstaben oder Zahlen.
- Der Text liegt in einer Standardschrift und nicht einer speziellen Schriftart vor. Text auf Kfz-Kennzeichen oder Filmplakaten wird möglicherweise nicht erkannt. Auch handschriftlicher Text wird wahrscheinlich nicht erkannt.
- Das Textmodell ist hauptsächlich für Wörter in englischer Sprache trainiert. Text in anderen Sprachen wird mit einiger Wahrscheinlichkeit nicht erkannt.

## Nächste Schritte
{: #recognize-text-next-steps}

- [Aufruf ausführen](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text), um Text in einem Bild zu erkennen.
- Machen Sie sich in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window} mit der API vertraut.
