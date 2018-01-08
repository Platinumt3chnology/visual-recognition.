---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# {{site.data.keyword.alchemyvisionshort}} から {{site.data.keyword.visualrecognitionshort}} へのマイグレーション

2016 年 5 月 19 日現在で、{{site.data.keyword.alchemyvisionshort}} サービスは非推奨となり、その機能は {{site.data.keyword.visualrecognitionshort}} (GA) の一部になりました。{{site.data.keyword.Bluemix_notm}} 上にデプロイされたアプリケーションを {{site.data.keyword.alchemyvisionshort}} サービスから {{site.data.keyword.visualrecognitionshort}} サービスにマイグレーションするには、コードを更新します。
{: shortdesc}

{{site.data.keyword.alchemyvisionshort}} と {{site.data.keyword.visualrecognitionshort}} の間の以下の差異は、アプリケーション・コードに影響を与える可能性があります。

- **クラスと分類器:** {{site.data.keyword.alchemyvisionshort}} では、分析された画像は「タグ」でラベル付けされていました。{{site.data.keyword.visualrecognitionshort}} では、「タグ」は「クラス」と呼ばれます。クラスのグループは「分類器」と呼ばれます。{{site.data.keyword.alchemyvisionshort}} からのデフォルト・タグはすべて、{{site.data.keyword.visualrecognitionshort}} でクラスとして引き続き使用できます。
- **カスタム分類器:** {{site.data.keyword.visualrecognitionshort}} では、カスタム分類器およびクラスをトレーニングして作成できます。
- **バッチ入力:** {{site.data.keyword.visualrecognitionshort}} では、複数の画像または画像 URL のバッチは、画像ファイルを圧縮 (.zip) ファイルで送信することで、また、単一画像 URL は JSON ストリングで送信することで、分類できるようになりました。
- **言語の指定:** {{site.data.keyword.alchemyvisionshort}} では、タグ付け呼び出しの言語を照会パラメーターとして指定していました。{{site.data.keyword.visualrecognitionshort}} では、分類呼び出しの言語を `Accept-Language` ヘッダーで指定します。
- **エンドポイント:** 以下の {{site.data.keyword.alchemyvisionshort}} 機能は、{{site.data.keyword.visualrecognitionshort}} の GA リリースに新規エンドポイントとして含まれています。

| 機能 | {{site.data.keyword.alchemyvisionshort}} エンドポイント (非推奨) | {{site.data.keyword.visualrecognitionshort}} エンドポイント (GA) |
|---------------|--------------------|----------------|
| 組み込み分類器による画像のタグ付け | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| 顔、年齢層、および性別の検出 | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| HTML または Web サイト URL からのメイン画像の抽出 | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | 独立したエンドポイントを介さずに、URL で画像を `/v3/classify` メソッドおよび `/v3/detect_faces` メソッドに提供できます。|
