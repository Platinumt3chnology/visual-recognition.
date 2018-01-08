---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-11"

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

# Releaseinformationen

Folgende neue Features und Änderungen am Service sind verfügbar.
{: shortdesc}

## Beta-Features
{: #beta}

{{site.data.keyword.IBM_notm}} stellt als "Beta" eingestufte Services, Features und Sprachunterstützung zur Verfügung, die Sie testen können. Diese Features können instabil sein, sich häufig ändern und kurzfristig wieder eingestellt werden. Beta-Features bieten möglicherweise auch nicht die Leistung oder Kompatibilität allgemein verfügbarer Features und sie sind nicht für den Einsatz in einer Produktionsumgebung konzipiert. Beta-Features werden nur unter [developerWorks Answers ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} unterstützt.

## Änderungen
{: #changelog}

Folgende neue Features und Änderungen am Service sind verfügbar.

### 11. Dezember 2017
{: #11december2017}

<ul>
  <li>
    <strong>Höhere Genauigkeit und gesteigerte Ausgabe mit dem Modell "Allgemein"</strong>
      <p>
        Das Modell "Allgemein" (General), das mehrere hundert Tags enthält, erkennt nun mehr sekundäre Objekte und bietet eine verbesserte Szenenerkennung. Diese Verbesserungen tragen dazu bei, dass auch die weniger hervorstechenden Aspekte eines Bilds erkannt werden. Darüber hinaus wurde die durchschnittliche Zahl von Tags, die pro Bild zurückgegeben werden, auf 10 erhöht.
      </p>
      <p>
                Das folgende Bild zeigt ein Beispiel für die zurückgegebenen Tags vor dem Update und danach.
      </p>
      <img src="images/antarctica-iceberg.jpg" alt="Eisberg in der Antarktis">
      <table>
        <tr>
          <th>Ursprüngliche Tags</th>
          <th>Zusätzliche Tags</th>
        </tr>
        <tr>
          <td>
          Tag: Eisberg<br/>
          Score: 0,919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: Eismassen<br/>
          Score: 0,801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: Natur<br/>
          Score: 0,770</td>
        </tr>
        <tr>
          <td>
          Tag: Blaue Farbe<br/>
          Score: 0,975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: Alabasterfarbe<br/>
          Score: 0,5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Neues Modell für unangemessene Inhalte in Betaversion verfügbar</strong>
      <p>
        Das Modell für unangemessene Inhalte (Explicit), das in der Betaversion eingeführt wird, klassifiziert Bilder danach, ob sie pornografische Inhalte enthalten und für die allgemeine Verwendung ungeeignet sind. Sie können das Modell für unangemessene Inhalte mit anderen Modellen für eine gemeinsame Analyse kombinieren. Beispielsweise können Sie die Klassifikationsmerkmal-IDs `default` und `explicit` in Ihre Anforderung aufnehmen, damit Bildtags zurückgegeben und unangemessene Inhalte ermittelt werden.
      <p>
        Details zum API-Aufruf finden Sie unter dem Stichwort **Classify images** in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image). Oder testen Sie das Modell im [API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify).
      </p>
    </li>
    <li>
      <strong>Unterstützung größerer Dateien</strong>
      <p>
        Die Methoden <strong>Bilder klassifizieren</strong> unterstützen jetzt Bilddateien bis zu 10 MB und .zip-Dateien bis 100 MB.
    </li>
    <li>
      <strong>Array, das beim Übergeben von Klassifikationsmerkmal-IDs erforderlich ist</strong>
      <p>
        Die API erzwingt jetzt ein Array, wenn Sie `classifier_ids` als Teil des Objekts **parameters** in der Methode **Bilder klassifizieren** übergeben. Zuvor konnten Sie eine Klassifikationsmerkmal-ID als Zeichenfolge übergeben. Weitere Informationen finden Sie in der Parameterbeschreibung und Beispieldatei in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image).
      </p>
    </li>
</ul>

### 8. September 2017
{: #8september2017}

- **Ähnlichkeitssuche (Beta) und Sammlungen geschlossen**: Seit dem 8. September 2017 ist der Betazeitraum für die Ähnlichkeitssuche geschlossen. Weitere Informationen finden Sie unter [Visual Recognition API – Similarity Search Update ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30. Juni 2017
{: #30june2017}

- **Verbessertes Tagging**: Die Zahl der Trainingsbilder für das Klassifikationsmerkmal "Standard" (Default) wurde erhöht. Dadurch kann die "Gesamtszene" eines Bilds besser erkannt werden. Weitere Informationen finden Sie unter [Further Enhancements for General Tagging Feature ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}.
- **Zusätzliche Sprachen**: Die Methode **Bilder klassifizieren** unterstützt jetzt Koreanisch, Italienisch und Deutsch zusätzlich zu Englisch, Arabisch, Spanisch und Japanisch.

    Details zum API-Aufruf finden Sie unter dem Stichwort **Classify an image** (Bild klassifizieren) in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}.

### 16. Mai 2017
{: #16may2017}

- **Neues Klassifikationsmerkmal für Lebensmittel verfügbar: Beta**

    Ein neues Betamodell für die Erkennung von Lebensmitteln bietet eine erweiterte Spezifität und Genauigkeit für Bilder von Lebensmitteln. Die Methode **Bild klassifizieren** gibt Ihnen die Möglichkeit, dieses neue Klassifikationsmerkmal "Lebensmittel" zum Parameter `classifier_ids` hinzuzufügen.

### 5. April 2017
{: #5april2017}

- **Neues {{site.data.keyword.visualrecognitionshort}}-Tool ist verfügbar: Beta**

    Ein neues Beta-Feature, das {{site.data.keyword.visualrecognitionshort}}-Tool, steht unter folgender Adresse zur Verfügung: [https://watson-visual-recognition.ng.bluemix.net/ ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Dieses Tool bietet einen höheren Bedienungskomfort beim Arbeiten mit dem {{site.data.keyword.visualrecognitionshort}}-Service. Nach Eingabe Ihres {{{site.data.keyword.cloud_notm}}-API-Schlüssels können Sie eine grafische Benutzerschnittstelle verwenden, mit der Sie auf die Features für allgemeines Tagging und Gesichtserkennung zugreifen und benutzerdefinierte Klassifikationsmerkmale, die Ihrem API-Schlüssel zugeordnet sind, nahtlos und ohne Codierungsaufwand erstellen, neu trainieren und löschen können.

### 8. März 2017
{: #8march2017}

- **Aktualisierte Sprachunterstützung für das Tagging allgemeiner Klassifikationsmerkmale**

    Das allgemeine Klassifikationsmerkmal (General) gibt nun Tags in allen unterstützten Sprachen zurück.

- **Bekannte Probleme**

    **Korrektur vom 13.04.2017**: Wiederholtes Aufrufen von `GET /classifiers` zum Prüfen des Status beim Trainieren oder Neutrainieren kann zum Abbruch des Trainingsjobs führen. Um dieses Problem zu umgehen, können Sie den Status des neuen Klassifikationsmerkmals mit `GET /classifiers/{klassifikationsmerkmal-id}` abfragen. D. h., Sie können das Klassifikationsmerkmal `GET` für eine einzelne Klassifikationsmerkmal-ID anstatt `GET /classifiers` verwenden, wodurch alle Klassifikationsmerkmale abgerufen werden, was das Problem auslösen kann. Außerdem erfolgt die Verarbeitung bei `GET /classifiers/{klassifikationsmerkmal-id}` schneller.

### 15. Dezember 2016
{: #15december2016}

- **Verbessertes Tagging allgemeiner Klassifikationsmerkmale**

    - Die Deep-Learning-Algorithmen des allgemeinen Klassifikationsmerkmals (General) wurden aktualisiert. Die Qualität der Tags wurde für alle Sprachen deutlich gesteigert und der Service gibt wesentlich mehr englische Tags zurück. Diese Ausgabe qualitativ hochwertiger Tags ist auch verfügbar, wenn Sie ein eigenes benutzerdefiniertes Klassifikationsmerkmal erstellen.
    - Als Neuerung wurde Farbtagging hinzugefügt. Der Service gibt nun die ein oder zwei im Bild vorherrschenden Farben zurück.

- **Bekannte Probleme**

    - Bilder, die mit EXIF-Metadatentags an die Demo übergeben wurden, geben die Ausrichtung (Querformat oder Hochformat) nicht richtig für den Service an. Mit dem iPhone hochgeladene Bilder können EXIF-Metadatentags enthalten. Sie können das Problem umgehen, indem Sie Ihre Bildmetadaten so ändern, dass sie keine EXIF-Metadatentags verwenden, um die Ausrichtung Ihres Bilds anzugeben. Häufig können Sie dies tun, indem Sie einfach das Bild auf Ihrem Computer öffnen und es speichern. Beispielsweise kann das Bild auf einem Mac im Vorschaumodus geöffnet und gespeichert werden und erhält so die richtigen Tags für die Ausrichtung.
    - Das Senden von Bildern an den {{site.data.keyword.visualrecognitionshort}}-Service mit [EXIF-Tag-Werten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://en.wikipedia.org/wiki/Exif){: new_window} von 8, 3 oder 6 kann die Latenz erhöhen. Der Service dreht die Bildpixel zum codierten Blickpunkt. Sie können Zeit sparen, wenn Sie Ihre Bilder im Voraus drehen oder indem Sie die EXIF-Header entfernen, wenn Sie für Ihre {{site.data.keyword.visualrecognitionshort}}-Task nicht wichtig sind.

### 1. Dezember 2016
{: #1december2016}

- **Neue Preisgestaltung**

    IBM hat die Preise für benutzerdefinierte Klassifikationsmerkmale im {{site.data.keyword.visualrecognitionshort}}-Service gesenkt und das Angebot des kostenlosen Plans erweitert. Weitere Informationen finden Sie auf der [{{site.data.keyword.visualrecognitionshort}}-Seite für die Preisstruktur](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7. Oktober 2016
{: #7october2016}

- **Verbesserungen bei der Gesichtserkennung**

    Der Service bietet einen neuen Algorithmus für die Gesichtserkennung, der die Antworten der Methoden `GET` und `POST /v3/detect_faces` verbessert. Der Service hat das Filtern der Gesichtserkennung (Alter, Name und Geschlecht) mit geringer Verlässlichkeit angepasst. Folglich werden mehr Gesichter gefunden und es werden mehr Verlässlichkeitsbereiche zurückgegeben.

### 8. September 2016
{: #8september2016}

- **Ähnlichkeitssuche (BETA)**

    Benutzer können jetzt ihre eigene Sammlung von Bildern hochladen und die Sammlung anhand eines Bilds nach ähnlichen Bildern durchsuchen. Daraufhin gibt der Service die 100 ähnlichsten Bilder zurück. Die Ähnlichkeitssuche kann für beliebige Zwecke verwendet werden und die Benutzer können jeden Service anhand von Sammlungen von bis zu einer Million Bilder trainieren. Weitere Informationen zur neuen Funktionalität für die Ähnlichkeitssuche finden Sie im [Lernprogramm](/docs/services/visual-recognition/tutorial-collections.html) und auf den Seiten der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Texterkennung ist jetzt für einen exklusiven Benutzerkreis verfügbar (Closed Beta)**

    Die Methoden `POST` und `GET /v3/recognize_text` stehen jetzt wieder einem exklusiven Benutzerkreis zur Verfügung (Closed Beta). IBM unterstützt BETA-Kunden auch weiterhin, die den Service nutzen, und beabsichtigt derzeit nicht, die Beta-Features allgemein zur Verfügung zu stellen (Open Beta).

### 1. August 2016

- **Ende des Einstiegspreisangebots**

    Das Trainieren und Neutrainieren von benutzerdefinierten Klassifikationsmerkmalen, die Klassifizierung benutzerdefinierter Bilder und das Speichern benutzerdefinierter Klassifikationsmerkmale ist nicht mehr kostenlos möglich. Weitere Informationen zur Preisgestaltung finden Sie auf der [Seite für die Preisstruktur](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) des {{site.data.keyword.visualrecognitionshort}}-Service.

### 5. Juli 2016
{: #5july2016}

- **Benutzerdefinierte Klassifikationsmerkmale aktualisieren**

    Benutzerdefinierte Klassifikationsmerkmale sind nicht mehr auf bestimmte Trainingsdaten begrenzt. Ein Benutzer kann nun vorhandene Klassifikationsmerkmale mit neuen Bildern aktualisieren oder zusätzliche Klassifikationsmerkmale mit positiven oder negativen Beispielen zu einem trainierten Klassifikationsmerkmal hinzufügen. Wenn Sie zusätzliche Beispielbilder zur Verfügung stellen, mit deren Hilfe Watson dazulernen kann, wird die Genauigkeit eines Klassifikationsmerkmals durch den Service verbessert. Benutzerdefinierte Klassifikationsmerkmale können im Laufe der Zeit dazulernen und verstehen die visuellen Informationen immer besser.

- **Bekannte Probleme**

    **Korrektur vom 13.04.2017**: Benutzer erhalten möglicherweise nach 30 oder 90 Sekunden einen Fehlercode 500, wenn Sie ein vorhandenes Klassifikationsmerkmal aktualisieren. Trotz des Fehlers ist die Wahrscheinlichkeit hoch, dass die Anforderung zum Neutrainieren erfolgreich ausgeführt wird. Warten Sie mindestens zwei Minuten und prüfen Sie dann den Status des Klassifikationsmerkmals unter Verwendung der Methode `GET classifiers/{classifier\_id}`. Wenn der Status "ready" (Bereit) ist und die Zeitmarke "retrained" (Neu trainiert) aktualisiert wurde, war die Anforderung zum Neutrainieren, die den Fehlercode 500 generiert hat, erfolgreich. Wenn die "retrained"-Zeitmarke nicht aktualisiert wurde, wird der Antwort eine Erläuterung hinzugefügt, die beschreibt, warum das Neutrainieren fehlgeschlagen ist, und der Service setzt das Klassifikationsmerkmal auf die Version zurück, die vorlag, bevor die Anforderung zum Neutrainieren ausgegeben wurde.

### 20. Mai 2016
{: #20 may 2016}

Dies ist das allgemein verfügbare Release (General Availability, GA) des {{site.data.keyword.visualrecognitionshort}}-Service. Dieses Release führt Version 3 des Service ein und stellt eine grundlegende Änderung dar. Dieses Release enthält die Funktionalität des AlchemyVision-Service (veraltet).

Alle benutzerdefinierten Klassifikationsmerkmale, die erstellt wurden, während sich der Service in der Betaphase befand, müssen in einer GA-Instanz des Service neu erstellt werden.

Die folgenden Änderungen und Aktualisierungen wurden am {{site.data.keyword.visualrecognitionshort}}-Service vorgenommen:

- **Versionsdatum:** Um die Features dieses Release verwenden zu können, müssen Sie den Wert `2016-05-20` für den Parameter `version` verwenden.
- **Klassen und Klassifikationsmerkmale:** Einzelne Klassifikationsmerkmale werden nun als "Klassen" bezeichnet. Im GA-Release wird eine Gruppe von Klassen als "Klassifikationsmerkmal" bezeichnet.
- **Klassifizierung:** Verwenden Sie die Methoden `POST` oder `GET /v3/classify`, um verschiedene Gegenstände und Szenen schnell und präzise mit Standardklassen zu identifizieren.
- **Gesichtserkennung:** Verwenden Sie die Methoden `POST` oder `GET /v3/detect_faces`, um Gesichter in Bildern zu erkennen und um Informationen über sie zu sammeln (z. B. die Position des Gesichts in dem Bild sowie die geschätzte Altersgruppe und das Geschlecht jeder Person). Der Service erkennt auch viele bekannte Persönlichkeiten aus dem öffentlichen Leben und er kann einen Knowledge Graph bereitstellen, in dem Informationen systematisch miteinander verknüpft werden können.
- **Benutzerdefinierte Klassifikationsmerkmale mit mehreren Facetten:** Sie können jetzt hoch spezialisierte Klassifikationsmerkmale erstellen und definieren, die durch verschiedene Klassen definiert werden. Beispiel: Sie können ein Klassifikationsmerkmal "new\_red\_car" erstellen, das durch die Klassen "new\_cars" und "red\_cars" definiert wird. Weitere Informationen zum Erstellen von Klassifikationsmerkmalen mit mehreren Facetten finden Sie unter [Struktur der Trainingsdaten](/docs/services/visual-recognition/customizing.html#structure).
- **Asynchrones Training:** Das Trainieren benutzerdefinierter Klassifikationsmerkmale erfolgt nun asynchron. Das bedeutet, Trainingsaufrufe werden schnell ausgeführt, während Ihr benutzerdefiniertes Klassifikationsmerkmal im Hintergrund weiter dazulernt. Um den Trainingsstatus Ihres benutzerdefinierten Klassifikationsmerkmals zu prüfen und herauszufinden, wann es zur Verwendung verfügbar ist, rufen Sie die Methode `GET /v3/classifiers/{klassifikationsmerkmal-id}` auf und prüfen Sie den Antwortparameter `status`.

### 2. Dezember 2015
{: #2december2015}

Das neueste Release des {{site.data.keyword.visualrecognitionshort}}-Service beinhaltet eine grundlegende Änderung, die eine neue Version der {{site.data.keyword.visualrecognitionshort}}-API (v2) einführt. Version 1 des {{site.data.keyword.visualrecognitionshort}}-Service kann verwendet werden, bis der Betazeitraum des Service abgelaufen ist.

Um sofort mit Version 2 der API arbeiten zu können, müssen Sie folgende Änderungen beachten und Ihren Code entsprechend ändern:

- In Version 1 des Service haben Sie Bilder anhand von Bezeichnungen (Labels) analysiert. In Version 2 des Service werden diese Bezeichnungen **Klassifikationsmerkmale** genannt. Klassifikationsmerkmale haben eine eindeutige Klassifikationsmerkmal-ID, die durch den Parameter `classifier_id` angegeben wird, und einen Kurznamen, der durch den Parameter `name` angegeben wird.
- Die bisherige Methode `POST /v1/recognize` zur Analyse eines Bilds ist nun die Methode [`POST /v2/classify` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}. Der Parameter `labels_to_check` wurde in `classifier_ids` umbenannt.
- Die bisherige Methode `GET /v1/tag/labels` für das Abrufen einer Liste von Bezeichnungen in Version 1 ist nun die Methode [`GET /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} für das Abrufen einer Liste von Klassifikationsmerkmalen.
- Sie können nicht nur eine Liste mit Klassifikationsmerkmalen abrufen, sondern mit der neuen Methode [`GET /v2/classifiers/{klassifikationsmerkmal-id}` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window} auch Details zu einem Klassifikationsmerkmal abrufen.
- Mit Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API können Sie benutzerdefinierte Klassifikationsmerkmale mit der neuen Methode [`POST /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window} erstellen. Weitere Informationen zum Erstellen von benutzerdefinierten Klassifikationsmerkmalen finden Sie unter [Benutzerdefinierte Klassifikationsmerkmale erstellen](/docs/services/visual-recognition/customizing.html).
- Mit Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API können Sie benutzerdefinierte Klassifikationsmerkmale mit der neuen Methode [`DELETE /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window} auch löschen.
- Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API erfordert den Parameter `version`. Geben Sie das Freigabedatum der Version der API, die Sie verwenden wollen, im Format `MM-TT-JJJJ` an.
