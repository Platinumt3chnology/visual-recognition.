---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom object detection,object detection,bounding boxes,visual inspection
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

<!-- Link definitions -->

[api-ref-v4]: https://{DomainName}/apidocs/visual-recognition-v4

# Custom Object Detection (Beta)
{: #object-detection-overview}

O Custom Object Detection (Beta) do {{site.data.keyword.visualrecognitionfull}} identifica itens e seus locais em uma imagem. O serviço detecta esses itens com base em um conjunto de imagens com dados de treinamento rotulados fornecidos.
{: shortdesc}

O Custom Object Detection é um recurso beta privado e deve-se ter permissão do {{site.data.keyword.IBM_notm}} para fazer chamadas para o modelo. [Solicitar acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}. Para obter mais informações sobre recursos beta, consulte as [Notas sobre a liberação](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

Você treina o modelo de detecção de objeto para reconhecer objetos que são importantes para seu fluxo de trabalho ou domínio. Por exemplo, detectar danos nos carros, localizar máquinas que precisam de manutenção ou executar inspeções visuais no campo. Também é possível usar a detecção de objeto para contar objetos ou gerenciar o inventário.

## Detecção de objeto e classificação em comparação
{: #obj-detect-comparison}

O modelo Custom Object Detection é o recurso mais recente no serviço {{site.data.keyword.visualrecognitionshort}}, que inclui classificação.

A classificação e a detecção de objeto são semelhantes, mas têm usos diferentes. Em geral, se você desejar prever a existência de objetos em uma imagem, use a classificação. Se desejar localizar ou contar objetos em uma imagem, use a detecção de objeto.

### Classificação
{: #obj-detect-classify}

Quando você classifica uma imagem, o serviço responde com a probabilidade de que determinados objetos estejam nessa imagem. É possível usar os modelos integrados (General, Food ou Explicit) ou criar seu próprio modelo customizado.

Por exemplo, quando você classifica uma imagem de cookies, como a imagem a seguir, o serviço prevê que há cookies na imagem com uma confiança de 95%.

![Imagem de resposta da classificação](images/cookies-tag.png "Uma imagem para mostrar classificação")

### Detecção de objeto
{: #obj-detect-detect}

A detecção de objeto customizado é semelhante à classificação customizada, mas o serviço identifica o local de itens na imagem. Como a classificação, a resposta também inclui o rótulo de cada item detectado e a confiança em sua identificação.

Os itens detectados se baseiam nas informações fornecidas quando se treina um modelo de detecção de objeto.

Na imagem a seguir, o método **Analisar imagens** de Custom Object Detection identifica o local de cookies na imagem. Cada objeto detectado inclui o rótulo (neste caso, `Cookie`) com sua localização e uma pontuação de confiança.

![Imagem de resposta da detecção de objeto](images/cookies-bbox.png "Uma imagem para mostrar a detecção de objeto")

## Como usar o Custom Object Detection
{: #object-detection-sequence}

Para usar o Custom Object Detection do {{site.data.keyword.visualrecognitionshort}}, siga esta sequência de etapas para configurar um modelo de detecção de objeto customizado:

1.  Crie uma coleção: uma coleção é um contêiner para suas imagens e dados de treinamento. Consulte [Criar uma coleção ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window} na Referência de API v4.
1.  Inclua suas imagens na coleção. É possível incluir imagens únicas por URL ou por arquivo ou fazer upload de um arquivo de imagens `.zip`. Consulte [Incluir imagens ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window} na Referência de API v4.
1.  Incluir dados de treinamento em suas imagens. Consulte  [ Preparando seus dados de treinamento ](#object-detection-preparation).
1.  Treine sua coleção. Depois de ter dados de treinamento suficientes, inicie o treinamento nas imagens da coleção. Consulte [Treinar uma coleção ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} na Referência de API v4.

Depois de concluir essas etapas e treinar sua coleção, é possível analisar imagens com relação a ela.

### Preparando seus dados de treinamento
{: #object-detection-preparation}

A parte mais importante do processo de configuração é preparar e montar seus dados de treinamento. Assim como quando você [cria um modelo customizado](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier) para classificar imagens, você monta um conjunto de imagens que representam os objetos que deseja detectar.

Além de um conjunto de imagens, você também fornece dados de treinamento para cada imagem. Para detecção de objeto, dados de treinamento são o conjunto de rótulos e locais para objetos na imagem que você deseja que o {{site.data.keyword.visualrecognitionshort}} reconheça. É possível ter mais de um objeto em uma imagem.

O rótulo identifica o que o objeto é. O local identifica onde ele está na imagem. Você identifica o local desenhando uma _caixa delimitadora_ ao redor do objeto e fornecendo as coordenadas de pixel superior e esquerda dessa caixa, juntamente com a largura e a altura em pixels.

O exemplo a seguir mostra os dados de treinamento para um objeto rotulado `BurntCookie`.

```json
{
  "objects": [{
    "object": "BurntCookie",
    "location": {
      "left": 33,
      "top": 8,
      "width": 163,
      "height": 119
    }
  }]
}
```
{: codeblock}

Nesta liberação beta inicial, você cria as informações de local manualmente ou usando uma ferramenta de anotação de imagem.

Em geral, quanto mais imagens e caixas delimitadoras você fornecer nos dados de treinamento, melhor. Aqui estão algumas diretrizes de dados de treinamento para começar a usar:

- Cada imagem tem pelo menos 500 pixels para a altura e a largura.
- Cada objeto rotulado na coleção tem pelo menos 100 locais (caixas delimitadoras).
- Cada imagem na coleção não tem mais de 10 caixas de delimitação.
- O tamanho de cada caixa delimitadora é maior que 15% das dimensões de imagem.
- A API lê as tags de orientação EXIF em suas imagens. Certifique-se de que as coordenadas `location` correspondam a essa orientação. Para ajustar a orientação, é possível usar uma ferramenta como a ImageMagick para _auto-orientar_ suas imagens antes da inclusão de caixas delimitadoras.

Para obter mais informações sobre o método **Incluir dados de treinamento em uma imagem**, consulte a [Referência de API v4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}.

### Treinar a coleção
{: #object-detection-train}

Depois de incluir os dados de treinamento em imagens em sua coleção, a etapa final de configuração é treinar um modelo de detecção de objeto. Uma única chamada para a API inicia o treinamento e a resposta inclui informações de status. Por exemplo, o status a seguir mostra que o treinamento começou, mas ainda não foi concluído:

```json
"training_status": {
  "objects": {
    "ready": false,
    "in_progress": true,
    "data_changed": false,
    "latest_failed": false,
    "description": "Starting training"
  }
}
```
{: codeblock}

É possível treinar novamente um modelo depois de atualizar os dados de treinamento, emitindo a chamada novamente.

Para obter mais informações, consulte [Treinar uma coleção ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window} na Referência de API v4.

## Analisar imagens
{: #object-detection-analyze}

Depois de configurar um modelo de detecção de objeto customizado e o treinamento estiver completo, será possível detectar objetos em outras imagens. Como com a classificação, você fornece uma imagem ou um arquivo `.zip` de imagens e um **limite** opcional para configurar a pontuação mínima de objetos detectados. Para obter mais informações, consulte o método **Analisar imagens** na [Referência de API v4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images).

## Próximos passos
{: #object-detection-next-steps}

- Familiarize-se com a API na [Referência de API v4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")][api-ref-v4]{: new_window}.
