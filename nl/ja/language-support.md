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

# サポート対象言語

## イメージの分類
{: #language-support}

{{site.data.keyword.visualrecognitionfull}} の **Classify images** メソッドは、英語 (`en`)、アラビア語 (`ar`)、ドイツ語 (`de`)、スペイン語 (`es`)、フランス語 (`fr`)、イタリア語 (`it`)、日本語 (`ja`)、韓国語 (`ko`)、ポルトガル語 (ブラジル) (`pt-br`)、中国語 (簡体字) (`zh-cn`)、および中国語 (繁体字)(`zh-tw`) をサポートします。

これらの言語は、すべての組み込みモデル (`default` (一般モデルとも呼ぶ)、`food`、および `explicit` の各モデル) の出力クラスでサポートされています。

API 呼び出しについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window} 内の **Classify images** メソッドを参照してください。

## 顔検出
{: #detect_faces}

**Detect faces** メソッドは、応答として、英語で性別を表す単語 (「Male」と「Female」) の翻訳を返します。言語は **Accept-Language** 要求ヘッダーで設定します。

詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window} 内の **Detect faces** メソッドを参照してください。
