---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# Criando um modelo customizado
{: #tutorial-custom-classifier}

Depois de analisar uma imagem no "Tutorial de introdução", você está pronto para treinar e criar um modelo customizado. Com um modelo customizado, é possível treinar o serviço {{site.data.keyword.visualrecognitionshort}} para classificar imagens para adequar às suas necessidades de negócios.
{: shortdesc}

## Etapa 1: copiar suas credenciais
{: #copy-credentials}

Use as credenciais que você copiou na "Tutorial de Introdução". Se você não criou uma instância de serviço, execute essas etapas na seção [Antes de começar](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites).

## Etapa 2: Criando um modelo customizado
{: #create}

O {{site.data.keyword.visualrecognitionshort}} pode aprender com imagens de exemplo das quais você faz upload para criar um novo modelo multifacetado. Cada arquivo de exemplo é treinado com relação a outros arquivos nessa chamada e os exemplos positivos são armazenados como classes. Essas classes são agrupadas para definir um único modelo e retornar suas próprias pontuações. Arquivos de exemplo negativo não são armazenados como classes.

1.  Faça download dos arquivos de treinamento de exemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>.
1.  Chame o método `POST /v3/classifiers` com o comando a seguir, que faz upload dos dados de treinamento e cria um modelo customizado `dogs`:
    - Substitua `{your_api_key}` pelas credenciais de serviço que você copiou na primeira etapa.
    - Modifique o local do `{class}_positive_examples` para apontar para onde você salvou os arquivos .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    Nomes de arquivos de exemplo positivo requerem o sufixo `_positive_examples`. Neste exemplo, os nomes de arquivos são `beagle_positive_examples`, `goldenretriever_positive_examples` e `husky_positive_examples`. O prefixo (beagle, goldenretriever e husky) é retornado como o nome da classe.
    {:tip }

    A resposta inclui um novo ID de classificador e status, por exemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle" }
      ], "core_ml_enabled": true }
    ```
    {: codeblock}

1.  Verifique o status de treinamento periodicamente, até ver um status `ready`. O treinamento começa imediatamente e deve ser concluído antes que você possa consultar o modelo. Substitua `{your_api_key}` e `{classifier_id}` pelas suas informações:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \ "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{2}{0}{1}{8}-03-19"
    ```
    {: pre}

## Etapa 3: Atualizando um modelo customizado existente
{: #tutorial-custom-classifier-update}

É possível atualizar um modelo customizado incluindo classes nele ou incluindo imagens em uma classe existente. Aqui, você melhora o modelo criado na Etapa 2, incluindo uma classe *Dálmata* para os tipos de cães que podem ser classificados. Você também inclui imagens de gatos no exemplo negativo configurado para o modelo customizado "dogs".

1.  Faça download dos arquivos de treinamento de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>.
1.  Chame o método `POST /v3/classifiers/{classifier_id}` com o comando cURL a seguir, que faz upload dos dados de treinamento e atualiza o modelo customizado "dogs\_1941945966":
    - Substitua `{your_api_key}` pelas credenciais de serviço que você copiou na primeira etapa.
    - Substitua `{classifier_id}` pelo ID do modelo customizado que você deseja atualizar.
    - Modifique o local do `{class}_positive_examples` para apontar para onde você salvou os arquivos .zip.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{2}{0}{1}{8}-03-19"
    ```
    {: pre}

    O modelo customizado "dogs" existente é substituído pelo que passou pelo novo treinamento com o mesmo classifier_id. A resposta lista o novo conjunto de classes e o status atual. Por exemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ], "core_ml_enabled": true }
    ```
    {: codeblock}

    O treinamento inicia imediatamente. Quando o novo estiver disponível, o status mudará para `ready`.

    Não emita outra solicitação de retreinamento até o estado `ready` do status atual. Múltiplas solicitações para treinar novamente um modelo resultam na efetivação de um único novo treinamento. Um registro de data e hora chamado `updated` mostra o horário em que o modelo foi atualizado mais recentemente. Se você chamar o método `/classify` enquanto o modelo estiver sendo treinado novamente, a definição antiga do modelo será usada.
    {: tip}
1.  Verifique o status de treinamento periodicamente, até ver um status `ready`. Substitua `{your_api_key}` e `{classifier_id}` pelas suas informações:

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \ "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{2}{0}{1}{8}-03-19"
    ```
    {: pre}

## Etapa 4: Classificando uma imagem com um modelo customizado
{: #tutorial-custom-classifier-classify}

Quando o novo modelo estiver pronto, chame-o para ver como ele é executado.

1.  Faça download do <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>.
1.  Use o método `POST /v3/classify` para testar seu modelo customizado. O exemplo a seguir classifica a imagem `dogs.jpg` com relação ao modelo customizado "dogs\_1941945966" e ao modelo General integrado `default`:
    - Substitua `{your_api_key}` pelas credenciais de serviço que você copiou na primeira etapa.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    Para classificar com relação apenas ao modelo General integrado, omita o parâmetro `classifier_ids`.
    {: tip}

    A resposta inclui classificadores (modelos), suas classes e uma pontuação para cada uma. Amplitude de pontuação de 0 a 1, com uma pontuação mais alta indicando maior correlação. As chamadas `/v3/classify` omitem as classes de baixa pontuação por padrão se as classes de alta pontuação são identificadas. É possível configurar uma pontuação mínima para ser exibida especificando um valor de vírgula flutuante para o parâmetro `threshold` em sua chamada.

    ```json
    {
      "images": [ {
          "classifiers": [ {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  Revise os resultados.

Pronto! Você criou, treinou e consultou um modelo customizado com o {{site.data.keyword.visualrecognitionshort}}.

### Excluindo seu modelo customizado
{: #tutorial-custom-classifier-delete}

Talvez você queira excluir seu modelo customizado para começar a desenvolver seu aplicativo com uma instância limpa.

Para excluir o modelo, chame o método `DELETE /v3/classifiers/{classifier_id}`. Substitua `{your_api_key)` e `classifier_id` por suas informações:

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{2}{0}{1}{8}-03-19"
```
{: pre}

## Próximos passos
{: #tutorial-custom-classifier-next-steps}

Agora que você tem um entendimento básico de como usar modelos customizados, é possível ir mais fundo:

- Saiba mais sobre as [Melhores práticas para classificadores customizados![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### Atribuições
{: #tutorial-custom-classifier-attributions}

Todas as imagens usadas nesta página são do Flikr e usadas sob [licença do Creative Commons Attribution 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessas imagens.
