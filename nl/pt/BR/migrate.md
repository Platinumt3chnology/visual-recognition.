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

# Migrando
{: #migrating}

Para migrar seus modelos atuais (classificadores), provisione uma nova instância do serviço {{site.data.keyword.visualrecognitionshort}}. Para modelos customizados, treine novamente o modelo criando outro modelo (classificador) com as imagens do modelo anterior.
{: shortdesc}

As instâncias de serviço do {{site.data.keyword.visualrecognitionfull}} criadas **antes** de 23 de maio de 2018 têm uma URL de host de `gateway-a.watsonplatform.net`. Deve-se migrar essas instâncias para uma nova instância de serviço do {{site.data.keyword.visualrecognitionshort}} para continuar a usá-las.
{: deprecated}

1.  Crie outra instância do serviço  {{site.data.keyword.visualrecognitionshort}} :
    1.  Acesse a página [{{site.data.keyword.visualrecognitionshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/visual-recognition){: new_window} no catálogo.
    1.  Selecione um plano e clique em  ** Criar **.
1.  Copie as novas credenciais para autenticação em sua instância de serviço:
    1.  Na página **Gerenciar**, clique em **Mostrar credenciais**.
    1.  Copie o valor da  ` Chave API ` .
1.  [Recrie e treine seus modelos customizados](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) em sua nova instância do serviço {{site.data.keyword.visualrecognitionshort}}.
1.  Modifique como você chama seu serviço.

    Forneça uma chave do Identity and Access Management (IAM) ou o token de acesso para sua instância de serviço. Os tokens fornecem maior segurança porque devem ser renovados periodicamente e suportam solicitações sem suas credenciais de serviço incorporadas em cada chamada. As chaves de API usam autenticação básica e não expiram.

    - Para obter mais informações sobre tokens, consulte [Autenticando com tokens do IAM](/docs/services/watson?topic=watson-iam#iam).
    - Para obter mais informações sobre como usar uma chave de API do IAM, consulte a [Referência de API](https://{DomainName}/apidocs/visual-recognition/#authentication).
