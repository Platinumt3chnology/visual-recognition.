---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-17"

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

# Text in einem Bild erkennen
{: #tutorial-recognize-text}

Dieses Lernprogramm führt Sie durch die Verwendung des ersten Aufrufs mit dem {{site.data.keyword.visualrecognitionshort}}-Beta-Textmodell zur Erkennung von englischem Text in einem Bild.
{: shortdesc}

Das Textmodell ist eine Privat-Betafunktion. Sie müssen über die Berechtigung von {{site.data.keyword.IBM_notm}} verfügen, um Aufrufe an das Modell durchzuführen. [Fordern Sie Zugriff an ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Weitere Informationen zu Beta-Funktionen finden Sie in den [Releaseinformationen](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

## Vorbereitende Schritte
{: #tutorial-recognize-text-prerequisites}

1.  Wechseln Sie zur Seite [{{site.data.keyword.visualrecognitionshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/visual-recognition){: new_window} im {{site.data.keyword.Bluemix_notm}}-Katalog.
    1.  Registrieren Sie sich entweder für ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
    1.  Klicken Sie auf **Erstellen**.
- Kopieren Sie die Berechtigungsnachweise, um sich für Ihre Serviceinstanz zu authentifizieren:
    1.  Klicken Sie auf **Anzeigen**, um Ihre Berechtigungsnachweise anzuzeigen.
    1.  Kopieren Sie den Wert für **API key** (API-Schlüssel).

## Schritt 1: Text in einem Bild erkennen
{: #tutorial-recognize-text-recognize-text}

1.  Geben Sie folgenden Aufruf aus, um Text in [einem Bild ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window} zu erkennen. Ersetzen Sie `{your_api_key}` (Ihren API-Schlüssel) durch den API-Schlüsselwert, den Sie zuvor kopiert haben.

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    Die Antwort enthält den erkannten Text und die Positionen von Wörtern im Text mit einem Konfidenzscore für jedes Wort. Anhand der Positionsdaten können Rahmen um die Wörter gezogen werden.

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

## Nächste Schritte

Sie haben nun ein grundlegendes Verständnis für die Erkennung von Text in einem Bild. Unter den folgenden Links können Sie sich weiter informieren.

- Lesen Sie die [Übersicht](/docs/services/visual-recognition?topic=visual-recognition-recognize-text#recognize-text).
- Erkunden Sie die Methoden für Textmodelle in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}.

### Bildnachweis
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window} von [Lubo Minar ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://unsplash.com/@bubo){: new_window} in [Unsplash ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}. An diesem Bild wurden keine Änderungen vorgenommen.
