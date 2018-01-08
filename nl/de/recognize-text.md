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

# Texterkennung in natürlichen Szenen

Sie können das Beta-Textmodell verwenden, um englischen Text in Bildern zu erkennen. Das Textmodell dient primär zur Erkennung von Legendentext in Bildern, nicht von umfangreicherem Text in Dokumenten.

Das Textmodell ist ein Beta-Feature und nicht für den Einsatz in einer Produktionsumgebung konzipiert. Weitere Informationen finden Sie im Abschnitt "Beta-Features" in den [Releaseinformationen](/docs/services/visual-recognition/release-notes.html#beta).
{: tip}

Das Textmodell ist am besten für die Verarbeitung kurzer Textfolgen geeignet. Häufig wird das Textmodell z. B. zum Lesen von Verkehrs- und Hinweisschildern verwendet.

![Verkehrs-/Hinweisschild mit einem Rahmen um die erkannten Wörter](images/road-sign-text-detection.png)

![Im Bild mit dem Verkehrs-/Hinweisschild erkannte Wörter und Verlässlichkeitsscores](images/road-sign-text-response.png)

Die weißen Felder stellen alle Wörter dar, die von dem Modell im Bild erkannt wurden.

## Antwort

Die Antwort enthält die erkannte Zeichenfolge und jedes Wort in der Zeichenfolge wird mit folgenden Informationen identifiziert:

- Das erkannte Wort.
- Ein Score, der die Verlässlichkeit oder Richtigkeit des erkannten Wortes angibt.
- Die Position des Rahmens um das Wort. Der Rahmen gibt an, wo sich das Wort im Bild befindet.
- Eine Zeilennummer, die angibt, wo das Wort erkannt wurde.

## Richtlinien für bessere Ergebnisse bei der Texterkennung

Text in Bildern wird besser erkannt, wenn er den folgenden Richtlinien entspricht:

- Der Text besteht primär aus vollständigen Wörtern und nicht aus beliebigen Buchstabenfolgen (z. B. Produktcodes). Das Modell erkennt eher Wörter als einzelne Zeichen und berücksichtigt u. U. "Wörter" aus Einzelzeichen oder Zahlen nicht.
- Der Text liegt in einer Standardschrift und nicht einer speziellen Schriftart vor. Text auf Kfz-Kennzeichen oder Filmplakaten wird möglicherweise nicht erkannt. Auch handschriftlicher Text wird wahrscheinlich nicht erkannt.
- Der Text macht mindestens 5% des Bilds aus.
- Der Text ist nicht mehr als 45 Grad aus der Horizontalen geneigt. Das Beta-Textmodell liest EXIF-Tags und dreht Bilder. Für einen hohen Durchsatz ist es aber besser, wenn Sie nur Bilder senden, die nicht von dem Service gedreht werden müssen (EXIF-Tag **Orientation** ist auf `1` gesetzt).
- Das Textmodell ist für Wörter in englischer Sprache trainiert. Text in anderen Sprachen wird wahrscheinlich nicht erkannt.

## Nächste Schritte

Machen Sie sich im [API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window} mit der API vertraut.

Wenn Sie Fragen oder Kommentare zum Textmodell haben, wenden Sie sich an Kevin Gong (kgong@us.ibm.com).

---

Wechseln Sie zur [Hauptdokumentation](/docs/services/visual-recognition/index.html).
