---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-30"

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

# Sobre classificadores

Quando você classifica uma imagem, o Visual Recognition retorna um conjunto de classes localizadas na imagem. Ele deriva essas informações das imagens em elas são treinadas. Um classificador é um grupo de classes.

O Visual Recognition inclui vários classificadores integrados que podem fornecer resultados altamente precisos sem a necessidade de executar o treinamento. Também é possível treinar os classificadores customizados para criar classes especializadas.

Introdução ao Clarifai
> O tipo de predição é baseado em qual modelo você executa a entrada. Por exemplo, se você executar sua entrada por meio do modelo 'food', as predições retornadas conterão conceitos que o modelo 'food' conhece. Se você executar sua entrada por meio do modelo 'color', ela retornará predições sobre as cores dominantes em sua imagem.

Clarifai
> O Clarifai fornece muitos modelos diferentes que 'veem' o mundo de forma diferente. Um modelo contém um grupo de conceitos. Um modelo verá somente os conceitos que ele contém.
>
> Há momentos em que se deseja ter um modelo que vê o mundo da maneira como você vê. A API permite fazer isso. É possível criar seu próprio modelo e treiná-lo com suas próprias imagens e conceitos. Depois de treiná-lo para ver como você gostaria que ele visse, é possível então usar esse modelo para fazer predições.

## Classificadores integrados

O Visual Recognition inclui um conjunto de classificadores que fornece resultados altamente precisos sem treinamento. Os classificadores integrados atuais são denominados `default`, `food` e `explicit`.

### Classificador padrão

O classificador padrão retorna classes de milhares de tags possíveis organizadas em categorias e subcategorias. As categorias de nível superior a seguir podem ser retornadas:

- Animais (incluindo pássaros, répteis, anfíbios, etc.)
- Atividades e informações orientadas para pessoa(s)
- Comida (incluindo comida cozida e bebidas)
- Plantas (incluindo árvores, arbustos, plantas aquáticas, vegetais)
- Esportes
- Natureza (incluindo muitos tipos de formações naturais, estruturas geológicas)
- Transporte (por terra, água, ar)
- E muitos outros, incluindo móveis, frutas, instrumentos musicais, ferramentas, cores, gadgets, dispositivos, instrumentos, armas, prédios, estruturas e objetos feitos pelo homem, roupas e acessórios, e flores, entre outros.

### Classificador de alimento

Embora o classificador padrão possa identificar alimentos e bebidas, é possível especificar o classificador `food` integrado para...

### Classificador explícito

O Visual Recognition pode classificar se uma imagem é inadequada para uso geral. O classificador `explicit` identifica atualmente o que pode ser considerado imagens pornográficas. Uma abreviação comum para essa classificação é chamada _NSFW_, significando _não seguro para o trabalho_.

Uma pontuação acima ou abaixo de um determinado número não é uma garantia de que a imagem é explícita ou não. No entanto, é possível usar a resposta como um filtro inicial de uma imagem e fazer mais análises desse ponto.

Resposta:
```json
{
  "images": [ {
      "classifiers": [ {
          "classes": [ {
              "class": "not explicit",
              "score": 0.704
            }
          ],
          "classifier_id": "explicit",
          "name": "explicit"
        }
      ],
      "resolved_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png",
      "source_url": "https://images-na.ssl-images-amazon.com/images/I/C1XxZKbHSrS._SL1000_.png"
    }
  ], "images_processed": 1 }
```
{: codeblock}

## Combinando classificadores


## Hierarquia de classes na resposta

O método `/v3/classify` classifica imagens em uma hierarquia de classes relacionadas. Por exemplo, uma imagem de um Beagle pode ser classificada como "animal" ou como os itens relacionados "dog" e "beagle". Uma correspondência positiva com as classes relacionadas, nesse caso "dog" e "beagle", impulsiona a pontuação da resposta pai. Nesse exemplo, a resposta inclui todas as três classes: "animal", "dog" e "beagle". A pontuação da classe pai ("animal") é impulsionada, pois ela corresponde às classes relacionadas ("dog" e "beagle"). O pai é também um "type\_hierarchy" para mostrar que é um pai da hierarquia.

## Diretrizes para classificar altos volumes

Maximize a eficiência e o desempenho do serviço das seguintes maneiras ao enviar muitas imagens:

- Corte ou redimensione suas imagens para 224 x 224 pixels. O serviço é otimizado atualmente para o tamanho, embora ele possa mudar.
    - Corte a imagem se ela tem uma proporção de aspecto maior de 2:1 ou menor de 1:2.
    - Considere cortar a imagem e várias imagens quadradas ou inclua somente o centro da imagem, dependendo do que é mais importante para seu uso.
- Envie até 20 imagens em um único arquivo .zip. Você não precisa usar nenhuma compactação, pois as imagens JPEG e PNG são arquivos compactados.
- Use o parâmetro **classifier_ids** para especificar somente os classificadores que deseja usar.
- Embora o serviço leia tags EXIF e gire imagens, para obter o melhor rendimento, envie imagens que não precisam ser giradas pelo serviço (a tag **Orientação** é configurada para `1`).
