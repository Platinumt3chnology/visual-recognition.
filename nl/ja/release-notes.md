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

# リリース情報
{: #release-notes}

本サービスに対する以下の新機能および変更点があります。
{: shortdesc}

## サービス API のバージョン管理
{: version}

API 要求には、`version=YYYY-MM-DD` という形式で日付を設定する version パラメーターが必要です。後方互換性のない方法で API が変更されると、API の新規マイナー・バージョンがリリースされます。

API 要求のたびに version パラメーターを送信してください。サービスでは、指定された日付の API バージョン、またはその日付より前の最新のバージョンが使用されます。現在日付をデフォルトに設定しないでください。代わりに、ご使用のアプリと互換性のあるバージョンに一致する日付を指定し、より新しいバージョン用にアプリの準備ができるまでその日付を変更しないでください。

現行バージョンは `2018-03-19` です。

## ベータ機能
{: #beta}

{{site.data.keyword.IBM_notm}} は、お客様の評価を得るために、ベータとして分類されるサービス、機能、および言語サポートをリリースしています。 これらの機能は、不安定であったり、頻繁に変更される可能性があったり、短い通知期間で中止されたりする可能性があります。 また、ベータ機能は、一般出荷可能機能と同レベルのパフォーマンスや互換性を提供しない可能性もあり、実稼働環境での使用を意図したものではありません。 ベータ機能は、[IBM Developer Answers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} でのみサポートされます。

## 変更内容
{: #changelog}

本サービスに対する以下の新機能および変更点があります。

### 2019 年 1 月 15 日
{: #15january2019}

- **Detect Faces での性別の翻訳**
    - **Detect Faces** メソッドは、**Accept-Language** 要求ヘッダーで言語を指定した場合、「Male」と「Female」に相当する翻訳ラベルを返すようになりました。詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window} を参照してください。

### 2018 年 10 月 1 日
{: #01october2018}

- **2018 年 5 月 23 日より前に作成されたサービス・インスタンスが削除される**

    - 以前に通知されたとおり、2018 年 5 月 23 日より前に作成された {{site.data.keyword.visualrecognitionshort}} のすべてのインスタンスがアクティブでなくなりました。それらのインスタンスのデータは削除されます。新規サービス・インスタンスへの移行方法について詳しくは、[マイグレーション](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)を参照してください。
    - この日付の後に作成されたサービス・インスタンスは影響を受けません。
    - ご不明な点については、[IBM サポート ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/ibmcloudsupport){: new_window} にお問い合わせください。

### 2018 年 8 月 1 日
{: #01august2018}

- **Food モデルと Explicit モデルの一般出荷版**

    Food モデルと Explicit モデルが、ベータ版から一般出荷版 (GA) に移りました。Food モデルは、一般 (default) モデルより多くの食品と料理を認識します。Explicit モデルは、わいせつ画像と見なされる可能性があるイメージを識別します。

    コードの変更は不要です。これらのモデルは両方とも、ライト・プランでは無料、標準プランでは 1 画像につき $0.002 です。

    詳しくは、<em>Watson ブログ</em>の [Updates to Watson Visual Recognition ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://ibm.biz/visrec-price-reduction){: new_window} を参照してください。

### 2018 年 7 月 1 日
{: #01july2018}

- **カスタム・モデルの新料金**
    - 2018 年 7 月 1 日以降、カスタム・モデルによる画像分類の新料金は、旧料金の半額です。1 画像につき $0.002 となりました。詳細や他の重要情報については、<em>Watson ブログ</em> の [Updates to Watson Visual Recognition \- Price reduction for Custom Classification ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/visrec-price-reduction){: new_window} を参照してください。

### 2018 年 6 月 21 日
{: #21june2018}

- **追加の言語サポート**

    - **Classify** メソッドが、`default` (一般) モデル・クラスの出力で中国語 (簡体字と繁体字) およびポルトガル語 (ブラジル) をサポートするようになりました。言語の詳細リストについては、[サポート対象言語](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)を参照してください。
    - さらに **Food** モデルと **Explicit** モデルからの応答ですべての言語がサポートされるようになりました。


### 2018 年 5 月 22 日
{: #22may2018}

- **新しい API 認証プロセス**:

    新しいエンドポイントで ID およびアクセス管理 (IAM) による認証が行われるようになりました。

    - 新規インスタンスでは、別のエンドポイント URL を使用してください。デフォルトのエンドポイントは `https:/gateway.watsonplatform.net/visual-recognition/api/` です。ご使用のサービス・インスタンスの URL を確認するには、{{site.data.keyword.cloud_notm}} [ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/dashboard/apps?watson){: new_window} でそのインスタンスをクリックして、資格情報を確認します。
    - API に対する認証方法を変更します。サービス・インスタンスの IAM キーまたはアクセス・トークンを指定します。例については、[マイグレーション](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)を参照してください。

    2018 年 5 月 23 日より前に作成されたサービス・インスタンスについては、認証プロセスとエンドポイントが変更されていません。`api_key` 照会パラメーターを指定することによって認証します。

- **ライト・プランの更新**

    2018 年 5 月 22 日より後に作成されたライト・プランは、以下のように変更されます。

    - ライト・プランの新しいインスタンスは、毎月使用する場合、30 日経過後も引き続き使用できます。
    - 新しいライト・プランでは、2 つのカスタム・モデルを作成してリトレーニングできます。
    - ライト・プランでは、1 カ月あたり最大 1,000 個のイベントを処理できます。分類、検出、またはトレーニングのために送信される画像 1 つにつき、1 つのイベントとなります。Core ML モデルのダウンロードは、イベント制限のカウントの対象外です。

    ライト・プランの制限を超過する必要がある場合は、有料アカウントに更新します。価格プランを [確認 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} してください。

- **機密保護**:

    資料が更新されて、データ・プライバシーに関する新しい詳細情報が追加されました。それらの詳細情報については、[機密保護](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security)を参照してください。

### 2018 年 4 月 12 日
{: #12april2018}

- **ライト・プランでカスタム・モデルのリトレーニングをサポート**

    ライト・プランで、カスタム・モデルを更新またはリトレーニングする必要がある場合に、そのモデルを削除して別のカスタム・モデルを作成する必要がなくなりました。同プランの 1 日および 1 カ月あたりの[制限](https://console.bluemix.net/catalog/services/visual-recognition)内で使用する限り、カスタム・モデルを更新できるようになりました。

    複数のモデルを所有する必要がある場合、または同じモデルの複数のバージョンを所有する必要がある場合は、ライト・プランから有料アカウントに更新してください。

- **CORS をサポートする新規マイナー・バージョン**

    **バージョン:** `2018-03-19`

    要求で `version=2018-03-19` を指定する場合に、クロス・オリジン・リソース共有 (CORS) ヘッダーをサポートするようになりました。

### 2018 年 4 月 5 日
{: #5april2018}

- **Face モデルのスコアに関する問題の修正**

  Face モデルでの年齢スコアの範囲が、元の範囲である、0 から 1 に戻されました。詳しくは、2018 年 4 月 2 日の[既知の問題](#2april2018)を参照してください。

- **新しいフォーム・データ・パラメーター**

    **Classify images** メソッドと **Detect faces in images** メソッドが、新しいフォーム・データ・パラメーターをサポートするようになりました。Classify images は、`url`、`classifier_ids`、`threshold`、`owners` という別々のパラメーターをサポートし、Detect faces は `url` をサポートします。

    以前は、JSON ストリングに値をエンコードし、**parameters** フォーム・データ・パラメーターを渡していました。今後はすべてのアプリケーション開発で、それらの値を別々のフォーム・データ・パラメーターで渡すという新しい方式を使用することができます。詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition){: new_window} を参照してください。

### 2018 年 4 月 2 日
{: #2april2018}

- **拡張された Face モデルの一般出荷版**

    更新された顔検出モデルが一般出荷版 (GA) になりました。

    この拡張モデルでは、より広範なトレーニング・データ・セットを使用することによって、顔検出での年齢と性別に関する正確度が向上します。例えば、年齢予測が向上して、`min` と `max` の間の範囲が縮小しています。以前のモデルにおける 9 年という固定範囲は、より短い動的範囲に置き替わりました。平均年齢範囲は 4.9 年になりました。

    - API の変更点

    拡張 Face モデルと旧 Face モデルとの間の他の相違点は以下のとおりです。
        - 拡張モデルは、.gif と .tif の画像形式をサポートします。
        - 拡張モデルは、より大きいファイル・サイズをサポートしています。画像ファイルは最大 10 MB、.zip ファイルは最大 100 MB までサポートされます。
        - 拡張モデルでは、応答に `FaceIdentity` 情報が含まれません。この ID 情報とは、人物の名前 (`name`)、`score`、`type_hierarchy` ナレッジ・グラフを指します。

    API について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window} を参照してください。

    - 既知の問題

        - form パラメーターに **Content-Type** を含めることができません。例えば、以下の要求は、`;type=text/plain` が含まれるため、**url** パラメーターを分析できません。

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - 年齢スコアの範囲は 0 から 0.3 です。元の範囲である 0 から 1 に戻すように修正しています。

    - 非推奨になったベータ・エンドポイント

    `/v3/detect_faces_beta` のベータ・エンドポイントは非推奨となりました。2018 年 5 月 17 日より後にはアクセスできません。要求が `/v3/detect_faces` を指すようにしてください。

### 2018 年 3 月 20 日
{: #20march2018}

- **Apple Core ML との統合**

    {{site.data.keyword.visualrecognitionshort}} は、Apple Core ML モデル形式をサポートするようになりました。iOS アプリで Core ML バージョンの {{site.data.keyword.visualrecognitionshort}} モデルを使用できます。

    **開発を始める**: {{site.data.keyword.visualrecognitionshort}} と Core ML での開発を始めるには、GitHub で以下のプロジェクトを確認してください。

    - 画像をローカルで分類する: [{{site.data.keyword.visualrecognitionshort}} with Core ML ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}。
    - {{site.data.keyword.discoveryfull}} と結果を統合する: [{{site.data.keyword.visualrecognitionshort}} and Discovery with Core ML ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}。
    - SDK を探索する: [Swift SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}。

- **API の変更点**

    この統合では、後方互換性のある以下の変更が API に加えられています。

    - 分類器モデルを Core ML モデルとしてダウンロード可能かどうかを示す、新しい `core_ml_enabled` フィールド。このフィールドは、`GET および POST /v3/classifiers` と `GET /v3/classifiers/{classifier_id}` への呼び出しの応答で返されます。
    - Core ML モデルを .mlmodel ファイルとしてダウンロードするための、新しい `GET /v3/classifiers/{classifier_id}/core_ml_model` メソッド。3 月 19 日より後に作成されたカスタム・モデルでは、Core ML モデル・ファイルをダウンロードできます。
    - モデルの最新トレーニング日が設定される、新しい `updated` フィールド。`updated` フィールドは、`retrained` フィールドまたは `created` フィールドのいずれかと一致します。

    Core ML のための API の変更について詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window} を参照してください。

- **新しいツールを使用可能: Watson Studio**

    [Watson Studio ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")][watson-studio-reg]{: new_window} は、ベータ版 {{site.data.keyword.visualrecognitionshort}} ツールの代替となるツールが組み込まれた、新しい統合環境です。Watson Studio は、{{site.data.keyword.visualrecognitionshort}} だけでなく、{{site.data.keyword.cloud_notm}} の他の多くのサービスとリソースをサポートしています。{{site.data.keyword.visualrecognitionshort}} の既存のすべてのインスタンスおよび分類器と一緒に、Watson Studio を使用できます。

     Watson Studio は、クラウドでのコラボレーティブ環境を実現します。Watson Studio を利用すると、開発者、対象分野の専門家、データ・サイエンティスト、その他の要員が、{{site.data.keyword.visualrecognitionshort}} モデルや他の AI モデルを作成してトレーニングすることができます。また、Watson Studio を使用して、組み込みの一般モデルと Face モデルにアクセスすることもできます。

     Watson Studio は Core ML もサポートしています。カスタム・モデル用に Core ML モデル・ファイルをダウンロードすることができます。

    Watson Studio の[使用を開始 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")][watson-studio-reg]{: new_window} してみてください。

- **カスタム・モデル用のディープ・ラーニング・アーキテクチャーの更新**

    {{site.data.keyword.visualrecognitionshort}} は、より高速で効率的なディープ・ラーニング・ネットワーク・アーキテクチャーを分類のために使用するようになりました。また、更新されたモデルを使用することで、最上位クラスとその他のクラスとの差異をより明確にすることができます。この方式により、トレーニング時間が多少長くなる可能性があります。この新しいアーキテクチャーは、新しいカスタム・モデルのトレーニングに使用されます。既存の旧モデルをリトレーニングする場合は、元のアーキテクチャーが使用されます。

    以下の例は、新しいアーキテクチャーによる差異化を示しています。

    ![アーチェリーの弓と矢を握る人。Unsplash での Annie Spratt による写真](images/archery.jpg)

    <table>
      <tr>
        <th>元のクラスとスコア</th>
        <th>更新後のクラスとスコア</th>
      </tr>
      <tr>
        <td>Archery</br>0.99 </td>
        <td><strong>archery<strong></br>0.9</td>
      </tr>
      <tr>
        <td>Auto Racing</br>0.996398</td>
        <td><strong>biking</strong></br>0.004</td>
      </tr>
      <tr>
        <td>Biking</br>0.0500174</td>
        <td><strong>fishing</strong></br>0.001</td>
      </tr>
      <tr>
        <td>Fishing</br>0.11029</td>
        <td><strong>golf</strong></br>0.031</td>
      </tr>
      <tr>
        <td>Golf</br>0.0980796</td>
        <td><strong>gymnastics</strong></br>0.029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0.964391</td>
        <td><strong>judo</strong></br>0.021</td>
      </tr>
      <tr>
        <td>Judo</br>0.339119</td>
        <td><strong>racing</strong></br>0.002</td>
      </tr>
      <tr>
        <td>Skating</br>0.0393602</td>
        <td><strong>skating</strong></br>0.061</td>
      </tr>
      <tr>
        <td>Skiing</br>0.0310527</td>
        <td><strong>skiing</strong></br>0.003</td>
      </tr>
      <tr>
        <td>Track and Field</br>0.208147</td>
        <td><strong>track</strong></br>0.035</td>
      </tr>
    </table>

- **フランス語の言語サポート**

    **Classify** メソッドが、`default` モデル・クラスの出力でフランス語をサポートするようになりました。言語の詳細リストについては、[サポート対象言語](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)を参照してください。

### 2018 年 2 月 23 日
{: #23february2018}

- **拡張された Face モデルをベータ版で使用可能**

    更新された顔検出モデルを使用できます。このベータ版モデルでは、より広範なトレーニング・データ・セットを使用することによって、顔検出での年齢と性別に関する正確度が向上します。詳しくは、[Increasing the Accuracy of IBM’s Watson {{site.data.keyword.visualrecognitionshort}} service ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} および [Mitigating Bias in AI Models ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window} を参照してください。

    - 更新されたモデルの結果は、[デモ ![外部リンク・アイコン ](../../icons/launch-glyph.svg "外部リンク・アイコン")][demo]{: new_window} およびベータ版の [Visual Recognition ツール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} で参照できます。
    - ベータ版モデルは `/v3/detect_faces_beta` にあります。

    ベータ版モデルと一般出荷版 (GA) モデルの違いは以下のとおりです。
    - ベータ版モデルは、.gif と .tif の画像形式をサポートします。この拡張は、GA モデルに適用される見込みです。
    - ベータ版モデルは、より大きいファイル・サイズをサポートしています。画像ファイルは最大 10 MB、.zip ファイルは最大 100 MB までサポートされます。この拡張は、GA モデルに適用される見込みです。
    - ベータ版の顔検出では、応答に `FaceIdentity` 情報が含まれません。
    - ベータ版モデルの POST 要求では、空でないファイル名が必須です。GA の Face モデルでは、この制約が適用されません。
    - ベータ版モデルの POST 要求では、`url` という、別個の form パラメーターがサポートされます。GA モデルでは、その情報が `parameters` JSON オブジェクトに格納されます。詳しくは、[API explorer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-api-explorer.mybluemix){: new_window} を参照してください。

- **非推奨になった Face の ID**

    GA の Face モデルの応答における ID 情報が非推奨になったため、**2018 年 4 月 2 日**に API から削除されます。この ID 情報とは、人物の名前 (`name`)、`score`、`type_hierarchy` ナレッジ・グラフを指します。

### 2018 年 1 月 16 日
{: #16january2018}

- **無料プランがライト・アカウント/プランに置き換わる**

    ライト・アカウントは無料で、クレジット・カードは不要です。ただし、ライト・プランのサービス・インスタンスは、30 日が経過すると削除されます。

    ライト・プランで発行できる API 呼び出しの最大数は、無料プランと若干異なります。ライト・プランでは、1 日あたり 250 回の呼び出し、1 カ月あたり最大 7,500 回の API 呼び出しを行うことができます。

    カスタム分類器がある場合に有料アカウントに更新するには、別のサービス・インスタンスを作成し、カスタム分類器を再作成してください。

### 2017 年 12 月 11 日
{: #11december2017}

<ul>
  <li>
    <strong>一般モデルでの正確度と出力の向上</strong>
      <p>
        一般モデル (数千のタグが含まれて組み込まれている) は、より 2 次的な対象を検出するようになり、情景の検出が改善されました。 こうした改善は、画像のあまり目立たない側面を認識するのに役立ちます。 さらに、画像ごとに返されるタグの平均数が 10 に増えました。
      </p>
      <p>
        以下の画像は、更新前に返されたタグと、現在返される追加タグの例を示しています。
      </p>
      <img src="images/tree-flower.jpg" alt="アザレア (植物) の写真">
      <table>
        <tr>
          <th>元のタグ</th>
          <th>追加タグ</th>
        </tr>
        <tr>
          <td></td>
          <td>
          タグ: tree<br/>
          スコア: 0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          タグ: flower<br/>
          スコア: 0.792</td>
        </tr>
        <tr>
          <td>
          タグ: alpine azalea<br/>
          スコア: 0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          タグ: plant<br/>
          スコア: 0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          タグ: azalea<br/>
          スコア: 0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            タグ: swamp azalea<br/>
          スコア: 0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            タグ: reddish orange color<br/>
          スコア: 0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>新規の Explicit モデルをベータ版で提供</strong>
      <p>
        Explicit モデル (ベータ版で開始) は、画像にわいせつなコンテンツが含まれていて、一般用として不適切なものであるかどうかを分類するものです。 Explicit モデルを他のモデルと一緒に含めて、組み合わせて分析を行うことができます。 例えば、`default` 分類器 ID と `explicit` 分類器 ID の両方を要求に含めて、画像タグと、画像に不適切な表現のコンテンツが含まれているかどうかを返すようにします。
      <p>
        API 呼び出しについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg " 外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#classify-images) の **Classify images** メソッドを参照してください。
      </p>
    </li>
    <li>
      <strong>より大きいファイル・サイズのサポート</strong>
      <p>
        <strong>「画像分類 (Classify images)」</strong>のメソッドは、10 MB までの画像ファイルおよび 100 MB までの .zip ファイルをサポートするようになりました。
    </li>
    <li>
      <strong>分類器 ID の引き渡し時に配列が必要</strong>
      <p>
        API では、**「画像分類 (Classify images)」**のメソッドで**「パラメーター (parameters)」**オブジェクトの一部として `classifier_ids` を渡す際に、配列を適用するようになりました。 以前は、分類器 ID をストリングとして渡すことができました。 詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#classify-images) のパラメーターの説明およびサンプル・ファイルを参照してください。
      </p>
    </li>
</ul>

### 2017 年 9 月 8 日
{: #8september2017}

- **ベータ版の Similarity Search およびコレクションは終了しました**: 2017 年 9 月 8 日現在、 Similarity Search のベータ期間は終了しています。 詳しくは、[Visual Recognition API – Similarity Search Update ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window} を参照してください。

### 2017 年 6 月 30 日
{: #30june2017}

- **タグ付けの改善**: デフォルト分類器のトレーニング画像の数を増やしました。 これにより、画像の全体的な「情景」を正確に認識できるようになります。 詳しくは、[Further Enhancements for General Tagging Feature ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window} を参照してください。
- **追加言語**: **「画像分類 (Classify images)」**のメソッドでは、英語、アラビア語、スペイン語、日本語に加えて、韓国語、イタリア語、およびドイツ語をサポートするようになりました。

    API 呼び出しについて詳しくは、『[API reference ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}』内の**「Classify images」**メソッドを参照してください。

### 2017 年 5 月 16 日
{: #16may2017}

- **新しい食品分類器が使用可能: ベータ**

    新しいベータ食品認識モデルは、食品の画像の特異性および正確度の向上を実現します。 **「画像分類 (Classify an image)」**メソッドでは、この新しい分類器「food」を `classifier_ids` パラメーターに追加できます。

### 2017 年 4 月 5 日
{: #5april2017}

- **新規 {{site.data.keyword.visualrecognitionshort}} ツールが使用可能: ベータ**

    新しいベータ機能である {{site.data.keyword.visualrecognitionshort}} ツールが [https://watson-visual-recognition.ng.bluemix.net/ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} で利用可能です。 このツールを使用すると、{{site.data.keyword.visualrecognitionshort}} サービスをより簡単に操作できるようになります。 {{site.data.keyword.cloud_notm}} API キーを入力することで、GUI を使用して「全般的タグ付け」機能や「顔検出」機能にアクセスできるだけでなく、API キーに関連付けられたカスタム分類器の作成、リトレーニング、 および削除をシームレスに実行することができ、コーディングの必要がありません。

### 2017 年 3 月 8 日
{: #8march2017}

- **一般分類器タグ付けの言語サポートの更新**

    一般分類器は、サポートされるすべての言語でタグを返すようになりました。

- **既知の問題**

    **修正 04-13-2017**: トレーニングまたはリトレーニング中に、状況を確認するために繰り返し `GET /classifiers` を呼び出した結果、トレーニング・ジョブが強制終了されることがあります。 この問題の回避策として、`GET /classifiers/{classifier_id}` を使用して新規分類器の状況をポーリングします。 つまり、この問題を引き起こす可能性がある、すべての分類器を取得する `GET /classifiers` ではなく、単一分類器 ID 用の分類器 `GET` を使用します。 `GET /classifiers/{classifier_id}` は、より高速でもあります。

### 2016 年 12 月 15 日
{: #15december2016}

- **一般分類器タグ付けの改善**

    - 一般分類器のディープ・ラーニング・アルゴリズムが更新されました。 すべての言語のタグの品質が大きく改善され、サービスが返す英語のタグの量が大幅に増えました。 ユーザー独自のカスタム分類器を作成する場合も、高品質のタグ出力が得られます。
    - カラーのタグ付けが追加されました。 サービスは、画像内の上位 1 つまたは 2 つのカラーを返すようになりました。

- **既知の問題**

    - EXIF メタデータ・タグを使用してデモに送信される画像は、サービスに対して方向 (横長と縦長) を正しく指定しません。 iPhone でアップロードされた画像には、EXIF メタデータ・タグが含まれていることがあります。 この問題の回避策は、画像メタデータを更新して、EXIF メタデータ・タグに依存しないで画像の方向を指定するようにすることです。 多くの場合、コンピューターで画像を開き、それを保存するだけで、これを達成できます。 例えば、Mac では、画像をプレビューで開き、その画像を保存すると、正しい方向のタグが設定されます。
    - {{site.data.keyword.visualrecognitionshort}} サービスに画像を送信する際に、[EXIF タグ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://en.wikipedia.org/wiki/Exif){: new_window} 値を 8、3、または 6 に指定すると、待ち時間が増えることがあります。 サービスは、画像のピクセルをエンコードされた視点に回転させます。 画像を事前に回転させるか、あるいは {{site.data.keyword.visualrecognitionshort}} タスクにとって重要でない場合は EXIF ヘッダーを削除すると、時間を節約できます。

### 2016 年 12 月 1 日
{: #1december2016}

- **新しい料金**

    {{site.data.keyword.IBM_notm}} は、{{site.data.keyword.visualrecognitionshort}} サービス上のカスタム分類器の料金を引き下げ、無料プランで利用できる内容を増やしました。 詳しくは、[{{site.data.keyword.visualrecognitionshort}} Pricing ページ](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)を参照してください。

### 2016 年 10 月 7 日
{: #7october2016}

- **顔検出の機能拡張**

    本サービスは、`GET` メソッドおよび `POST /v3/detect_faces` メソッドの応答を改善する、新しい顔検出アルゴリズムを採用しています。 本サービスでは、信頼度の低い、年齢、名前、および性別の顔検出のフィルター処理を調整しました。 その結果、より多くの顔が検出され、より広範囲の信頼度が返されるようになりました。

### 2016 年 9 月 8 日
{: #8september2016}

- **Similarity Search BETA**

    ユーザーは独自に収集した画像をアップロードし、1 つの画像を使用して、その類似した画像の集合を検索できるようになりました。この場合、サービスは上位 100 件の最も類似した画像を返します。 類似性の検索はどのような目的にも使用できます。ユーザーは、それぞれ最大 100 万件の画像の集合に対して本サービスをカスタム・トレーニングできます。 新規の類似性検索機能について詳しくは、[チュートリアル](/docs/services/visual-recognition/tutorial-collections.html)、および [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} のページを参照してください。

- **テキスト認識はクローズド・ベータになる**

    `POST` メソッドと `GET /v3/recognize_text` メソッドは、クローズド・ベータに戻りました。 {{site.data.keyword.IBM_notm}} は、このサービスを使用する BETA のお客様のサポートを継続する意向ですが、現在のところ、再びオープン・ベータについての計画はありません。

### 2016 年 8 月 1 日

- **導入価格の終了**

    カスタム分類器のトレーニングおよびリトレーニング、カスタム画像分類、およびカスタム分類器保管は、無料ではなくなりました。 料金については、{{site.data.keyword.visualrecognitionshort}} サービスの [pricing ページ](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)を参照してください。

### 2016 年 7 月 5 日
{: #5july2016}

- **カスタム分類器の更新**

    カスタム分類器は、一定のトレーニング・データ・セットに制限されなくなりました。 ユーザーは、新規画像を使用して既存の分類器を更新したり、正例または負例の分類器を既存のトレーニング済み分類器に追加したりできます。 Watson が学習するための追加のサンプル画像を提供することにより、サービスはユーザーの分類器をより正確なものにできます。 カスタム分類器は、長い時間をかけて学習することが可能になり、可視情報の理解が継続的に向上します。

- **既知の問題**

    **修正 04-13-2017**: ユーザーは、既存の分類器を更新した 30 秒後または 90 秒後に 500 エラー・コードを受け取ることがあります。 エラーにもかかわらず、リトレーニング要求は正常に完了する可能性が十分あります。 少なくとも 2 分間待ってから、`GET classifiers/{classifier\_id}` メソッドを使用して、分類器の状況を確認してください。 状況が「ready」で、「retrained」タイム・スタンプが更新されていれば、500 コードを生成したリトレーニング要求は正常に実行済みです。 あるいは、「retrained」タイム・スタンプが更新されていない場合は、リトレーニングが失敗した理由を示す説明が応答に追加されており、サービスはリトレーニング要求が出される前に存在したバージョンの分類器に戻します。

### 2016 年 5 月 20 日
{: #20 may 2016}

これは、{{site.data.keyword.visualrecognitionshort}} サービスの一般出荷版です。 このリリースでは、バージョン 3 のサービスが導入されており、これは互換性を破る重要な変更です。 このリリースには、非推奨になった AlchemyVision サービスからの機能が取り込まれています。

サービスがベータ版の間に作成されたカスタム分類器はすべて、サービスの GA インスタンスで再作成する必要があります。

{{site.data.keyword.visualrecognitionshort}} サービスに対して、以下の変更および更新が行われました。

- **バージョンの日付:** このリリースの機能を使用するには、`version` パラメーターの値として `2016-05-20` を使用します。
- **クラスと分類器:** 単一の分類器は「クラス」と呼ばれるようになりました。 GA では、クラスのグループを「分類器」と呼びます。
- **分類:** デフォルトのクラスを使用して各種の対象や情景を素早く正確に識別するには、`POST` メソッドまたは `GET /v3/classify` メソッドを使用します。
- **顔検出:** 画像内の顔を検出し、それに関する情報 (顔が画像のどの位置にあるかや、それぞれの顔の推定年齢層や性別など) を取得するには、`POST` メソッドまたは `GET /v3/detect_faces` メソッドを使用します。 また、サービスでは、名前によって多くの有名人を特定したり、ナレッジ・グラフを提供して、ユーザーが関心のある集計を行ってより上位の概念に集約できるようにしたりすることもできます。
- **多面的なカスタム分類器:** いくつかのクラスで定義された非常に特化された分類器を作成し、トレーニングできるようになりました。 例えば、クラス「new\_cars」と「red\_cars」で定義された「new\_red\_car」分類器を作成できます。 多面的な分類器の作成について詳しくは、[トレーニング・データの構造](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure)を参照してください。
- **非同期トレーニング:** カスタム分類器のトレーニングは、非同期になりました。これにより、カスタム分類器はバックグラウンドで学習を継続しながら、トレーニングの呼び出しを迅速に完了できます。 カスタム分類器のトレーニング状況を調べて、使用可能になる時期を確認するには、`GET /v3/classifiers/{classifier_id}` メソッドを呼び出して、`status` 応答パラメーターを確認します。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} サービスの最新リリースでは、新規バージョンの {{site.data.keyword.visualrecognitionshort}} API (v2) が導入され、互換性を破る重要な変更が行われています。 {{site.data.keyword.visualrecognitionshort}} サービスのバージョン 1 は、このサービスのベータ版が終了するまで使用可能です。

API のバージョン 2 の使用をすぐに開始するには、以下の変更を理解し、変更を反映させるようにコードを更新します。

- バージョン 1 のサービスでは、ラベルによって画像を分析しました。 バージョン 2 のサービスでは、ラベルは**分類器**と呼ばれます。 分類器には、`classifier_id` パラメーターで示される固有の分類器 ID と、`name` パラメーターで示される短い名前があります。
- 画像を分析するための `POST /v1/recognize` メソッドは、[`POST /v2/classify` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window} メソッドになりました。 `labels_to_check` パラメーターは、`classifier_ids` に名前変更されました。
- V1 でラベルのリストを取得するための `GET /v1/tag/labels` メソッドは、分類器のリストを取得するための [`GET /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} メソッドになりました。
- 分類器のリストを取得するのに加えて、新規 [`GET /v2/classifiers/{classifier_id}` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window} メソッドを使用して、特定の分類器の詳細を取得することもできます。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、新規 [`POST /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window} メソッドを使用して、カスタム分類器を作成できます。 カスタム分類器の作成について詳しくは、[カスタム分類器の作成](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)に関する説明を参照してください。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、新規 [`DELETE /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window} メソッドを使用して、カスタム分類器を削除することもできます。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、`version` パラメーターが必要です。 使用するバージョンの API のリリース日を `MM-DD-YYYY` 形式で指定します。
