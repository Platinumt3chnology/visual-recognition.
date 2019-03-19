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

# Migration
{: #migrating}

Pour faire migrer vos modèles en cours (discriminants), indiquez une nouvelle instance du service {{site.data.keyword.visualrecognitionshort}}. Pour les modèles personnalisés, recyclez le modèle en créant un autre modèle (discriminant) avec les images de l'ancien modèle.
{: shortdesc}

Les instances de service {{site.data.keyword.visualrecognitionfull}} créées **avant** le 23 mai 2018 possèdent l'URL hôte `gateway-a.watsonplatform.net`. Vous devez faire migrer ces instances vers une nouvelle instance de service {{site.data.keyword.visualrecognitionshort}} pour pouvoir continuer à les utiliser.
{: deprecated}

1.  Créez une autre instance du service {{site.data.keyword.visualrecognitionshort}} :
    1.  Accédez à la page [{{site.data.keyword.visualrecognitionshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/visual-recognition){: new_window} du catalogue.
    1.  Sélectionnez un plan et cliquez sur **Créer**.
1.  Copiez les nouvelles données d'identification pour vous authentifier auprès de votre instance de service : 
    1.  Sur la page **Gérer**, cliquez sur **Afficher les données d'identification**.
    1.  Copiez la valeur de la `clé d'API`. 
1.  [Recréez et entraînez vos modèles personnalisés](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) dans votre nouvelle instance du service {{site.data.keyword.visualrecognitionshort}}. 
1.  Modifiez votre façon d'appeler votre service.

    Vous pouvez fournir une clé IAM (Identity and Access Management) ou un jeton d'accès pour votre instance de service. Les jetons offrent une meilleure sécurité car ils doivent être périodiquement renouvelés et prennent en charge les demandes sans que vous imbriquiez les données d'identification du service dans chaque appel. Les clés d'API utilisent l'authentification de base et n'expirent jamais.

    - Pour plus d'informations sur les jetons, voir [Authentification à l'aide de jetons IAM](/docs/services/watson?topic=watson-iam#iam).
    - Pour plus d'informations sur l'utilisation d'une clé d'API IAM, voir la [référence d'API](https://{DomainName}/apidocs/visual-recognition/#authentication).
