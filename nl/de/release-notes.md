---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

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

<!-- Link definitions -->

[watson-studio-reg]: https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs
[demo]: https://www.ibm.com/watson/services/visual-recognition/demo

# Releaseinformationen
{: #release-notes}

Folgende neue Features und Änderungen am Service sind verfügbar.
{: shortdesc}

## API-Versionierung des Service
{: version}

API-Anforderungen benötigen einen Versionsparameter, der ein Datum im Format `version=JJJJ-MM-TT` angibt. Bei jeder abwärtskompatiblen Änderung der API wird eine neue Unterversion der API freigegeben.

Senden Sie den Versionsparameter zusammen mit jeder API-Anforderung. Der Service verwendet die API-Version für das von Ihnen angegebene Datum oder die Version, die vor diesem Datum zuletzt freigegeben wurde. Verwenden Sie nicht das aktuelle Datum als Standardwert. Geben Sie stattdessen ein Datum für eine Version an, die mit Ihrer App kompatibel ist, und ändern Sie das Datum erst dann, wenn Ihre App zur Verwendung einer späteren Version bereit ist.

Die aktuelle Version ist `2018-03-19`.

## Beta-Features
{: #beta}

{{site.data.keyword.IBM_notm}} stellt als "Beta" eingestufte Services, Features und Sprachunterstützung zur Verfügung, die Sie testen können. Diese Features können instabil sein, sich häufig ändern und kurzfristig wieder eingestellt werden. Beta-Features bieten möglicherweise auch nicht die Leistung oder Kompatibilität allgemein verfügbarer Features und sie sind nicht für den Einsatz in einer Produktionsumgebung konzipiert. Beta-Funktionen werden nur in [IBM Developer Answers ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} unterstützt.

## Änderungen
{: #changelog}

Folgende neue Features und Änderungen am Service sind verfügbar.

### 15. Januar 2019
{: #15january2019}

- **Übersetzung für das Geschlecht bei der Gesichtserkennung**
    - Die Methoden für **Detect Faces** (Gesichter erkennen) geben jetzt übersetzte Bezeichnungen für "Male" und "Female" zurück, wenn Sie die Sprache im Anforderungsheader **Accept-Language** angeben. Weitere Informationen finden Sie in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}.

### 1. Oktober 2018
{: #01october2018}

- **Serviceinstanzen, die vor dem 23. Mai 2018 erstellt wurden, werden gelöscht.**

    - Wie zuvor angekündigt, sind alle {{site.data.keyword.visualrecognitionshort}}-Instanzen, die vor dem 23. Mai 2018 erstellt wurden, inaktiviert. Daten aus diesen Instanzen sind jetzt gelöscht. Ausführliche Informationen zu Verschiebungen auf eine neue Serviceinstanz finden Sie unter [Migrieren](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating).
    - Nach diesem Datum erstellte Serviceinstanzen sind nicht betroffen.
    - Bei Fragen wenden Sie sich an den [IBM Support ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/ibmcloudsupport){: new_window}.

### 1. August 2018
{: #01august2018}

- **Allgemeine Verfügbarkeit der Modelle für Lebensmittel und unangemessene Inhalte**

    Die Modelle "Food" (Lebensmittel) und "Explicit" (unangemessene Inhalte) wurden von der Beta-Version in den Status der allgemeinen Verfügbarkeit (GA) versetzt. Das Modell für Lebensmittel erkennt mehr Nahrungsmittel und Mahlzeiten als das allgemeine (Standard-) Modell. Das Modell für unangemessene Inhalte erkennt potenziell pornografische Darstellungen.

    Es sind keine Codeänderungen erforderlich. Beide Modelle stehen kostenlos mit dem Lite-Plan zur Verfügung und kosten unter dem Standard-Plan 0,002 USD pro Bild.

    Weitere Informationen finden Sie unter [Aktualisierungen an Watson Visual Recognition ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/visrec-price-reduction){: new_window} im <em>Watson-Blog</em>.

### 1. Juli 2018
{: #01july2018}

- **Neue Preisgestaltung für angepasste Modelle**
    - Ab 1. Juli 2018 kostet die Klassifizierung eines Bildes mit einem angepassten Modell die Hälfte des früheren Preises, also 0,002 USD pro Bild. Weitere Informationen hierzu und zu anderen wichtigen Aspekten finden Sie im Beitrag zu [Aktualisierungen an Watson Visual Recognition \- Preissenkung für benutzerdefinierte Klassifizierung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/visrec-price-reduction){: new_window} im <em>Watson-Blog</em>.

### 21. Juni 2018
{: #21june2018}

- **Zusätzliche Sprachunterstützung**

    - Die **Classify**-Methoden unterstützen jetzt Chinesisch (Vereinfacht und Traditionell) sowie Portugiesisch (Brasilien) in der Ausgabe der (allgemeinen) `default`-Modellklassen. Eine vollständige Liste der Sprachen finden Sie in [Unterstützte Sprachen](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).
    - Alle Sprachen werden jetzt auch in den Antworten aus den Modellen **Food** (Lebensmittel) und **Explicit** (unangemessene Inhalte) unterstützt.


### 22. Mai 2018
{: #22may2018}

- **Neuer API-Authentifizierungsprozess**:

    Die Authentifizierung erfolgt jetzt mit Identity and Access Management (IAM) an einem neuen Endpunkt:

    - Verwenden Sie für neue Instanzen eine andere Endpunkt-URL. Der Standardendpunkt ist `https:/gateway.watsonplatform.net/visual-recognition/api/`. Die URL für Ihre Serviceinstanz finden Sie in den Berechtigungsnachweisen, indem Sie im {{site.data.keyword.cloud_notm}} [Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/apps?watson){: new_window} auf die Instanz klicken.
    - Modifizieren Sie die Art der Authentifizierung bei der API. Geben Sie dazu entweder einen IAM-Schlüssel oder ein Zugriffstoken für Ihre Serviceinstanz an. Beispiele hierzu finden Sie unter [Migrieren](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating).

    Für Serviceinstanzen, die vor dem 23. Mai 2018 erstellt wurden, haben sich der Authentifizierungsprozess und der Endpunkt nicht geändert. Führen Sie die Authentifizierung durch Angabe der `api_key`-Abfrageparameter durch.

- **Aktualisierungen am Lite-Plan**

    Die nach dem 22. Mai 2018 erstellten Lite-Pläne werden geändert:

    - Instanzen des neuen Lite-Plans bleiben auch nach 30 Tagen noch verfügbar, wenn Sie sie jeden Monat verwenden.
    - Sie können unter dem neuen Lite-Plan zwei angepasste Modelle erstellen und neu trainieren.
    - Lite-Pläne umfassen bis zu 1000 Ereignisse pro Monat. Ein Ereignis ist jedes Bild, das Sie zur Klassifizierung, Erkennung oder zum Training versenden. Das Herunterladen eines Core ML-Modells geht nicht in die Zahl der Ereignisse ein und unterliegt daher nicht dem Grenzwert.

    Wenn Ihre Anforderungen den Lite-Plan überschreiten, aktualisieren Sie auf ein gebührenpflichtiges Konto. [Erkunden Sie die ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} Preistarife.

- **Informationssicherheit**:

    Die Dokumentation wurde aktualisiert und enthält nun neue Informationen zum Datenschutz. Lesen Sie dazu die Details im Abschnitt [Informationssicherheit](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security).

### 12. April 2018
{: #12april2018}

- ** Unterstützung für erneutes Training eines angepassten Modells im Lite-Plan**

    Unter dem Lite-Plan müssen Sie ein anderes angepasstes Modell nicht mehr löschen und ein neues erstellen, wenn Sie das Modell aktualisieren oder neu trainieren möchten. Sie können ein angepasstes Modell jetzt aktualisieren, solange Sie unterhalb der Tages- und Monats-[Grenzwerte](https://console.bluemix.net/catalog/services/visual-recognition) für den Plan bleiben.

    Wenn Sie mehrere Modelle oder mehrere Versionen desselben Modells benötigen, aktualisieren Sie vom Lite-Plan auf ein gebührenpflichtiges Konto.

- ** Neue Unterversion mit Unterstützung für CORS**

    **Version:** `2018-03-19`

    Für die Angabe von `version=2018-03-19` in Ihren Anforderungen wird jetzt Cross-Origin Resource Sharing (CORS) unterstützt.

### 5. April 2018
{: #5april2018}

- **Korrektur für ein Problem mit dem Score für das Modell "Gesicht"**

  Der Bereich für den Altersscore im Modell "Gesicht" wurde auf den ursprünglichen Bereich von 0 bis 1 zurückgesetzt. Details hierzu finden Sie unter [Bekannte Probleme](#2april2018) zum 2. April 2018.

- **Neue Formulardaten-Parameter**

    Die Methoden **Classify images** (Bilder klassifizieren) und **Detect faces in images** (Gesichter in Bildern erkennen) unterstützen jetzt neue Formulardaten-Parameter. Die Methode "Classify images" (Bilder klassifizieren) unterstützt die separaten Parameter `url`, `classifier_ids`, `threshold` und `owners`. Die Methode "Gesichter erkennen" unterstützt die Angabe der `url`.

    In der Vergangenheit mussten Sie die Werte in einer JSON-Zeichenfolge codieren und den Formulardaten-Parameter **parameters** übergeben. Sie können die neue Methode verwenden, diese Werte in separaten Formulardaten-Parametern für die gesamte Anwendungsentwicklung zu übergeben. Weitere Informationen zur API enthält die [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### 2. April 2018
{: #2april2018}

- **Allgemeine Verfügbarkeit des erweiterten Modells "Gesicht"**

    Das aktualisierte Gesichtserkennungsmodell befindet sich jetzt im Status der allgemeinen Verfügbarkeit (GA).

    Dieses erweiterte Modell verwendet breitere Trainingsdatensätze, um die Genauigkeit der Gesichtserkennung für Alter und Geschlecht zu erhöhen. So werden z. B. die Altersvorhersagen verbessert, indem der Bereich zwischen dem `min`- und dem `max`-Wert verringert wird. Die festgelegte Altersspanne von 9 Jahren im Vorgängermodell wird durch einen dynamischen, kleineren Bereich ersetzt. Der durchschnittliche Altersbereich liegt bei 4,9 Jahren.

    - Änderungen an der API

    Weitere Unterschiede zwischen dem erweiterten und dem vorherigen Gesichts-Modell:
        - Das erweiterte Modell unterstützt die Bildformate .gif und .tif.
        - Das erweiterte Modell unterstützt größere Dateigrößen: bis zu 10 MB für Bilddateien und bis zu 100 MB für ZIP-Dateien.
        - Das erweiterte Modell enthält keine Informationen zu `FaceIdentity` (Gesichts-Identität) in der Antwort. Die Identitätsinformationen beziehen sich auf `name` der Person, `score` und die Knowledge Graph-Funktion `type_hierarchy`.

    Weitere Informationen zur API finden Sie in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

    - Bekannte Probleme

        - Formularparameter dürfen nicht den Inhaltstyp (**Content-Type**) enthalten. Diese Anforderung kann z. B. den Parameter **url** nicht analysieren, weil er die Angabe `;type=text/plain` enthält:

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - Der Altersscore umfasst den Bereich von 0 bis 0,3. Wir arbeiten daran, den ursprünglichen Bereich von 0 bis 1 wiederherzustellen.

    - Beta-Endpunkt wird nicht mehr unterstützt

    Der Beta-Endpunkt unter `/v3/detect_faces_beta` wird nicht mehr verwendet und ist nach dem 17. Mai 2018 nicht mehr zugänglich. Achten Sie darauf, dass Ihre Anforderungen auf `/v3/detect_faces` verweisen.

### 20. März 2018
{: #20march2018}

- **Integration in Apple Core ML**

    {{site.data.keyword.visualrecognitionshort}} umfasst jetzt Unterstützung für das Apple Core ML-Modellformat. Sie können eine Core ML-Version Ihres {{site.data.keyword.visualrecognitionshort}}-Modells in Ihren iOS-Apps verwenden.

    **Starten der Entwicklung:** Für den Beginn der Entwicklung mit {{site.data.keyword.visualrecognitionshort}} und Core ML checken Sie folgende Projekte in GitHub aus:

    - Lokale Klassifizierung von Bildern: [{{site.data.keyword.visualrecognitionshort}} with Core ML ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - Integration von {{site.data.keyword.discoveryfull}} in die Ergebnisse: [{{site.data.keyword.visualrecognitionshort}} und Discovery mit Core ML ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - Durchsuchen des SDK: [Swift-SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **Änderungen an der API**

    Die folgenden abwärtskompatiblen Änderungen an der API sind in der Integration enthalten:

    - Ein neues Feld namens `core_ml_enabled`, das angibt, ob ein Klassifikationsmerkmal-Modell als Core ML-Modell heruntergeladen werden kann. Das Feld wird in der Antwort für Aufrufe an `GET and POST /v3/classifiers` und `GET /v3/classifiers/{classifier_id}` zurückgegeben.
    - Eine neue Methode `GET /v3/classifiers/{classifier_id}/core_ml_model` zum Herunterladen eines Core ML-Modells als Datei mit der Endung '.mlmodel'.  Sie können Core ML-Modelldateien für angepasste Modelle herunterladen, die nach dem 19. März erstellt wurden.
    - Ein neues Feld `updated` (Aktualisiert) mit dem letzten Trainingsdatum des Modells. Das Feld `updated` stimmt entweder mit dem Feld `retrained` (neu trainiert) oder mit dem Feld `created` (erstellt) überein.

    Ausführliche Informationen zu den API-Änderungen für Core ML finden Sie in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}.

- **Neues Tool verfügbar: Watson Studio**

    [Watson Studio ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")][watson-studio-reg]{: new_window} ist die neue integrierte Umgebung, die einen Ersatz für das {{site.data.keyword.visualrecognitionshort}} Beta-Tool enthält. Watson Studio unterstützt nicht nur {{site.data.keyword.visualrecognitionshort}}, sondern auch viele andere {{site.data.keyword.cloud_notm}}-Services und -Ressourcen. Sie können Watson Studio mit allen vorhandenen {{site.data.keyword.visualrecognitionshort}}-Instanzen und -Klassifikationsmerkmalen verwenden.

     Watson Studio stellt eine kollaborative Umgebung in der Cloud bereit. Mit Watson Studio können z. B. Entwickler, Experten und Data-Scientists {{site.data.keyword.visualrecognitionshort}}- und andere KI-Modelle erstellen und trainieren. Watson Studio ermöglicht auch den Zugriff auf die integrierten Modelle "Allgemein" und "Gesicht".

     Watson Studio unterstützt auch Core ML. Sie können eine Core ML-Modelldatei für Ihr angepasstes Modell herunterladen.

    [Erste Schritte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")][watson-studio-reg]{: new_window} mit Watson Studio.

- **Aktualisierte Deep-Learning-Architektur für angepasste Modelle**

    {{site.data.keyword.visualrecognitionshort}} verwendet jetzt eine schnellere und effizientere Deep-Learning-Netzarchitektur für die Klassifizierung. Die aktualisierten Modelle können auch stärker zwischen der obersten Klasse und den übrigen Klassen unterscheiden. Dieser Ansatz könnte zu etwas längeren Trainingszeiten führen. Die neue Architektur wird verwendet, um neue angepasste Modelle zu trainieren. Wenn Sie vorhandene ältere Modelle erneut trainieren, wird die ursprüngliche Architektur verwendet.

    Das folgende Beispiel zeigt die Differenzierung mit der neuen Architektur:

    ![Mann beim Bogenschießen. Foto von Annie Spratt in Unsplash](images/archery.jpg)

    <table>
      <tr>
        <th>Ursprüngliche Klasse und Score</th>
        <th>Aktualisierte Klasse und Score</th>
      </tr>
      <tr>
        <td>Bogenschießen</br>0,99</td>
        <td><strong>Bogenschießen<strong></br>0,9</td>
      </tr>
      <tr>
        <td>Autorennen</br>0,996398</td>
        <td><strong>Radfahren</strong></br>0,004</td>
      </tr>
      <tr>
        <td>Radfahren</br>0,0500174</td>
        <td><strong>Angeln</strong></br>0,001</td>
      </tr>
      <tr>
        <td>Angeln</br>0,11029</td>
        <td><strong>Golf</strong></br>0,031</td>
      </tr>
      <tr>
        <td>Golf</br>0,0980796</td>
        <td><strong>Turnen</strong></br>0,029</td>
      </tr>
      <tr>
        <td>Turnen</br>0,964391</td>
        <td><strong>Judo</strong></br>0,021</td>
      </tr>
      <tr>
        <td>Judo</br>0,339119</td>
        <td><strong>Rennen</strong></br>0,002</td>
      </tr>
      <tr>
        <td>Schlittschuhlaufen</br>0,0393602</td>
        <td><strong>Schlittschuhlaufen</strong></br>0,061</td>
      </tr>
      <tr>
        <td>Skifahren</br>0,0310527</td>
        <td><strong>Skifahren</strong></br>0,003</td>
      </tr>
      <tr>
        <td>Leichtathletik</br>0,208147</td>
        <td><strong>Leichtathletik</strong></br>0,035</td>
      </tr>
    </table>

- **Sprachunterstützung für Französisch**

    Die **Classify**-Methoden unterstützten jetzt Französisch in der Ausgabe von `default`-Modellklassen. Eine vollständige Liste der Sprachen finden Sie in [Unterstützte Sprachen](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).

### 23. Februar 2018
{: #23february2018}

- **Erweitertes Modell "Gesicht" in der Beta-Version verfügbar**

    Es ist ein aktualisiertes Gesichtserkennungsmodell verfügbar. Dieses Beta-Modell verwendet breitere Trainingsdatensätze, um die Genauigkeit der Gesichtserkennung für Alter und Geschlecht zu erhöhen. Weitere Informationen finden Sie unter [Genauigkeit des IBM Watson {{site.data.keyword.visualrecognitionshort}}-Service erhöhen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} und [Beeinflussung (Bias) in KI-Modellen mindern ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}.

    - Die Ergebnisse des aktualisierten Modells sind im [Demo ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")][demo]{: new_window} und im Beta-Tool von [Visual Recognition ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} zu sehen.
    - Das Beta-Modell ist unter `/v3/detect_faces_beta` verfügbar.

    Unterschiede zwischen dem Beta- und dem allgemein verfügbaren (GA) Modell:
    - Das Beta-Modell unterstützt die Bildformate .gif und .tif. Diese Verbesserung wird voraussichtlich auf das GA-Modell angewendet.
    - Das Beta-Modell unterstützt größere Dateigrößen: bis zu 10 MB für Bilddateien und bis zu 100 MB für ZIP-Dateien. Diese Verbesserung wird voraussichtlich auf das GA-Modell angewendet.
    - Die Beta-Gesichtserkennung enthält keine Informationen zu `FaceIdentity` (Gesichts-Identität) in der Antwort.
    - Die POST-Anforderung des Beta-Modells erfordert einen nicht leeren Dateinamen. Von dem GA-Modell "Gesicht" wird diese Bedingung nicht erzwungen.
    - Die POST-Anforderung des Beta-Modells unterstützt einen separaten Formularparameter mit dem Namen `url`. Das GA-Modell schließt diese Informationen in das JSON-Objekt `parameters` ein. Weitere Informationen finden Sie im [API-Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-api-explorer.mybluemix){: new_window}.

- **Gesichtsidentität wird nicht weiter unterstützt**

    Die Identitätsinformationen in der Antwort des GA-Modell "Gesicht" sind veraltet und werden am **2. April 2018** aus der API entfernt. Die Identitätsinformationen beziehen sich auf `name` der Person, `score` und die Knowledge Graph-Funktion `type_hierarchy`.

### 16. Januar 2018
{: #16january2018}

- **Lite-Konto und -Plan ersetzen den kostenfreien Plan**

    Lite-Konten sind kostenlos; eine Kreditkarte ist nicht erforderlich. Allerdings werden Serviceinstanzen des Lite-Plans nach 30 Tagen gelöscht.

    Die maximale Anzahl von API-Aufrufen, die Sie mit dem Lite-Plan vornehmen können, unterscheidet sich geringfügig von dem kostenfreien Plan. Unter dem Lite-Plan können Sie maximal 7.500 API-Aufrufe pro Monat bei 250 Aufrufen pro Tag vornehmen.

    Wenn Sie über benutzerdefinierte Klassifikationsmerkmale verfügen, müssen Sie für das Upgrade auf ein gebührenpflichtiges Konto eine weitere Serviceinstanz erstellen und Ihre benutzerdefinierten Klassifikationsmerkmale erneut erstellen.

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
      <img src="images/tree-flower.jpg" alt="Foto einer Azalee">
      <table>
        <tr>
          <th>Ursprüngliche Tags</th>
          <th>Zusätzliche Tags</th>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: Baum<br/>
          Score: 0,799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: Blume<br/>
          Score: 0,792</td>
        </tr>
        <tr>
          <td>
          Tag: Berg-Azalee<br/>
          Score: 0,696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: Pflanze<br/>
          Score: 0,868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: Azalee<br/>
          Score: 0,617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            Tag: Sumpf-Azalee<br/>
          Score: 0,5</td>
          </td>
          <td></td>
        <tr>
          <td>
            Tag: rötlich-orange Farbe<br/>
          Score: 0,1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Neues Modell für unangemessene Inhalte in Betaversion verfügbar</strong>
      <p>
        Das Modell für unangemessene Inhalte (Explicit), das in der Betaversion eingeführt wird, klassifiziert Bilder danach, ob sie pornografische Inhalte enthalten und für die allgemeine Verwendung ungeeignet sind. Sie können das Modell für unangemessene Inhalte mit anderen Modellen für eine gemeinsame Analyse kombinieren. Beispielsweise können Sie die Klassifikationsmerkmal-IDs `default` und `explicit` in Ihre Anforderung aufnehmen, damit Bildtags zurückgegeben und unangemessene Inhalte ermittelt werden.
      <p>
        Details zum API-Aufruf finden Sie in der Methode **Classify images** (Bilder klassifizieren) in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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
        Die API erzwingt jetzt ein Array, wenn Sie `classifier_ids` als Teil des Objekts **parameters** in der Methode **Bilder klassifizieren** übergeben. Zuvor konnten Sie eine Klassifikationsmerkmal-ID als Zeichenfolge übergeben. Weitere Informationen finden Sie in der Parameterbeschreibung und Beispieldatei in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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

    Details zum API-Aufruf finden Sie unter dem Stichwort **Classify an image** (Bild klassifizieren) in der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

### 16. Mai 2017
{: #16may2017}

- **Neues Klassifikationsmerkmal für Lebensmittel verfügbar: Beta**

    Ein neues Betamodell für die Erkennung von Lebensmitteln bietet eine erweiterte Spezifität und Genauigkeit für Bilder von Lebensmitteln. Die Methode **Bild klassifizieren** gibt Ihnen die Möglichkeit, dieses neue Klassifikationsmerkmal "Lebensmittel" zum Parameter `classifier_ids` hinzuzufügen.

### 5. April 2017
{: #5april2017}

- **Neues {{site.data.keyword.visualrecognitionshort}}-Tool ist verfügbar: Beta**

    Ein neues Beta-Feature, das {{site.data.keyword.visualrecognitionshort}}-Tool, steht unter folgender Adresse zur Verfügung: [https://watson-visual-recognition.ng.bluemix.net/ ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Dieses Tool bietet einen höheren Bedienungskomfort beim Arbeiten mit dem {{site.data.keyword.visualrecognitionshort}}-Service. Nach Eingabe Ihres {{site.data.keyword.cloud_notm}}-API-Schlüssels können Sie eine grafische Benutzerschnittstelle verwenden, mit der Sie auf die Features für allgemeines Tagging und Gesichtserkennung zugreifen und benutzerdefinierte Klassifikationsmerkmale, die Ihrem API-Schlüssel zugeordnet sind, nahtlos und ohne Codierungsaufwand erstellen, neu trainieren und löschen können.

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

    {{site.data.keyword.IBM_notm}} hat die Preise für benutzerdefinierte Klassifikationsmerkmale im {{site.data.keyword.visualrecognitionshort}}-Service gesenkt und das Angebot des kostenfreien Plans erweitert. Weitere Informationen finden Sie auf der [{{site.data.keyword.visualrecognitionshort}}-Seite für die Preisstruktur](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7. Oktober 2016
{: #7october2016}

- **Verbesserungen bei der Gesichtserkennung**

    Der Service bietet einen neuen Algorithmus für die Gesichtserkennung, der die Antworten der Methoden `GET` und `POST /v3/detect_faces` verbessert. Der Service hat das Filtern der Gesichtserkennung (Alter, Name und Geschlecht) mit geringer Verlässlichkeit angepasst. Folglich werden mehr Gesichter gefunden und es werden mehr Verlässlichkeitsbereiche zurückgegeben.

### 8. September 2016
{: #8september2016}

- **Ähnlichkeitssuche (BETA)**

    Benutzer können jetzt ihre eigene Sammlung von Bildern hochladen und die Sammlung anhand eines Bilds nach ähnlichen Bildern durchsuchen. Daraufhin gibt der Service die 100 ähnlichsten Bilder zurück. Die Ähnlichkeitssuche kann für beliebige Zwecke verwendet werden und die Benutzer können jeden Service anhand von Sammlungen von bis zu einer Million Bilder trainieren. Weitere Informationen zur neuen Funktionalität für die Ähnlichkeitssuche finden Sie im [Lernprogramm](/docs/services/visual-recognition/tutorial-collections.html) und auf den Seiten der Veröffentlichung [API Reference ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **Texterkennung ist jetzt für einen exklusiven Benutzerkreis verfügbar (Closed Beta)**

    Die Methoden `POST` und `GET /v3/recognize_text` stehen jetzt wieder einem exklusiven Benutzerkreis zur Verfügung (Closed Beta). {{site.data.keyword.IBM_notm}} unterstützt BETA-Kunden auch weiterhin, die den Service nutzen, und beabsichtigt derzeit nicht, die Beta-Features allgemein zur Verfügung zu stellen (Open Beta).

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
- **Gesichtserkennung:** Verwenden Sie die Methoden `POST` oder `GET /v3/detect_faces`, um Gesichter in Bildern zu erkennen und um Informationen über sie zu sammeln (z. B. die Position des Gesichts in dem Bild sowie die geschätzte Altersgruppe und das Geschlecht jeder Person). Der Service erkennt auch viele bekannte Persönlichkeiten aus dem öffentlichen Leben und kann einen Knowledge Graph bereitstellen, in dem Aggregationen von Interesse in Konzepte einer höheren Ebene durchgeführt werden können.
- **Benutzerdefinierte Klassifikationsmerkmale mit mehreren Facetten:** Sie können jetzt hoch spezialisierte Klassifikationsmerkmale erstellen und definieren, die durch verschiedene Klassen definiert werden. Beispiel: Sie können ein Klassifikationsmerkmal "new\_red\_car" erstellen, das durch die Klassen "new\_cars" und "red\_cars" definiert wird. Weitere Informationen zum Erstellen von Klassifikationsmerkmalen mit mehreren Facetten finden Sie unter [Struktur der Trainingsdaten](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure).
- **Asynchrones Training:** Das Trainieren benutzerdefinierter Klassifikationsmerkmale erfolgt nun asynchron. Das bedeutet, Trainingsaufrufe werden schnell ausgeführt, während Ihr benutzerdefiniertes Klassifikationsmerkmal im Hintergrund weiter dazulernt. Um den Trainingsstatus Ihres benutzerdefinierten Klassifikationsmerkmals zu prüfen und herauszufinden, wann es zur Verwendung verfügbar ist, rufen Sie die Methode `GET /v3/classifiers/{klassifikationsmerkmal-id}` auf und prüfen Sie den Antwortparameter `status`.

### 2. Dezember 2015
{: #2december2015}

Das neueste Release des {{site.data.keyword.visualrecognitionshort}}-Service beinhaltet eine grundlegende Änderung, die eine neue Version der {{site.data.keyword.visualrecognitionshort}}-API (v2) einführt. Version 1 des {{site.data.keyword.visualrecognitionshort}}-Service kann verwendet werden, bis der Betazeitraum des Service abgelaufen ist.

Um sofort mit Version 2 der API arbeiten zu können, müssen Sie folgende Änderungen beachten und Ihren Code entsprechend ändern:

- In Version 1 des Service haben Sie Bilder anhand von Bezeichnungen (Labels) analysiert. In Version 2 des Service werden diese Bezeichnungen **Klassifikationsmerkmale** genannt. Klassifikationsmerkmale haben eine eindeutige Klassifikationsmerkmal-ID, die durch den Parameter `classifier_id` angegeben wird, und einen Kurznamen, der durch den Parameter `name` angegeben wird.
- Die bisherige Methode `POST /v1/recognize` zur Analyse eines Bilds ist nun die Methode [`POST /v2/classify` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window}. Der Parameter `labels_to_check` wurde in `classifier_ids` umbenannt.
- Die bisherige Methode `GET /v1/tag/labels` für das Abrufen einer Liste von Bezeichnungen in Version 1 ist nun die Methode [`GET /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} für das Abrufen einer Liste von Klassifikationsmerkmalen.
- Sie können nicht nur eine Liste mit Klassifikationsmerkmalen abrufen, sondern mit der neuen Methode [`GET /v2/classifiers/{klassifikationsmerkmal-id}` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window} auch Details zu einem Klassifikationsmerkmal abrufen.
- Mit Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API können Sie benutzerdefinierte Klassifikationsmerkmale mit der neuen Methode [`POST /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window} erstellen. Weitere Informationen zum Erstellen von benutzerdefinierten Klassifikationsmerkmalen finden Sie unter [Benutzerdefinierte Klassifikationsmerkmale erstellen](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- Mit Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API können Sie benutzerdefinierte Klassifikationsmerkmale mit der neuen Methode [`DELETE /v2/classifiers` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window} auch löschen.
- Version 2 der {{site.data.keyword.visualrecognitionshort}}-Beta-API erfordert den Parameter `version`. Geben Sie das Freigabedatum der Version der API, die Sie verwenden wollen, im Format `MM-TT-JJJJ` an.
