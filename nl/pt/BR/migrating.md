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

# Migrando para o {{site.data.keyword.visualrecognitionshort}} do {{site.data.keyword.alchemyvisionshort}}

Em 19 de maio de 2016, o serviço {{site.data.keyword.alchemyvisionshort}} foi descontinuado e sua funcionalidade tornou-se parte do {{site.data.keyword.visualrecognitionshort}} (GA). Para migrar um aplicativo implementado no {{site.data.keyword.Bluemix_notm}} do serviço {{site.data.keyword.alchemyvisionshort}} para o serviço {{site.data.keyword.visualrecognitionshort}}, atualize seu código.
{: shortdesc}

As diferenças a seguir entre o {{site.data.keyword.alchemyvisionshort}} e o {{site.data.keyword.visualrecognitionshort}} podem afetar seu código do aplicativo:

- **Classes e classificadores:** no {{site.data.keyword.alchemyvisionshort}}, as imagens analisadas eram rotuladas com "tags". No {{site.data.keyword.visualrecognitionshort}}, as "tags" são chamadas de "classes". Os grupos de classes são chamados de "classificadores". Todas as tags padrão do {{site.data.keyword.alchemyvisionshort}} ainda estão disponíveis como classes no {{site.data.keyword.visualrecognitionshort}}.
- **Classificadores customizados:** o {{site.data.keyword.visualrecognitionshort}} permite treinar e criar classificadores e classes customizadas.
- **Entrada de lote:** no {{site.data.keyword.visualrecognitionshort}}, agora é possível classificar lotes de imagens ou URLs de imagens enviando arquivos de imagem em um arquivo compactado (.zip) ou uma única URL de imagem em uma sequência JSON.
- **Especificar linguagem:** no {{site.data.keyword.alchemyvisionshort}}, você especificou a linguagem de uma chamada de identificação como um parâmetro de consulta. No {{site.data.keyword.visualrecognitionshort}}, você especifica a linguagem de uma chamada de classificação no cabeçalho `Accept-Language`.
- **Terminais:** a funcionalidade do {{site.data.keyword.alchemyvisionshort}} a seguir é incluída em novos terminais na liberação GA do {{site.data.keyword.visualrecognitionshort}}:

| Funcionalidade | Terminal do {{site.data.keyword.alchemyvisionshort}} (descontinuado) | Terminal do {{site.data.keyword.visualrecognitionshort}} (GA) |
|---------------|--------------------|----------------|
| Identificar imagens com classificadores integrados | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| Detectar faces, faixa de idade e sexo | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| Extrair a imagem principal de HTML ou uma URL de website | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | É possível fornecer uma imagem de URL para os métodos `/v3/classify` e `/v3/detect_faces`, não por meio de um terminal independente. |
