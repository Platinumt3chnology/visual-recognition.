---

copyright: years: 2015, 2017 lastupdated: "2017-12-11"

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

# Criando um classificador customizado

Depois de classificar uma imagem no "Tutorial de Introdução", você está pronto para treinar e criar um classificador customizado (ou modelo). Com um classificador customizado, é possível treinar o serviço {{site.data.keyword.visualrecognitionshort}} para classificar as imagens para adequar às suas necessidades de negócios.
{: shortdesc}

## Etapa 1: copiar suas credenciais
{: #copy-credentials}

Use as credenciais que você copiou na "Tutorial de Introdução". Se você não criou uma instância de serviço, execute essas etapas na seção [Antes de começar](/docs/services/visual-recognition/getting-started.html#prerequisites).

## Etapa 2: criando um classificador customizado
{: #create}

O {{site.data.keyword.visualrecognitionshort}} pode aprender por meio de imagens de exemplo para criar um novo classificador com diversas máscaras. Cada arquivo de exemplo é treinado com relação a outros arquivos nessa chamada e os exemplos positivos são armazenados como classes. Essas classes são agrupadas para definir um único classificador e retornar suas próprias pontuações. Arquivos de exemplo negativo não são armazenados como classes.

1.  Faça download dos arquivos de treinamento de exemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Chame o método `POST /v3/classifiers` com o comando a seguir, que faz upload dos dados de treinamento e cria um classificador `dogs`:
    - Substitua `{api-key}` pelas credenciais de serviço copiadas na primeira etapa.
    - Modifique o local do `{class}_positive_examples` para apontar para onde você salvou os arquivos .zip.

    ```bash
    curl -X POST \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Nomes de arquivos de exemplo positivo requerem o sufixo `_positive_examples`. Neste exemplo, os nomes de arquivos são `beagle_positive_examples`, `goldenretriever_positive_examples` e `husky_positive_examples`. O prefixo (beagle, goldenretriever e husky) é retornado como o nome da classe.
    {:tip }

    A resposta inclui um novo ID de classificador e status, por exemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "training",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle" }
      ]
    }
    ```
    {: codeblock}

1.  Verifique o status de treinamento periodicamente, até ver um status `ready`. O treinamento começa imediatamente e deve ser concluído antes de ser possível consultar o classificador. Substitua `{api key}` e `{classifier_id}` por suas informações:

    ```bash
    curl -X GET \ "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Etapa 3: atualizando um classificador customizado existente

Não é possível atualizar um classificador customizado com uma chave API grátis. Se você tem uma chave grátis, é possível fazer upgrade para um plano Padrão. Para obter detalhes, veja [Mudando seu plano](https://console.bluemix.net/docs/pricing/changing_plan.html).
{: tip}

É possível atualizar um classificador customizado incluindo classes no classificador ou incluindo imagens em uma classe existente. Aqui, você melhora o classificador que você criou na Etapa 2 incluindo uma classe *Dalmatian* para os tipos de cães que podem ser classificados. Você também inclui imagens de gatos no exemplo negativo configurado para o classificador "dogs".

1.  Faça download dos arquivos de treinamento de amostra <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> e <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Chame o método `POST /v3/classifiers/{classifier_id}` com o comando cURL a seguir, que faz upload dos dados de treinamento e atualiza o classificador "dogs\_1941945966":
    - Substitua `{api-key}` pelas credenciais de serviço copiadas na primeira etapa.
    - Substitua `{classifier_id}` pelo ID do classificador que você deseja atualizar.
    - Modifique o local do `{class}_positive_examples` para apontar para onde você salvou os arquivos .zip.

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    O classificador "dogs" existente é substituído pelo retreinado com o mesmo classifier_id. A resposta lista o novo conjunto de classes e o status atual. Por exemplo:

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "status": "retraining",
      "created": "2016-05-18T21:32:27.752Z",
      "classes": [
        {
          "class": "dalmatian"
        },
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle" }
      ]
    }
    ```
    {: codeblock}

    O treinamento inicia imediatamente. Quando o novo estiver disponível, o status mudará para `ready`.

    Não emita outra solicitação de retreinamento até o estado `ready` do status atual. Múltiplas solicitações para retreinar um classificador resultam em um único retreinamento em vigor. Um registro de data e hora chamado `retrained` mostra a última vez que o retreinamento de classificador foi concluído. Se você chama o método `/classify` enquanto o classificador está em retreinamento, a definição antiga do classificador é usada.
    {: tip}
1.  Verifique o status de treinamento periodicamente, até ver um status `ready`. Substitua `{api key}` e `{classifier_id}` por suas informações:

    ```bash
    curl -X GET \ "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## Etapa 4: classificando uma imagem com um classificador customizado
{: #classify}

Quando o novo classificador estiver pronto, chame-o para ver como ele é executado.

1.  Crie um arquivo JSON denominado `myparams.json` que inclua os parâmetros para sua chamada, como o `classifier_id` para o seu novo classificador e o classificador de modelo Geral (que usa o classifier_id `default`). Um arquivo JSON simples pode ser semelhante a este:

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  Faça download do <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>.
1.  Use o método `POST /v3/classify` para testar seu classificador customizado. O exemplo a seguir classifica a imagem `dogs.jpg` com relação ao classificador "dogs\_1941945966":
    - Substitua `{api-key}` pelas credenciais de serviço copiadas na primeira etapa.

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    Para classificar com relação somente ao modelo Geral integrado, omita o parâmetro `parameters`.
    {: tip}

    A resposta inclui classificadores, suas classes e uma pontuação para cada classe. Amplitude de pontuação de 0 a 1, com uma pontuação mais alta indicando maior correlação. As chamadas `/v3/classify` omitem as classes de baixa pontuação por padrão se as classes de alta pontuação são identificadas. É possível configurar uma pontuação mínima para ser exibida especificando um valor de vírgula flutuante para o parâmetro `threshold` em sua chamada.

    ```json
    {
      "images": [ {
          "classifiers": [ {
              "classes": [ {
                  "class": "animal",
                  "score": 1.0,
                  "type_hierarchy": "/animals"
                },
                {
                  "class": "mammal",
                  "score": 1.0,
                  "type_hierarchy": "/animals/mammal"
                },
                {
                  "class": "dog",
                  "score": 0.880797,
                  "type_hierarchy": "/animals/pets/dog"
                }
              ],
              "classifier_id": "default",
              "name": "default"
            },
            {
              "classes": [ {
                  "class": "goldenretriever",
                  "score": 0.610501
                }
              ],
              "classifier_id": "dogs_1941945966",
              "name": "dogs"
            }
          ],
          "image": "dogs.jpg"
        }
      ], "images_processed": 1 }
    ```
    {: codeblock}

1.  Revise os resultados.

Pronto! Você criou, treinou e consultou um classificador customizado com o {{site.data.keyword.visualrecognitionshort}}.

### Excluindo o classificador customizado

Você pode desejar excluir seu classificador customizado para começar a desenvolver seu aplicativo com uma instância limpa.

Para excluir o classificador, chame o método `DELETE /v3/classifiers/{classifier_id}`. Substitua `{api_key)` e `classifier_id` por suas informações:

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## Próximos passos

Agora que você tem um entendimento básico de como usar classificadores customizados, é possível pesquisar detalhadamente:

- Saiba mais sobre as [Melhores práticas para classificadores customizados![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}.
- Leia a API na [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}.

### Atribuições
{: #attributions}

Todas as imagens usadas nesta página são do Flikr e usadas sob [licença do Creative Commons Attribution 2.0 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window}. Nenhuma mudança foi feita nessas imagens.
