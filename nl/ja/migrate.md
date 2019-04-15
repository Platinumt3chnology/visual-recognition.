---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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

# マイグレーション
{: #migrating}

現在のモデル (分類器) をマイグレーションするには、{{site.data.keyword.visualrecognitionshort}} サービスの新しいインスタンスをプロビジョンします。カスタム・モデルの場合、以前のモデルのイメージを使って別のモデル (分類器) を作成することで、モデルをリトレーニングします。
{: shortdesc}

2018 年 5 月 23 日より**前に**作成した {{site.data.keyword.visualrecognitionfull}} サービス・インスタンスは、ホスト URL が `gateway-a.watsonplatform.net` になっています。これらのインスタンスを引き続き使用するには、新しい {{site.data.keyword.visualrecognitionshort}} サービス・インスタンスにマイグレーションする必要があります。
{: deprecated}

1.  {{site.data.keyword.visualrecognitionshort}} サービスの別のインスタンスを次のように作成します。
    1.  カタログの [{{site.data.keyword.visualrecognitionshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/visual-recognition){: new_window} ページに移動します。
    1.  プランを選択して、**「作成」**をクリックします。
1.  サービス・インスタンスに認証するための新しい資格情報をコピーします。
    1.  **「管理」**ページで、**「資格情報の表示」**をクリックします。
    1.  `「API キー」`の値をコピーします。
1.  {{site.data.keyword.visualrecognitionshort}} サービスの新しいインスタンスで、[カスタム・モデルの再作成とトレーニング](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)を行います。
1.  サービスの呼び出し方法を変更します。

    サービス・インスタンスの ID とアクセス管理 (IAM) キー、またはアクセス・トークンを指定します。トークンを使用するほうがセキュリティーは向上します。トークンは定期的に更新が必要で、すべての呼び出しで、サービス資格情報を組み込まない要求もサポートするためです。API キーは基本認証を行い、有効期限はありません。

    - トークンについて詳しくは、[IAM トークンによる認証](/docs/services/watson?topic=watson-iam#iam)を参照してください。
    - IAM API キーの使用について詳しくは、[API リファレンス](https://{DomainName}/apidocs/visual-recognition/#authentication)を参照してください。
