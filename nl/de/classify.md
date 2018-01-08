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

# Informationen zu Klassifikationsmerkmalen

Wenn Sie ein Bild klassifizieren, gibt Visual Recognition eine Reihe von Klassen zurück, die in dem Bild gefunden werden. Diese Informationen werden von den Bildern abgeleitet, mit deren Hilfe das Programm trainiert wurde. Ein Klassifikationsmerkmal bezeichnet eine Gruppe von Klassen.

Visual Recognition enthält verschiedene Klassifikationsmerkmale, die sehr präzise Ergebnisse liefern, ohne dass Sie das Programm hierfür trainieren müssen. Sie haben außerdem die Möglichkeit, benutzerdefinierte Klassifikationsmerkmale zu trainieren, um spezialisierte Klassen zu erstellen.

Einführung in Clarifai
> Die Art der Vorhersage hängt davon ab, durch welches Modell Sie die Eingabe verarbeiten lassen. Wenn Sie Ihre Eingabe beispielsweise durch das Modell "Lebensmittel" verarbeiten lassen, enthalten die vom Modell zurückgegebenen Vorhersagen Konzepte, die das Modell "Lebensmittel" kennt. Wenn Sie Ihre Eingabe durch das Modell "Farbe" verarbeiten lassen, gibt es Vorhersagen über die vorwiegenden Farben in Ihrem Bild zurück.

Clarifai
> Clarifai bietet zahlreiche verschiedene Modelle, die die Welt unterschiedlich "sehen". Ein Modell enthält eine Gruppe von Konzepten. Ein Modell sieht nur die Konzepte, die es enthält.
>
> Es gibt Fälle, da wünschten Sie sich, Ihr Modell würde die Welt genauso sehen wie Sie selbst. Die API gibt Ihnen die Möglichkeit hierzu. Sie können Ihr eigenes Modell erstellen und mit Ihren eigenen Bildern und Konzepten trainieren. Wenn Sie das Modell so trainieren, dass es so sieht, wie Sie es möchten, können Sie das Modell anschließend verwenden, um Vorhersagen zu treffen.

## Integrierte Klassifikationsmerkmale

Visual Recognition enthält eine Reihe von Klassifikationsmerkmalen, die auch ohne Training sehr präzise Ergebnisse liefern. Die integrierten Klassifikationsmerkmale tragen die Bezeichnungen `Standard` (Default), `Lebensmittel` (Food) und `Unangemessen` (Explicit).

### Klassifikationsmerkmal "Standard"

Das Klassifikationsmerkmal "Standard" (Default) gibt Klassen aus Tausenden von möglichen Tags zurück, die in Kategorien und Unterkategorien organisiert sind. Die folgenden Kategorie der höchsten Ebene können zurückgegeben werden:

- Tiere (einschließlich Vögel, Reptilien, Amphibien usw.)
- Personenbezogene Informationen und Aktivitäten
- Lebensmittel (einschließlich zubereitete Speisen und Getränke)
- Pflanzen (einschließlich Bäume, Sträucher, Wasserpflanzen, Gemüsepflanzen)
- Sport
- Natur (einschließlich vieler Arten von Landschaftsformen und geologischen Strukturen)
- Transport und Verkehr (zu Land, zu Wasser und in der Luft)
- Außerdem viele andere mehr, wie z. B. Möbel, Früchte, Musikinstrumente, Werkzeuge, Farben, Gadgets, Geräte, Instrumente, Waffen, Gebäude, Konstruktionen und hergestellte Gegenstände, Bekleidung, Blumen usw.

### Klassifikationsmerkmal "Lebensmittel"

Das Klassifikationsmerkmal "Standard" (Default) kann zwar Lebensmittel und Getränke bezeichnen, aber Sie können auch das integrierte Klassifikationsmerkmal `Lebensmittel` (Food) angeben für ...

### Klassifikationsmerkmal "Unangemessen"

Visual Recognition kann eine entsprechende Klassifizierung vornehmen, wenn ein Bild nicht für die allgemeine Verwendung geeignet ist. Das Klassifikationsmerkmal `Unangemessen` (Explicit) bezeichnet derzeit Darstellungen, die als pornografisch erachtet werden könnten. Eine gängige Abkürzung für diese Klassifizierung ist _NSFW_ und steht für _Not Safe for Work_ (Nicht zur Ansicht bzw. Verwendung am Arbeitsplatz geeignet).

Ein Score über oder unter einer bestimmten Zahl bedeutet nicht automatisch, dass ein Bild unangemessen ist oder nicht. Aber Sie können die Antwort als einen ersten Filter für ein Bild verwenden und dann eine genauere Analyse durchführen.

Antwort:
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

## Klassifikationsmerkmale kombinieren


## Klassenhierarchie in der Antwort

Die Methode `/v3/classify` klassifiziert Bilder in einer Hierarchie zusammengehöriger Klassen. Beispiel: Das Bild eines Beagles kann als "Tier" und auch als "Hund" und "Beagle" klassifiziert werden. Eine positive Übereinstimmung mit den zugehörigen Klassen - in diesem Fall "Hund" und "Beagle" - erhöht den Score der übergeordneten Antwort. In diesem Fall enthält die Antwort alle drei Klassen: "Tier", "Hund" und "Beagle". Der Score der übergeordneten Klasse ("Tier") wird erhöht, weil sie den zugehörigen Klassen ("Hund" und "Beagle") entspricht. Die übergeordnete Klasse ist außerdem "type\_hierarchy", um zu zeigen, dass sie eine übergeordnete Klasse in der Hierarchie ist.

## Richtlinien für die Klassifizierung einer großen Zahl von Bildern

Maximieren Sie die Effizienz und Leistung des Service auf folgende Art und Weise, wenn Sie eine große Zahl von Bildern verarbeiten:

- Ändern Sie die Größe Ihrer Bilder in 224 x 224 Pixel (z. B. durch Ausschneiden). Der Service ist derzeit für diese Größe optimiert. Dies kann sich aber ändern.
    - Schneiden Sie das Bild zurecht, wenn es ein Seitenverhältnis größer als 2:1 oder kleiner als 1:2 hat.
    - Sie können das Bild zum Beispiel auf mehrere quadratische Bilder zurechtschneiden oder nur die Bildmitte verwenden, abhängig davon, was in Ihrem Anwendungsfall am wichtigsten ist.
- Stellen Sie bis zu 20 Bilder in eine einzelne Datei mit der Erweiterung .zip. Sie müssen keine Komprimierung vornehmen, weil JPEG- und PNG-Bilder bereits komprimierte Dateien sind.
- Verwenden Sie den Parameter **classifier_ids**, um nur die Klassifikationsmerkmale anzugeben, die Sie verwenden wollen.
- Auch wenn der Service EXIF-Tags liest und die Bilder dreht, sollten Sie für einen möglichst hohen Durchsatz Bilder senden, die nicht vom Service gedreht werden müssen (der EXIF-Tag **Orientation** ist auf `1` eingestellt).
