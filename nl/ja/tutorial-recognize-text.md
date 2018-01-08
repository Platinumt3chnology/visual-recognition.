---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# 画像内のテキストの認識

{: shortdesc}

## 始めに
{: #copy-credentials}

このチュートリアルの『入門のチュートリアル』でコピーした資格情報を使用します。サービス・インスタンスを作成していない場合は、『[始めに](/docs/services/visual-recognition/getting-started.html#prerequisites)』セクションの手順を実行してください。

## ステップ 1: 画像内のテキストを認識する
{: #recognize-text}

1.  サンプル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> 画像をダウンロードします
1.  `POST /v3/recognize_text` メソッドに対して以下のコマンドを発行し、画像をアップロードして分析します。ユーザー独自の画像を使用する場合、最大サイズは 2 MB です。
    - `{api-key}` を、前にコピーしたサービス資格情報に置き換えます。
    - images\_file ロケーションを変更して、画像を保存した場所を指すようにします。

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    応答には、場所、推定年齢、性別、ID とタイプ階層 (サービスがその顔を認識する場合)、およびそれぞれのスコアが含まれます。

    スコアは 0 から 1 までの範囲で、スコアが高いほど相関性が大きいことを示します。すべての顔が検出されますが、10 個を超える顔がある画像の場合、年齢および性別の信頼度スコアは、スコア 0 が返される可能性があります。


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## 次のステップ

{{site.data.keyword.visualrecognitionshort}} でのデフォルト分類器の使用法について基本的に理解できました。次に、さらに詳細に検討します。

- [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} で、API について学習します。

### 帰属
{: #attributions}

このページで使用された画像はすべて Flikr から提供されたもので、[Creative Commons Attribution 2.0 ライセンス ![外部リンク・アイコン ](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} に基づいて使用されています。これらの画像に変更は加えられていません。
