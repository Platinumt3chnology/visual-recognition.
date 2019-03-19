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

# カスタム物体検出 (ベータ)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} のカスタム物体検出 (ベータ) は、イメージ内のアイテムとその位置を識別します。このサービスは、ユーザーが提供するラベル付きトレーニング・データが含まれるイメージのセットに基づいて、これらのアイテムを検出します。
{: shortdesc}

カスタム物体検出はプライベート・ベータ機能です。このモデルに対して呼び出しを行うには、{{site.data.keyword.IBM_notm}} からの許可が必要です。[アクセスをリクエストしてください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}。ベータ機能について詳しくは、[リリース・ノート](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)を参照してください。
{: important}

ユーザーのワークフローやドメインにとって重要な物体を認識するように、物体検出モデルのトレーニングを行います。例えば、車体の損傷の検出、メンテナンスが必要な機械の検出、または屋外における視覚検査の実施などです。また、物体検出は物体の数を数えたり、在庫を管理したりする場合にも使用できます。

## 物体検出と分類の比較
{: #obj-detect-comparison}

カスタム物体検出モデルは {{site.data.keyword.visualrecognitionshort}} サービスの最新機能で、これには分類が含まれます。

分類と物体検出は似ていますが、用途が異なります。一般に、イメージ内における物体の有無を予測する場合は、分類を使用します。イメージ内で物体の位置を見つけたり物体の数を数えたりする場合は、物体検出を使用します。

### 分類
{: #obj-detect-classify}

イメージを分類する場合、このサービスはイメージ内に対象の物体があることの確率を返します。組み込みモデル (一般、Food、または Explicit) を使用することも、独自のカスタム・モデルを作成することもできます。

例えば、次のイメージのようなクッキーのイメージを分類する場合、このサービスは 95% の信頼度でイメージにクッキーがあることを予測します。

![分類の応答のイメージ](images/cookies-tag.png "分類を表すイメージ")

### 物体検出
{: #obj-detect-detect}

カスタム物体検出はカスタム分類に類似していますが、このサービスはイメージ内におけるアイテムの位置を識別します。分類と同様に、応答には検出した各アイテムのラベルと、その識別に対する信頼度も含まれます。

検出されるアイテムは、物体検出モデルのトレーニングを行う際に提供する情報に基づきます。

以下のイメージでは、カスタム物体検出の **Analyze images** メソッドがイメージ内のクッキーの位置を識別します。検出された各物体には、ラベル (この場合は `Cookie`) に加え、その位置と信頼度が含まれます。

![物体検出の応答のイメージ](images/cookies-bbox.png "物体検出を示すイメージ")

## カスタム物体検出の使用方法
{: #object-detection-sequence}

{{site.data.keyword.visualrecognitionshort}} のカスタム物体検出を使用するには、以下のステップの手順に従ってカスタム物体検出モデルをセットアップします。

1.  コレクションを作成します。コレクションとは、イメージとトレーニング・データのコンテナーです。v4 API リファレンスで、[コレクションの作成 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} を参照してください。
1.  コレクションにイメージを追加します。URL またはファイルを指定してイメージを 1 つずつ追加することも、イメージが複数含まれている `.zip` ファイルをアップロードすることもできます。v4 API リファレンスで、[イメージの追加 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} を参照してください。
1.  イメージにトレーニング・データを追加します。[トレーニング・データの準備](#object-detection-preparation)を参照してください。
1.  コレクションのトレーニングを行います。トレーニング・データが十分に整ったら、コレクション内のイメージに対してトレーニングを開始します。v4 API リファレンスで、[コレクションのトレーニング ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} を参照してください。

これらの手順を実行してコレクションのトレーニングが完了したら、コレクションと突き合わせてイメージの分析を行うことができます。

### トレーニング・データの準備
{: #object-detection-preparation}

セットアップ手順の中で最も重要な部分は、トレーニング・データの準備と組み立てです。イメージを分類するために[カスタム・モデルを作成](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)する場合と同様に、検出する物体を表すイメージのセットを組み立てます。

イメージのセットに加え、イメージごとにトレーニング・データも追加します。物体検出におけるトレーニング・データとは、{{site.data.keyword.visualrecognitionshort}} に認識させるイメージ内の物体 (object) に対応するラベルと位置 (location) をまとめたものです。イメージ内には複数の object が存在する場合があります。

ラベルは、その object が何であるかを示します。location は、それがイメージ内のどこにあるかを示します。位置を示すために、物体の周りに_境界ボックス_ を描いてそのボックスの上部と左方のピクセル座標を示すとともに、幅と高さをピクセルで表します。

以下の例は、`BurntCookie` というラベルが付いた object のトレーニング・データを示しています。

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

この初期のベータ版では、手動で、またはイメージ・アノテーション・ツールを使用して位置情報を作成します。

一般に、トレーニング・データに含めるイメージや境界ボックスの数が多ければ多いほど、トレーニングの効果が上がります。トレーニングを始めるにあたって、次のトレーニング・データのガイドラインをご利用ください。

- 各イメージの高さと幅は両方とも 500 ピクセル以上である。
- コレクション内のラベル付き object にそれぞれ 100 個以上の location (境界ボックス) が含まれている。
- コレクション内の各イメージに含まれる境界ボックスは 10 個を超えない。
- 各境界ボックスのサイズはイメージの寸法の 15% を超える。
- この API がイメージ内の EXIF 方向タグを読み取る。この方向が `location` の座標と一致するようにします。方向を調整するには、ImageMagick などのツールを使用してイメージの_方向を自動調整_ してから境界ボックスを追加します。

**Add training data to an image** メソッドについて詳しくは、[v4 API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window} を参照してください。

### コレクションのトレーニング
{: #object-detection-train}

コレクション内のイメージにトレーニング・データを追加したら、セットアップの最後のステップとして、物体検出モデルのトレーニングを行います。API への単一の呼び出しでトレーニングが開始され、状況情報が含まれる応答が返されます。例えば、以下の状況は、トレーニングが開始したものの、まだ完了していないことを示します。

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

呼び出しを再発行することで、トレーニング・データを更新してからモデルをリトレーニングすることができます。

詳しくは、v4 API リファレンスで、[コレクションのトレーニング ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} を参照してください。

## イメージの分析
{: #object-detection-train}

カスタム物体検出モデルをセットアップしてトレーニングが完了したら、他のイメージで物体を検出できます。分類と同様に、1 つのイメージ、または複数のイメージが入った `.zip` ファイルを追加します。さらにオプションで**しきい値**を指定して、検出される物体の最小スコアを設定することができます。詳しくは、[v4 API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images) で、**Analyze images** メソッドを参照してください。

## 次のステップ
{: #object-detection-next-steps}

- API について詳しくは、[v4 API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg " 外部リンク・アイコン")][api-ref-v4]{: new_window} を参照してください。
