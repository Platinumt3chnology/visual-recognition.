---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# Reconhecimento de texto em cenas naturais

Use o modelo de Texto beta para detectar e reconhecer texto em inglês em imagens. O modelo de Texto é projetado para reconhecer o texto de cena impressa em imagens em vez do texto mais denso em documentos.

O modelo de Texto é um recurso beta e não é destinado para uso em um ambiente de produção. Para obter mais informações, veja "Recursos beta" nas [Notas sobre a liberação](/docs/services/visual-recognition/release-notes.html#beta).
{: tip}

O modelo de Texto funciona melhor em sequências de texto curto. Por exemplo, um uso comum do modelo de Texto é ler sinais de trânsito.

![Sinal de trânsito com caixas delimitadoras em torno de palavras detectadas](images/road-sign-text-detection.png)

![Palavras e pontuações de confiança na imagem de sinal de trânsito](images/road-sign-text-response.png)

As caixas brancas ilustram cada palavra que o modelo detectou na imagem.

## A resposta

A resposta inclui a sequência detectada e cada palavra dentro dessa sequência é identificada com as informações a seguir:

- A palavra detectada
- Uma pontuação que indica a confiança na precisão da palavra detectada.
- O local da caixa delimitadora ao redor da palavra. A caixa indica onde a palavra está localizada na imagem.
- Um número de linha em que a palavra foi detectada.

## Diretrizes para bom reconhecimento de texto

O texto em imagens é melhor reconhecido quando adere a estas diretrizes:

- O texto é essencialmente palavras inteiras, não sequências de letras como códigos de produtos. O modelo reconhece palavras em vez de caracteres individuais e pode descartar "palavras" ou números com letras únicas.
- O texto é impresso em uma fonte padrão, não uma altamente estilizada. Por exemplo, o texto em placas de veículo ou títulos de cartaz de filme pode não ser reconhecido. Da mesma forma, o manuscrito pode não ser reconhecido.
- O texto ocupa pelo menos 5% da imagem.
- O texto é inclinado não mais que 45 graus da horizontal. O modelo de texto beta lê tags EXIF e gira imagens. No entanto, para o melhor rendimento, envie imagens que não precisam ser giradas pelo serviço (a tag de **Orientação** EXIF é configurada como `1`).
- O modelo de Texto é treinado em palavras no idioma inglês. O texto em outros idiomas provavelmente não será reconhecido.

## Próximas Etapas

Familiarize-se com a API no [explorador de API do ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window}

Se você tiver perguntas ou comentários sobre o modelo de Texto, entre em contato com Kevin Gong em kgong@us.ibm.com.

---

Acesse os [docs](/docs/services/visual-recognition/index.html) principais.
