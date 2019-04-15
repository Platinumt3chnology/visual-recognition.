---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

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

<!-- Link definitions -->

[api-ref-text]: https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text

# 自然の情景の中のテキストの認識 (ベータ)
{: #recognize-text}

{{site.data.keyword.visualrecognitionshort}} ベータ版のテキスト・モデルを使用して、画像内の英語のテキストを検出して認識します。 Text モデルは、文書内の高密度のテキストではなく、画像内の情景テキストを認識するように設計されています。

Text モデルはプライベート・ベータ機能です。このモデルを呼び出すには、{{site.data.keyword.IBM_notm}} の許可が必要です。[アクセスをリクエストしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://datasciencex.typeform.com/to/nU6efl){: new_window}。ベータ機能について詳しくは、[リリース・ノート](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)を参照してください。
{: important}

テキスト・モデルは、短いテキスト・ストリングに最も効果的です。 例えば、テキスト・モデルの一般的な使用に、標識の読み取りがあります。

![道路標識で、認識された単語の周囲に境界ボックスが表示されている。 Unsplash での Ashim D’Silva による写真](images/walk-signal-detection.png) ![道路標識の画像で検出された単語と信頼性スコア](images/walk-signal-response.png)

白いボックスは、このモデルが画像で認識した各単語を示しています。

## 応答
{: #recognize-text-response}

応答には、検出されたストリングが含まれ、そのストリング内の各単語は、以下の情報で識別されています。

- 認識された単語。
- 単語の認識の信頼度を示すスコア。
- 単語の文字枠の位置。 この枠は、その単語が画像内のどこにあるかを示します。
- 単語が検出された行番号。

## 効果的なテキスト認識のためのガイドライン
{: #recognize-text-guidelines}

以下のガイドラインに適合している場合、画像内のテキストが効果的に認識されます。

- テキストが、製品コードのような文字列ではなく、主にフルワードである。 モデルは、個々の文字ではなく単語を認識し、1 文字の「単語」や数字を破棄する可能性があります。
- テキストが、様式化されたフォントではなく、標準フォントで表示されている。 例えば、自動車のナンバー・プレートや映画のポスターのタイトルのテキストは、認識されない可能性があります。 同様に、手書きのテキストも認識されない可能性があります。
- Text モデルは、主に英語の単語でトレーニングされる。他の言語のテキストは、おそらく認識されません。

## 次のステップ
{: #recognize-text-next-steps}

- 画像内のテキストを認識させるために[呼び出しを実行](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text)します。
- API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window} を参照してください。
