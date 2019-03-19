---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

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

<!-- Link definitions -->

[api-ref-text]: https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text

# Reconhecimento de texto em cenas naturais (Beta)
{: #recognize-text}

Use o modelo Text beta do {{site.data.keyword.visualrecognitionshort}} para detectar e reconhecer texto em inglês em imagens. O modelo Text foi projetado para reconhecer texto de cenário em imagens em vez de texto mais denso em documentos.

O modelo de Texto é um recurso beta privado e deve-se ter permissão do {{site.data.keyword.IBM_notm}} para fazer chamadas para o modelo. [Solicitar acesso ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://datasciencex.typeform.com/to/nU6efl){: new_window}. Para obter mais informações sobre recursos beta, consulte as [Notas sobre a liberação](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta).
{: important}

O modelo de Texto funciona melhor em sequências de texto curto. Por exemplo, um uso comum do modelo Text é ler sinais.

![Placa de trânsito com caixas delimitadoras em torno das palavras reconhecidas. Foto de Ashim D’Silva no Unsplash](images/walk-signal-detection.png) ![Palavras e pontuações de confiança detectadas na imagem do sinal de trânsito](images/walk-signal-response.png)

As caixas brancas ilustram cada palavra que o modelo reconhece na imagem.

## A resposta
{: #recognize-text-response}

A resposta inclui a sequência detectada e cada palavra dentro dessa sequência é identificada com as informações a seguir:

- A palavra reconhecida.
- Uma pontuação que indica confiança no reconhecimento da palavra.
- O local da caixa delimitadora ao redor da palavra. A caixa indica onde a palavra está localizada na imagem.
- Um número de linha em que a palavra foi detectada.

## Diretrizes para bom reconhecimento de texto
{: #recognize-text-guidelines}

O texto em imagens é melhor reconhecido quando adere a estas diretrizes:

- O texto é essencialmente palavras inteiras, não sequências de letras como códigos de produtos. O modelo reconhece palavras em vez de caracteres individuais e pode descartar palavras ou números de uma única letra.
- O texto é impresso em uma fonte padrão, não uma altamente estilizada. Por exemplo, o texto em placas de veículo ou títulos de cartaz de filme pode não ser reconhecido. Da mesma forma, o manuscrito pode não ser reconhecido.
- O modelo Text é treinado principalmente em palavras em inglês. É improvável que texto em outros idiomas seja reconhecido.

## Próximas Etapas
{: #recognize-text-next-steps}

- [Faça uma chamada](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text) para reconhecer texto em uma imagem.
- Familiarize-se com a API na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")][api-ref-text]{: new_window}.
