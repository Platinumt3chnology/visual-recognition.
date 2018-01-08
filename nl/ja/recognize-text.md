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

# 自然の情景の中のテキストの認識

ベータ版のテキスト・モデルを使用して、画像内の英語のテキストを検出して認識します。テキスト・モデルは、文書の高密度のテキストではなく、画像に写された情景の中のテキストを認識するように設計されています。

テキスト・モデルはベータ機能であり、実稼働環境での使用を意図したものではありません。詳しくは、[リリース情報](/docs/services/visual-recognition/release-notes.html#beta)の『ベータ機能』を参照してください。
{: tip}

テキスト・モデルは、短いテキスト・ストリングに最も効果的です。例えば、テキスト・モデルの一般的な使用に、道路標識の読み取りがあります。

![検出された単語を枠で囲んだ道路標識](images/road-sign-text-detection.png)

![道路標識の画像で検出された単語と信頼度スコア](images/road-sign-text-response.png)

白い枠は、モデルが画像で検出した各単語を示しています。

## 応答

応答には、検出されたストリングが含まれ、そのストリング内の各単語は、以下の情報で識別されています。

- 検出された単語
- 検出された単語の正確性の信頼度を示すスコア。
- 単語の文字枠の位置。この枠は、その単語が画像内のどこにあるかを示します。
- 単語が検出された行番号。

## 効果的なテキスト認識のためのガイドライン

以下のガイドラインに適合している場合、画像内のテキストが効果的に認識されます。

- テキストが、製品コードのような文字列ではなく、主にフルワードである。モデルは、個々の文字ではなく単語を認識し、1 文字の「単語」や数字を破棄する可能性があります。
- テキストが、様式化されたフォントではなく、標準フォントで表示されている。例えば、自動車のナンバー・プレートや映画のポスターのタイトルのテキストは、認識されない可能性があります。同様に、手書きのテキストも認識されない可能性があります。
- テキストが画像の少なくとも 5% を占めている。
- テキストの傾斜が水平から 45 度以下である。ベータ版のテキスト・モデルは、EXIF タグを読み取り、画像を回転させます。ただし、最高のスループットを得るには、サービスで回転させる必要のない画像を送信してください (EXIF の**「方向 (Orientation)」**タグは、`「1」` に設定されています)。
- テキスト・モデルは、英語の単語に基づいてトレーニングされています。他の言語のテキストは、認識されない可能性があります。

## 次のステップ

[API explorer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window} で、API について習得します。

テキスト・モデルに関する質問やコメントは、Kevin Gong (kgong@us.ibm.com) にご連絡ください。

---

メイン[資料](/docs/services/visual-recognition/index.html)に移動する。
