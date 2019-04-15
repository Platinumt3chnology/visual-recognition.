---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom object detection,object detection,bounding boxes,visual inspection
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

<!-- Link definitions -->

[api-ref-v4]: https://{DomainName}/apidocs/visual-recognition-v4

# Benutzerdefinierte Objekterkennung (Beta)
{: #object-detection-overview}

Die Beta-Funktion der benutzerdefinierten Objekterkennung von {{site.data.keyword.visualrecognitionfull}} (Custom Object Detection) identifiziert Elemente und deren Position in einem Bild. Der Service erkennt diese Elemente auf Grundlage einer Gruppe von Bildern mit bezeichneten Trainingsdaten, die Sie angeben.
{: shortdesc}

Die benutzerdefinierte Objekterkennung ist eine private Beta-Funktion. Für Aufrufe an das Modell müssen Sie über entsprechende Berechtigungen von {{site.data.keyword.IBM_notm}} verfügen. [Fordern Sie Zugriff an ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}. Weitere Informationen zu den Beta-Funktionen finden Sie in den [Releaseinformationen](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Sie trainieren das Objekterkennungsmodell, sodass es Objekte erkennt, die für Ihren Workflow oder Ihre Domäne wichtig sind. Dies kann z. B. die Erkennung von Schäden an Autos oder von Maschinen mit Wartungsbedarf sein oder Sichtprüfungen an Produktionsstandorten. Mit der Objekterkennung können Sie auch Objekte zählen oder Bestände verwalten.

## Objekterkennung und Objektklassifizierung im Vergleich
{: #obj-detect-comparison}

Das Modell für benutzerdefinierte Objekterkennung ist die neueste Funktion des {{site.data.keyword.visualrecognitionshort}}-Service und umfasst auch die Klassifizierung.

Klassifizierung und Objekterkennung sind ähnlich, werden aber unterschiedlich eingesetzt. Grundsätzlich verwenden Sie für die Vorhersage von Objekten in einem Bild eine Klassifizierung. Wenn Objekte in einem Bild gesucht oder gezählt werden sollen, verwenden Sie die Objekterkennung.

### Klassifizierung
{: #obj-detect-classify}

Wenn Sie ein Bild klassifizieren, gibt der Service die Wahrscheinlichkeit zurück, mit der bestimmte Objekte in diesem Bild enthalten sind. Sie können die integrierten Modelle (General, Food oder Explicit - Allgemein, Lebensmittel oder unangemessene Inhalte) verwenden oder ein eigenes angepasstes Modell erstellen.

Wenn Sie beispielsweise ein Bild von Cookies wie im folgenden Bild klassifizieren, sagt der Service voraus, dass das Bild mit einer Konfidenz von 95%  Cookies enthält.

![Bild mit Klassifizierungs-Antwort](images/cookies-tag.png "Bild zur Darstellung der Klassifizierung")

### Objekterkennung
{: #obj-detect-detect}

Die benutzerdefinierte Objekterkennung ähnelt der benutzerdefinierten Klassifizierung, mit dem Unterschied, dass der Service die Position der Elemente im Bild identifiziert. Wie bei der Klassifizierung enthält die Antwort auch die Bezeichnung für jedes erkannte Element sowie die Konfidenz für die Identifizierung.

Welche Elemente erkannt werden, basiert auf den Informationen, die Sie angeben, wenn Sie ein Objekterkennungsmodell trainieren.

Im folgenden Bild identifiziert die Methode **Analyze images** (Bilder analysieren) der benutzerdefinierten Objekterkennung die Position von Cookies in dem Bild. Jedes erkannte Objekt enthält die Bezeichnung (in diesem Fall `Cookie`), zusammen mit der Position und einem Konfidenzscore.

![Bild mit Objekterkennungs-Antwort](images/cookies-bbox.png "Bild zur Darstellung der Objekterkennung")

## Verwendung einer benutzerdefinierten Objekterkennung
{: #object-detection-sequence}

Um die benutzerdefinierte Objekterkennung von {{site.data.keyword.visualrecognitionshort}} zu verwenden, führen Sie diese Folge von Schritten aus, mit der ein angepasstes Objekterkennungs-Modell eingerichtet wird:

1.  Erstellen Sie eine Sammlung: Eine Sammlung ist ein Container für Ihre Bilder und Trainingsdaten. Siehe hierzu [Sammlung erstellen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} in der Referenz zur API Version 4.
1.  Fügen Sie der Sammlung weitere Bilder hinzu. Sie können einzelne Bilder nach URL oder Datei hinzufügen oder eine `.zip `-Datei von Bildern hochladen. Siehe [Bilder hinzufügen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} in der Referenz zur API Version 4.
1.  Fügen Sie Ihren Bildern Trainingsdaten hinzu. Siehe hierzu [Trainingsdaten vorbereiten](#object-detection-preparation).
1.  Trainieren Sie Ihre Sammlung. Nachdem Sie genügend Trainingsdaten erhalten haben, beginnen Sie mit dem Training in den Bildern der Sammlung. Siehe hierzu [Sammlung trainieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} in der Referenz zur API Version 4.

Nachdem Sie diese Schritte ausgeführt und die Sammlung trainiert haben, können Sie Bilder anhand dieser Sammlung analysieren.

### Trainingsdaten vorbereiten
{: #object-detection-preparation}

Der wichtigste Teil des Einrichtungsprozesses ist die Vorbereitung und Assemblierung Ihrer Trainingsdaten. Wie beim [Erstellen eines angepassten Modells](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) für die Klassifizierung von Bildern assemblieren Sie eine Gruppe von Bildern, die die zu erkennenden Objekte darstellen.

Zusätzlich zu einer Gruppe von Bildern stellen Sie für jedes Bild auch Trainingsdaten zur Verfügung. Im Rahmen der Objekterkennung sind die Trainingsdaten die Gruppe von Bezeichnungen und Positionen für Objekte in dem Bild, die {{site.data.keyword.visualrecognitionshort}} erkennen soll. In einem Bild können auch mehrere Objekte enthalten sein.

Die Bezeichnung gibt an, worum es sich bei dem Objekt handelt. Die Position gibt an, wo sich das Objekt im Bild befindet. Sie identifizieren die Position, indem Sie einen _Rahmen_ um das Objekt ziehen und die oberen und linken Pixelkoordinaten dieses Feldes sowie Breite und Höhe in Pixeln angeben.

Das folgende Beispiel zeigt die Trainingsdaten für ein Objekt mit der Kennzeichnung `BurntCookie`.

```json
{
  "objects": [{
    "object": "BurntCookie",
    "location": {
      "left": 33,
      "top": 8,
      "width": 163,
      "height": 119
    }
  }]
}
```
{: codeblock}

In dieser anfänglichen Betaversion erstellen Sie die Positionsinformationen von Hand oder unter Verwendung eines Bildanmerkungstools.

Im Allgemeinen gilt: Je mehr Bilder und Rahmen Sie in Ihren Trainingsdaten angeben, desto besser. Im Folgenden finden Sie einige Richtlinien für Trainingsdaten, mit denen Sie beginnen können:

- Jedes Bild hat eine Höhe und Breite von mindestens 500 Pixeln.
- Jedes gekennzeichnete Objekt in der Sammlung besitzt mindestens 100 Positionen (Rahmen).
- Jedes Bild in der Sammlung hat maximal 10 Rahmen.
- Die Größe der einzelnen Rahmen beträgt mehr als 15% der Bildgröße.
- Die API liest die EXIF-Ausrichtungstags in Ihren Bildern. Stellen Sie sicher, dass die Koordinaten von `location` (Position) mit dieser Ausrichtung übereinstimmen. Zur Anpassung der Ausrichtung können Sie ein Tool wie ImageMagick verwenden, um Ihre Bilder _automatisch ausrichten_ zu lassen, bevor Sie die Rahmen hinzufügen.

Weitere Informationen zur Methode **Trainingsdaten zu einem Bild hinzufügen** finden Sie in der [Referenz zur API Version 4![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}.

### Sammlung trainieren
{: #object-detection-train}

Nachdem Sie die Trainingsdaten zu Bildern in Ihrer Sammlung hinzugefügt haben, besteht der abschließende Einrichtungsschritt darin, ein Objekterkennungsmodell zu trainieren. Ein einzelner Aufruf an die API startet das Training. Die Antwort enthält Statusinformationen. Zum Beispiel zeigt der folgende Status, dass das Training gestartet, aber noch nicht abgeschlossen wurde:

```json
"training_status": {
  "objects": {
    "ready": false,
    "in_progress": true,
    "data_changed": false,
    "latest_failed": false,
    "description": "Starting training"
  }
}
```
{: codeblock}

Sie können ein Modell nach dem Aktualisieren der Trainingsdaten neu trainieren, indem Sie den Aufruf erneut absetzen.

Weitere Informationen finden Sie unter [Sammlung trainieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} in der Referenz zur API Version 4.

## Bilder analysieren
{: #object-detection-analyze}

Nachdem Sie ein Modell für benutzerdefinierte Objekterkennung eingerichtet haben und das Training abgeschlossen ist, können Sie Objekte in anderen Bildern erkennen lassen. Wie bei der Klassifizierung stellen Sie ein Bild oder eine `.zip`-Datei von Bildern sowie optional einen **Schwellenwert** bereit, um den Mindest-Score für erkannte Objekte festzulegen. Weitere Informationen finden Sie im Abschnitt zur Methode **Analyze images** (Bilder analysieren) in der [Referenz für die API Version 4![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images).

## Nächste Schritte
{: #object-detection-next-steps}

- Informationen zur API finden Sie in der [Referenz zur API Version 4 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition-v4){: new_window}.
