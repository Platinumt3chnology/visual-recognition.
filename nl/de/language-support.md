---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition languages,language support,supported languages

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

# Unterstützte Sprachen

## Bilder klassifizieren
{: #language-support}

Die Methode **Classify images** (Bilder klassifizieren) von {{site.data.keyword.visualrecognitionfull}} unterstützt die Sprachen Englisch (`en`), Arabisch (`ar`), Deutsch (`de`), Spanisch (`es`), Französisch (`fr`), Italienisch (`it`), Japanisch (`ja`), Koreanisch (`ko`), Portugiesisch (Brasilien) (`pt-br`), Chinesisch (Vereinfacht) (`zh-cn`) und Chinesisch (Traditionell) (`zh-tw`).

Die Sprachen funktionieren mit den Ausgabeklassen aller integrierten Modelle: `default` (auch als Modell "Allgemein" bezeichnet), `food` (Lebensmittel) und `explicit` (unangemessene Inhalte).

Details zum API-Aufruf finden Sie in der Methode **Classify images** (Bilder klassifizieren) in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

## Gesichter erkennen
{: #detect_faces}

Die Methoden für **Detect faces** (Gesichter erkennen) geben Übersetzungen der englischen Wörter für die Geschlechter ("Male" und "Female") in der Antwort zurück. Legen Sie die Sprache mit dem Anforderungsheader **Accept-Language** fest.

Weitere Informationen finden Sie im Abschnitt zu **Detect faces** in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.
