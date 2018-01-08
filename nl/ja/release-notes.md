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

# リリース情報

本サービスに対する以下の新機能および変更点があります。
{: shortdesc}

## ベータ機能
{: #beta}

{{site.data.keyword.IBM_notm}} は、お客様の評価を得るために、ベータとして分類されるサービス、機能、および言語サポートをリリースしています。これらの機能は、不安定であったり、頻繁に変更される可能性があったり、短い通知期間で中止されたりする可能性があります。また、ベータ機能は、一般出荷可能機能と同レベルのパフォーマンスや互換性を提供しない可能性もあり、実稼働環境での使用を意図したものではありません。ベータ機能は、[developerWorks Answers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} でのみサポートされます。

## 変更内容
{: #changelog}

本サービスに対する以下の新機能および変更点があります。


### 2017 年 12 月 11 日
{: #11december2017}

<ul>
  <li>
    <strong>一般モデルでの正確度と出力の向上</strong>
      <p>
        一般モデル (数千のタグが含まれて組み込まれている) は、より 2 次的な対象を検出するようになり、情景の検出が改善されました。こうした改善は、画像のあまり目立たない側面を認識するのに役立ちます。さらに、画像ごとに返されるタグの平均数が 10 に増えました。
      </p>
      <p>
        以下の画像は、更新前に返されたタグと、現在返される追加タグの例を示しています。</p>
      <img src="images/antarctica-iceberg.jpg" alt="南極大陸の氷山">
      <table>
        <tr>
          <th>元のタグ</th>
          <th>追加タグ</th>
        </tr>
        <tr>
          <td>
          タグ: 氷山<br/>
          スコア: 0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          タグ: 氷塊<br/>
          スコア: 0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          タグ: 自然<br/>
          スコア: 0.770</td>
        </tr>
        <tr>
          <td>
          タグ: 水色<br/>
          スコア: 0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          タグ: 黄灰色<br/>
          スコア: 0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>新規の Explicit モデルをベータ版で提供</strong> <p>
        Explicit モデル (ベータ版で開始) は、画像にわいせつなコンテンツが含まれていて、一般用として不適切なものであるかどうかを分類するものです。Explicit モデルを他のモデルと一緒に含めて、組み合わせて分析を行うことができます。例えば、`default` 分類器 ID と `explicit` 分類器 ID の両方を要求に含めて、画像タグと、画像に不適切な表現のコンテンツが含まれているかどうかを返すようにします。<p>
        API 呼び出しについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image) の**「画像分類 (Classify images)」**のメソッドを参照するか、[API explorer  ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify) でモデルを試してみてください。
      </p>
    </li>
    <li>
      <strong>より大きいファイル・サイズのサポート</strong> <p>
        <strong>「画像分類 (Classify images)」</strong>のメソッドは、10 MB までの画像ファイルおよび 100 MB までの .zip ファイルをサポートするようになりました。 </li>
    <li>
      <strong>分類器 ID の引き渡し時に配列が必要</strong>
      <p>
        API では、**「画像分類 (Classify images)」**のメソッドで**「パラメーター (parameters)」**オブジェクトの一部として `classifier_ids` を渡す際に、配列を適用するようになりました。以前は、分類器 ID をストリングとして渡すことができました。詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image) のパラメーターの説明およびサンプル・ファイルを参照してください。
      </p>
    </li>
</ul>

### 2017 年 9 月 8 日
{: #8september2017}

- **ベータ版の Similarity Search およびコレクションは終了しました**: 2017 年 9 月 8 日現在、 Similarity Search のベータ期間は終了しています。詳しくは、[Visual Recognition API – Similarity Search Update ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window} を参照してください。

### 2017 年 6 月 30 日
{: #30june2017}

- **タグ付けの改善**: デフォルト分類器のトレーニング画像の数を増やしました。これにより、画像の全体的な「情景」を正確に認識できるようになります。詳しくは、[Further Enhancements for General Tagging Feature ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window} を参照してください。
- **追加言語**: **「画像分類 (Classify images)」**のメソッドでは、英語、アラビア語、スペイン語、日本語に加えて、韓国語、イタリア語、およびドイツ語をサポートするようになりました。

    API 呼び出しについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}外部リンク・アイコンの**「画像分類 (Classify an image)」**メソッドを参照してください。

### 2017 年 5 月 16 日
{: #16may2017}

- **新しい食品分類器が使用可能: ベータ**

    新しいベータ食品認識モデルは、食品の画像の特異性および正確度の向上を実現します。**「画像分類 (Classify an image)」**メソッドでは、この新しい分類器「food」を `classifier_ids` パラメーターに追加できます。

### 2017 年 4 月 5 日
{: #5april2017}

- **新規 {{site.data.keyword.visualrecognitionshort}} ツールが使用可能: ベータ**

    新しいベータ機能である {{site.data.keyword.visualrecognitionshort}} ツールが [https://watson-visual-recognition.ng.bluemix.net/ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} で利用可能です。このツールを使用すると、{{site.data.keyword.visualrecognitionshort}} サービスをより簡単に操作できるようになります。{{{site.data.keyword.cloud_notm}} API キーを入力することで、GUI を使用して「全般的タグ付け」機能や「顔検出」機能にアクセスできるだけでなく、API キーに関連付けられたカスタム分類器の作成、リトレーニング、 および削除をシームレスに実行することができ、コーディングの必要がありません。

### 2017 年 3 月 8 日
{: #8march2017}

- **一般分類器タグ付けの言語サポートの更新**

    一般分類器は、サポートされるすべての言語でタグを返すようになりました。

- **既知の問題**

    **修正 04-13-2017**: トレーニングまたはリトレーニング中に、状況を確認するために繰り返し `GET /classifiers` を呼び出した結果、トレーニング・ジョブが強制終了されることがあります。この問題の回避策として、`GET /classifiers/{classifier_id}` を使用して新規分類器の状況をポーリングします。つまり、この問題を引き起こす可能性がある、すべての分類器を取得する `GET /classifiers` ではなく、単一分類器 ID 用の分類器 `GET` を使用します。`GET /classifiers/{classifier_id}` は、より高速でもあります。

### 2016 年 12 月 15 日
{: #15december2016}

- **一般分類器タグ付けの改善**

    - 一般分類器のディープ・ラーニング・アルゴリズムが更新されました。すべての言語のタグの品質が大きく改善され、サービスが返す英語のタグの量が大幅に増えました。ユーザー独自のカスタム分類器を作成する場合も、高品質のタグ出力が得られます。
    - カラーのタグ付けが追加されました。サービスは、画像内の上位 1 つまたは 2 つのカラーを返すようになりました。

- **既知の問題**

    - EXIF メタデータ・タグを使用してデモに送信される画像は、サービスに対して方向 (横長と縦長) を正しく指定しません。iPhone でアップロードされた画像には、EXIF メタデータ・タグが含まれていることがあります。この問題の回避策は、画像メタデータを更新して、EXIF メタデータ・タグに依存しないで画像の方向を指定するようにすることです。多くの場合、コンピューターで画像を開き、それを保存するだけで、これを達成できます。例えば、Mac では、画像をプレビューで開き、その画像を保存すると、正しい方向のタグが設定されます。
    - {{site.data.keyword.visualrecognitionshort}} サービスに画像を送信する際に、[EXIF タグ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://en.wikipedia.org/wiki/Exif){: new_window} 値を 8、3、または 6 に指定すると、待ち時間が増えることがあります。サービスは、画像のピクセルをエンコードされた視点に回転させます。画像を事前に回転させるか、あるいは {{site.data.keyword.visualrecognitionshort}} タスクにとって重要でない場合は EXIF ヘッダーを削除すると、時間を節約できます。

### 2016 年 12 月 1 日
{: #1december2016}

- **新しい料金**

    IBM は、{{site.data.keyword.visualrecognitionshort}} サービス上のカスタム分類器の料金を引き下げ、無料プランで利用できる内容を増やしました。詳しくは、[{{site.data.keyword.visualrecognitionshort}} Pricing ページ](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)を参照してください。

### 2016 年 10 月 7 日
{: #7october2016}

- **顔検出の機能拡張**

    本サービスは、`GET` メソッドおよび `POST /v3/detect_faces` メソッドの応答を改善する、新しい顔検出アルゴリズムを採用しています。本サービスでは、信頼度の低い、年齢、名前、および性別の顔検出のフィルター処理を調整しました。その結果、より多くの顔が検出され、より広範囲の信頼度が返されるようになりました。

### 2016 年 9 月 8 日
{: #8september2016}

- **Similarity Search BETA**

    ユーザーは独自に収集した画像をアップロードし、1 つの画像を使用して、その類似した画像の集合を検索できるようになりました。この場合、サービスは上位 100 件の最も類似した画像を返します。類似性の検索はどのような目的にも使用できます。ユーザーは、それぞれ最大 100 万件の画像の集合に対して本サービスをカスタム・トレーニングできます。新規の類似性検索機能について詳しくは、[チュートリアル](/docs/services/visual-recognition/tutorial-collections.html)、および [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} のページを参照してください。

- **テキスト認識はクローズド・ベータになる**

    `POST` メソッドと `GET /v3/recognize_text` メソッドは、クローズド・ベータに戻りました。IBM は、このサービスを使用する BETA のお客様のサポートを継続する意向ですが、現在のところ、再びオープン・ベータについての計画はありません。

### 2016 年 8 月 1 日

- **導入価格の終了**

    カスタム分類器のトレーニングおよびリトレーニング、カスタム画像分類、およびカスタム分類器保管は、無料ではなくなりました。料金については、{{site.data.keyword.visualrecognitionshort}} サービスの [pricing ページ](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)を参照してください。

### 2016 年 7 月 5 日
{: #5july2016}

- **カスタム分類器の更新**

    カスタム分類器は、一定のトレーニング・データ・セットに制限されなくなりました。ユーザーは、新規画像を使用して既存の分類器を更新したり、正例または負例の分類器を既存のトレーニング済み分類器に追加したりできます。Watson が学習するための追加のサンプル画像を提供することにより、サービスはユーザーの分類器をより正確なものにできます。カスタム分類器は、長い時間をかけて学習することが可能になり、可視情報の理解が継続的に向上します。

- **既知の問題**

    **修正 04-13-2017**: ユーザーは、既存の分類器を更新した 30 秒後または 90 秒後に 500 エラー・コードを受け取ることがあります。エラーにもかかわらず、リトレーニング要求は正常に完了する可能性が十分あります。少なくとも 2 分間待ってから、`GET classifiers/{classifier\_id}` メソッドを使用して、分類器の状況を確認してください。状況が「ready」で、「retrained」タイム・スタンプが更新されていれば、500 コードを生成したリトレーニング要求は正常に実行済みです。あるいは、「retrained」タイム・スタンプが更新されていない場合は、リトレーニングが失敗した理由を示す説明が応答に追加されており、サービスはリトレーニング要求が出される前に存在したバージョンの分類器に戻します。

### 2016 年 5 月 20 日
{: #20 may 2016}

これは、{{site.data.keyword.visualrecognitionshort}} サービスの一般出荷版です。このリリースでは、バージョン 3 のサービスが導入されており、これは互換性を破る重要な変更です。このリリースには、非推奨になった AlchemyVision サービスからの機能が取り込まれています。

サービスがベータ版の間に作成されたカスタム分類器はすべて、サービスの GA インスタンスで再作成する必要があります。

{{site.data.keyword.visualrecognitionshort}} サービスに対して、以下の変更および更新が行われました。

- **バージョンの日付:** このリリースの機能を使用するには、`version` パラメーターの値として `2016-05-20` を使用します。
- **クラスと分類器:** 単一の分類器は「クラス」と呼ばれるようになりました。GA では、クラスのグループを「分類器」と呼びます。
- **分類:** デフォルトのクラスを使用して各種の対象や情景を素早く正確に識別するには、`POST` メソッドまたは `GET /v3/classify` メソッドを使用します。
- **顔検出:** 画像内の顔を検出し、それに関する情報 (顔が画像のどの位置にあるかや、それぞれの顔の推定年齢層や性別など) を取得するには、`POST` メソッドまたは `GET /v3/detect_faces` メソッドを使用します。また、サービスでは、名前によって多くの有名人を特定したり、ナレッジ・グラフを提供して、ユーザーが関心のある集計を行ってより上位の概念に集約できるようにしたりすることもできます。
- **多面的なカスタム分類器:** いくつかのクラスで定義された非常に特化された分類器を作成し、トレーニングできるようになりました。例えば、クラス「new\_cars」と「red\_cars」で定義された「new\_red\_car」分類器を作成できます。多面的な分類器の作成について詳しくは、[トレーニング・データの構造](/docs/services/visual-recognition/customizing.html#structure)を参照してください。
- **非同期トレーニング:** カスタム分類器のトレーニングは、非同期になりました。これにより、カスタム分類器はバックグラウンドで学習を継続しながら、トレーニングの呼び出しを迅速に完了できます。カスタム分類器のトレーニング状況を調べて、使用可能になる時期を確認するには、`GET /v3/classifiers/{classifier_id}` メソッドを呼び出して、`status` 応答パラメーターを確認します。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} サービスの最新リリースでは、新規バージョンの {{site.data.keyword.visualrecognitionshort}} API (v2) が導入され、互換性を破る重要な変更が行われています。{{site.data.keyword.visualrecognitionshort}} サービスのバージョン 1 は、このサービスのベータ版が終了するまで使用可能です。

API のバージョン 2 の使用をすぐに開始するには、以下の変更を理解し、変更を反映させるようにコードを更新します。

- バージョン 1 のサービスでは、ラベルによって画像を分析しました。バージョン 2 のサービスでは、ラベルは**分類器**と呼ばれます。分類器には、`classifier_id` パラメーターで示される固有の分類器 ID と、`name` パラメーターで示される短い名前があります。
- 画像を分析するための `POST /v1/recognize` メソッドは、[`POST /v2/classify` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} メソッドになりました。`labels_to_check` パラメーターは、`classifier_ids` に名前変更されました。
- V1 でラベルのリストを取得するための `GET /v1/tag/labels` メソッドは、分類器のリストを取得するための [`GET /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} メソッドになりました。
- 分類器のリストを取得するのに加えて、新規 [`GET /v2/classifiers/{classifier_id}` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window} メソッドを使用して、特定の分類器の詳細を取得することもできます。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、新規 [`POST /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window} メソッドを使用して、カスタム分類器を作成できます。カスタム分類器の作成について詳しくは、[カスタム分類器の作成](/docs/services/visual-recognition/customizing.html)に関する説明を参照してください。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、新規 [`DELETE /v2/classifiers` ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window} メソッドを使用して、カスタム分類器を削除することもできます。
- ベータ {{site.data.keyword.visualrecognitionshort}} API のバージョン 2 では、`version` パラメーターが必要です。使用するバージョンの API のリリース日を `MM-DD-YYYY` 形式で指定します。
