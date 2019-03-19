---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# Segurança de informações
{: #information-security}

A IBM está comprometida em fornecer aos nossos clientes e parceiros soluções inovadoras de privacidade de dados, segurança e governança.
{: shortdesc}

**Aviso:**
os clientes são responsáveis por assegurar sua própria conformidade com várias leis e regulamentações, incluindo o Regulamento Geral sobre a Proteção de Dados da União Europeia. Os clientes são os únicos responsáveis por obter aconselhamento de consultoria jurídica competente quanto à identificação e interpretação de quaisquer leis e regulamentos relevantes que possam afetar os negócios dos clientes e quaisquer ações que os clientes possam precisar tomar para cumprir tais leis e regulamentações.

Os produtos, serviços e outros recursos descritos aqui não são adequados para todas as situações do cliente e podem ter disponibilidade restrita. A IBM não fornece aviso jurídico, contábil ou de auditoria nem representa ou garante que os seus serviços ou produtos assegurarão que os clientes estejam em conformidade com qualquer lei ou regulamentação.
Se você precisar solicitar suporte do GDPR para os recursos do {{site.data.keyword.cloud}} {{site.data.keyword.watson}} que forem criados

- Na União Europeia, consulte [Solicitando suporte para recursos do IBM Cloud Watson criados na União Europeia](/docs/services/watson?topic=watson-gdpr-sar#request-EU).
- Fora da União Europeia, consulte [Solicitando suporte para recursos fora da União Europeia](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU).

## Regulamento Geral sobre a Proteção de Dados (GDPR) da União Europeia
{: #gdpr}

A IBM está comprometida em fornecer aos nossos clientes e parceiros soluções inovadoras de privacidade de dados, segurança e controle para auxiliá-los em sua jornada para a conformidade com GDPR.

Saiba mais sobre a própria jornada de prontidão GDPR da IBM e nossas capacidades e ofertas de GDPR para suportar sua jornada de conformidade [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/gdpr){: new_window}.

## Rotulando e excluindo dados no  {{site.data.keyword.visualrecognitionshort}}
{: #gdpr-visrec}

### Migração de Segurança GDPR
{: #gdpr-visrec-update}

- Todas as instâncias de serviço do {{site.data.keyword.visualrecognitionfull}} criadas antes de **22 de maio de 2018** não são adequadas para clientes que requerem conformidade com o Regulamento Geral sobre a Proteção de Dados da UE 2016/679 (GDPR).
- Os clientes sujeitos ao GDPR precisam [migrar para uma nova instância de serviço do {{site.data.keyword.visualrecognitionshort}}](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) disponível em **22 de maio de 2018** e adotar o novo contrato para o serviço {{site.data.keyword.visualrecognitionshort}}.
- Os clientes precisam provisionar um novo serviço {{site.data.keyword.visualrecognitionshort}} e gerar *novas chaves de autenticação* para utilizar o novo serviço {{site.data.keyword.visualrecognitionshort}}.
- Se um cliente não provisionar o novo serviço {{site.data.keyword.visualrecognitionshort}}, você confirmará que a IBM não está processando nenhum Dado pessoal no nome do cliente que está sujeito ao GDPR.
- Clientes que não forem para o novo serviço {{site.data.keyword.visualrecognitionshort}} entre 22 de maio de 2018 e 1º de outubro de 2018 terão seus dados excluídos.

### Rotulando dados

Se for necessário remover dados de um cliente individual de uma instância de serviço do {{site.data.keyword.visualrecognitionshort}} com vários clientes, primeiro será necessário associar esses dados a um ID de cliente exclusivo de cada indivíduo que possa ter fornecido dados.

Para especificar o ID do cliente de quaisquer dados enviados com o método **Criar um classificador**, inclua a propriedade **X-Watson-Metadata: customer_id** no cabeçalho da solicitação. O exemplo a seguir associa o ID de cliente `my_ID` a uma solicitação:

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

Caracteres de multibyte são suportados para a sequência de ID do cliente. Os caracteres devem ser codificados por URL, tanto no cabeçalho durante o treinamento, quanto no parâmetro de consulta durante a exclusão. O ID pode conter caracteres alfanuméricos e sublinhados (``_``). Estes caracteres não são suportados: ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & =% # ^ @:. , + espaço ``.

Você é responsável por criar valores de ID do cliente e assegurar que cada um seja exclusivo.
{: important}

### Excluindo dados rotulados

Para excluir todos os dados associados a um ID do cliente, use o método **Excluir dados rotulados**. Você passa a sequência `customer_id={id}` como um parâmetro de consulta com a solicitação. O exemplo a seguir exclui todos os dados do ID do cliente `my_ID`:

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

O método **Excluir dados rotulados** exclui todos os dados associados ao ID de cliente especificado, independentemente do método pelo qual as informações foram incluídas. O método não terá efeito se nenhum dado estiver associado ao ID do cliente.

As solicitações de exclusão são processadas em lotes e podem levar até 24 horas para serem concluídas.
{: tip}

### Suporte
{: #gdpr-visrec-support}

Direcione perguntas para seu representante de conta ou entre em contato com o suporte diretamente em [https://ibm.biz/ibmcloudsupport ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/ibmcloudsupport){: new_window}.
