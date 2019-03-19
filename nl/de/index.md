---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition service,Face model,Food model,Explicit,Text recognition,Visual Recognition use cases

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

# Produktinformationen
{: #index}

Am 2. April 2018 wurden die Identitätsinformationen in der Antwort auf Aufrufe des Modells "Gesicht" entfernt. Die Identitätsinformationen beziehen sich auf den Namen der Person, den Score und die Knowledge Graph-Funktion 'type_hierarchy'. Details zum erweiterten Modell "Gesicht" finden Sie in den [Releaseinformationen](/docs/services/visual-recognition?topic=visual-recognition-release-notes#2april2018).
{: deprecated}

Der Service {{site.data.keyword.visualrecognitionfull}} verwendet Deep-Learning-Algorithmen, um Bilder auf Szenen, Objekte, Gesichter und andere Inhalte hin zu untersuchen. Die Antwort enthält Schlüsselwörter, die Informationen zum Inhalt bereitstellen.
{: shortdesc}

## Verfügbare Modelle
{: #models}

Mit einer Gruppe von integrierten Modellen werden sehr präzise Ergebnisse ohne Training zur Verfügung gestellt:

- [Modell **General**](/docs/services/visual-recognition?topic=visual-recognition-customizing#general-model) (Allgemein): Standard-Klassifizierung aus Tausenden von Klassen.
- [Modell **Face**](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#detect-faces) (Gesicht): Gesichtsanalyse mit Alter und Geschlecht.
- Modell **Explicit** (unangemessene Inhalte): Gibt an, wenn ein Bild für die allgemeine Verwendung ungeeignet ist.
- Modell **Food** (Lebensmittel): Speziell für Bilder von Lebensmitteln.
- Modell **Text** (Privat-Beta): Textextraktion aus Bildern natürlicher Szenen. [Fordern Sie Zugriff an ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://datasciencex.typeform.com/to/nU6efl){: new_window}.

Sie können auch [angepasste Modelle](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) trainieren, um spezialisierte Klassen zu erstellen.

## Hinweise zur Verwendung des Service
{: #language-support-how-to}

Die folgende Abbildung zeigt den Prozess der Erstellung und Verwendung von {{site.data.keyword.visualrecognitionshort}}:

![Beschreibt den Verarbeitungsablauf des {{site.data.keyword.visualrecognitionshort}}-Service vom Vorbereiten, Trainieren und Klassifizieren der Bilder bis zum Anzeigen der Ergebnisse.](images/visual-recognition-process-110717.svg)


## Anwendungsfälle
{: #language-support-use-cases}

Der {{site.data.keyword.visualrecognitionshort}}-Service kann für verschiedenste Anwendungsfälle und Branchen verwendet werden, wie z. B.:

- **Fertigung:** Einsatz der Bildverarbeitung in der Fertigung, um sicherzustellen, dass die Produkte richtig auf der Fertigungslinie positioniert werden.
- **Sichtprüfung:** Visuelle Prüfung der Einhaltung von Vorgaben oder Prüfung auf Abnutzung/Schäden bei Flotten von LKWs, Flugzeugen oder Windkraftanlagen und Trainieren von benutzerdefinierten Modellen, um zu ermitteln, wie Schäden aussehen.
- **Versicherung:** Rasche Bearbeitung von Leistungsansprüchen durch Verwendung von Bildern zur Klassifizierung der Ansprüche in verschiedene Kategorien.
- **Social Listening:** Verwendung von Bildern Ihrer Produktlinien oder Ihres Logos, um zu verfolgen, was über Ihr Unternehmen in den sozialen Medien geschrieben wird.
- **Social Commerce:** Verwendung eines Bilds mit einem Gericht auf einem Teller, um ein Restaurant zu finden, in dem das Gericht angeboten wird (mit entsprechenden Bewertungen), und Verwendung eines Urlaubsfotos, um ähnliche Reiseempfehlungen zu erhalten.
- **Einzelhandel:** Verwendung eines Fotos mit bevorzugter Kleidung, um Geschäfte zu finden, die entsprechende Produkte vorrätig oder im Angebot haben, und Verwendung eines Reisefotos, um Einzelhandelsempfehlungen in der Nähe zu erhalten.
- **Schulung:** Erstellung von bildbasierten Anwendungen zur Schulung über Taxonomien.
