---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-29"

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

# Nota sobre a Liberação

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.
{: shortdesc}

## Recursos beta
{: #beta}

O {{site.data.keyword.IBM_notm}} libera os serviços, os recursos e o suporte ao idioma para sua avaliação que são classificados como beta. Esses recursos podem ficar instáveis, podem mudar frequentemente e podem ser descontinuados com breve aviso. Os recursos beta podem também não fornecer o mesmo nível de desempenho ou compatibilidade que os recursos geralmente disponíveis fornecem e não são destinados ao uso em um ambiente de produção. Os recursos beta são suportados somente no [developerWorks Answers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Mudanças
{: #changelog}

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.

### 11 de dezembro de 2017
{: #11december2017}

<ul>
  <li>
    <strong>Aumento de precisão e saída com o modelo Geral</strong>
      <p>
        O modelo Geral, que contém milhares de tags, agora detecta mais objetos secundários e melhorou a detecção de cenário. Essas melhorias ajudam a reconhecer os aspectos menos importantes de uma imagem. Além disso, o número médio de tags retornadas por imagem aumentou para 10.
      </p>
      <p>
        A imagem a seguir mostra um exemplo das tags retornadas antes da atualização e as tags adicionais que são agora retornadas.
      </p>
      <img src="images/antarctica-iceberg.jpg" alt="Iceberg na Antártida">
      <table>
        <tr>
          <th>Tags originais</th>
          <th>Tags adicionais</th>
        </tr>
        <tr>
          <td>
          Tag: iceberg<br/>
          Pontuação: 0,919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: ice mass<br/>
          Pontuação: 0,801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: nature<br/>
          Pontuação: 0,770</td>
        </tr>
        <tr>
          <td>
          Tag: blue color<br/>
          Pontuação: 0,975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: alabaster color<br/>
          Pontuação: 0,5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Novo modelo Explícito disponível em beta</strong>
      <p>
        O modelo Explícito, que é ativado no beta, classifica se uma imagem tem conteúdo pornográfico e é inapropriada para uso geral. É possível incluir o modelo Explícito com outros modelos para análise combinada. Por exemplo, inclua os IDs de classificador `default` e `explicit` em sua solicitação para retornar tags de imagem e se a imagem tem conteúdo explícito.
      <p>
Para obter detalhes sobre a chamada API, veja o método **Classificar imagens** na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image) ou experimente o modelo no [Explorador de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify).
      </p>
    </li>
    <li>
      <strong>Suporte para tamanhos de arquivos maiores</strong>
      <p>
        Os métodos <strong>Classificar imagens</strong> suportam agora arquivos de imagem de até 10 MB e arquivos .zip de até 100 MB.
    </li>
    <li>
      <strong>Matriz necessária ao passar IDs de classificador</strong>
      <p>
        A API cumpre agora uma matriz quando você passa `classifier_ids` como parte do objeto **parameters** no método **Classificar imagens**. Anteriormente, era possível passar um ID de classificador como uma sequência. Para obter mais informações, veja a descrição de parâmetros e o arquivo de exemplo na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image).
      </p>
    </li>
</ul>

### 8 de setembro de 2017
{: #8september2017}

- **Procura de similaridade beta e coleções encerradas**: desde 8 de setembro de 2017, o período beta para Procura de similaridade está encerrado. Para obter mais informações, veja [API do Visual Recognition - Atualização de procura de similaridade ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30 de junho de 2017
{: #30june2017}

- **Melhoria na identificação**: aumentamos o número de imagens de treinamento para o classificador padrão. Esse aumento melhora a capacidade de reconhecer precisamente o ‘cenário’ geral de uma imagem. Para obter detalhes, veja [Aprimoramentos adicionais para o recurso de identificação geral ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **Idiomas adicionais**: o método **Classificar imagens** suporta agora coreano, italiano e alemão, além de inglês, árabe, espanhol e japonês.

    Para obter detalhes sobre a chamada API, veja o método **Classificar uma imagem** na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}.

### 16 de maio de 2017
{: #16may2017}

- **Um novo classificador de alimento está disponível: beta**

    Um novo modelo de reconhecimento de alimento beta fornece especificidade e precisão aprimoradas para imagens de itens alimentares. O método **Classificar uma imagem** permite incluir esse novo classificador, "food", no parâmetro `classifier_ids`.

### 5 de abril de 2017
{: #5april2017}

- **Uma nova ferramenta {{site.data.keyword.visualrecognitionshort}} está disponível: beta**

    Um novo recurso beta, a ferramenta {{site.data.keyword.visualrecognitionshort}}, está disponível em [https://watson-visual-recognition.ng.bluemix.net/ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Essa ferramenta ajuda a trabalhar mais facilmente com o serviço {{site.data.keyword.visualrecognitionshort}}. Inserindo sua chave API do {{{site.data.keyword.cloud_notm}}, é possível usar uma GUI para acessar os recursos Identificação geral e Detecção de face, bem como para criar, retreinar e excluir facilmente classificadores customizados associados à sua chave API, sem necessidade de codificar.

### 8 de março de 2017
{: #8march2017}

- **Atualizado o suporte ao idioma para identificação de classificador geral**

    O classificador geral agora retorna tags em todos os idiomas suportados.

- **Problemas conhecidos**

    **CORRIGIDO 13-04-2017**: chamar repetidamente `GET /classifiers` enquanto o treinamento ou retreinamento está em andamento, a fim de verificar o status, pode resultar no encerramento da tarefa de treinamento. Como solução alternativa para esse problema, pesquisa o status de um novo classificador usando `GET /classifiers/{classifier_id}`. Em outras palavras, use o classificador `GET` para um único ID de classificador, em vez de `GET /classifiers`, que obtém todos os classificadores e pode acionar esse problema. Observe que `GET /classifiers/{classifier_id}` também é mais rápido.

### 15 de dezembro de 2016
{: #15december2016}

- **Melhoria na identificação do classificador geral**

    - Os algoritmos de aprendizado profundo do classificador geral foram atualizados. Há uma melhoria significativa na qualidade de tag para todos os idiomas e um aumento significativo no volume de tags em inglês retornadas pelo serviço. Essa saída de tag de alta qualidade também está disponível quando você cria seu próprio classificador customizado.
    - A identificação de cor foi incluída. O serviço agora retorna a primeira ou duas cores na imagem.

- **Problemas conhecidos**

    - As imagens enviadas para a demo com tags de metadados EXIF não especificam orientação (paisagem versus retrato) corretamente para o serviço. As imagens transferidas por upload do iPhone podem conter tags de metadados EXIF. A solução alternativa para isso é atualizar os metadados da imagem para não depender de tags de metadados EXIF para especificar a orientação de sua imagem. Geralmente, é possível fazer isso simplesmente abrindo a imagem em seu computador e salvando-a. Por exemplo, em um Mac, abrir em Visualização e, em seguida, salvar a imagem configura as tags de orientação correta.
    - Enviar imagens para o serviço {{site.data.keyword.visualrecognitionshort}} com os valores de [tag EXIF ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://en.wikipedia.org/wiki/Exif){: new_window} de 8, 3 ou 6 pode incluir latência. O serviço gira os pixels da imagem para o ponto de visualização codificado. É possível economizar tempo girando previamente suas imagens ou removendo os cabeçalhos EXIF se eles não são importantes para sua tarefa do {{site.data.keyword.visualrecognitionshort}}.

### 1 de dezembro de 2016
{: #1december2016}

- **Nova precificação**

    A IBM reduziu a precificação de classificadores customizados no serviço {{site.data.keyword.visualrecognitionshort}} e aumentou o que está disponível no plano grátis. Para obter mais informações, veja a [Página de precificação do {{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 de outubro de 2016
{: #7october2016}

- **Aprimoramentos de detecção de face**

    O serviço tem um novo algoritmo de detecção de face que melhora a resposta dos métodos `GET` e `POST /v3/detect_faces`. O serviço ajustou a filtragem de detecções faciais de idade, nome e sexo de baixa confiança. Como resultado, mais faces são localizadas e um intervalo maior de confianças é retornado.

### 8 de setembro de 2016
{: #8september2016}

- **Procura de similaridade BETA**

    Os usuários podem agora fazer upload de sua própria coleção de imagens, usar uma imagem para procurar essa coleção para imagens similares e, em seguida, o serviço retorna as 100 principais imagens mais semelhantes. A procura de similaridade pode ser utilizada para qualquer propósito e os usuários podem customizar o treinamento do serviço em coleções de até 1 milhão de imagens cada. Para obter mais informações sobre como usar a nova funcionalidade de procura de similaridade, veja as páginas [Tutorial](/docs/services/visual-recognition/tutorial-collections.html) e [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **O reconhecimento de texto está agora no beta encerrado**

    Os métodos `POST` e `GET /v3/recognize_text` voltaram no beta encerrado. A IBM espera continuar a suportar clientes BETA que usam o serviço, sem planos atuais para outro beta aberto.

### 1 de agosto de 2016

- **Término de precificação introdutória**

    O treinamento e o retreinamento de classificador customizado, a classificação de imagem customizada e o armazenamento de classificador customizado não são mais grátis. Para obter informações sobre a precificação, veja a [página de precificação](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) do serviço {{site.data.keyword.visualrecognitionshort}}.

### 5 de julho de 2016
{: #5july2016}

- **Atualizando classificadores customizados**

    Os classificadores customizados não são mais limitados a um conjunto fixo de dados de treinamento. Um usuário pode agora atualizar os classificadores existentes com novas imagens ou incluir classificadores de exemplo positivo ou negativo adicionais em um classificador treinado existente. Fornecendo imagens de exemplo adicionais para o Watson para aprendizado, o serviço pode tornar o classificador de um usuário mais preciso. Os classificadores customizados podem agora aprender ao longo do tempo, melhorando continuamente o entendimento de informações visuais.

- **Problemas conhecidos**

    **CORRIGIDO 13-04-2017**: os usuários podem obter um código de erro 500 após 30 ou 90 segundos ao atualizar um classificador existente. Apesar do erro, há uma boa chance de que a solicitação de retreinamento seja concluída com êxito. Aguarde pelo menos 2 minutos e, em seguida, verifique o status do classificador usando o método `GET classifiers/{classifier\_id}`. Se o status for "pronto" e o registro de data e hora "retreinado" foi atualizado, a solicitação de retreinamento que gerou o código 500 foi bem-sucedida. Caso contrário, se o registro de data e hora "retreinado" não foi atualizado, há uma explicação incluída na resposta que informa a razão pela qual o retreinamento falhou e o serviço reverterá o classificador para a versão que havia antes de a solicitação de retreinamento ser emitida.

### 20 de maio de 2016
{: #20 may 2016}

Esta é a liberação de Disponibilidade Geral do serviço {{site.data.keyword.visualrecognitionshort}}. Esta liberação introduz a Versão 3 do serviço e é uma mudança significativa. Esta liberação incorpora a funcionalidade do serviço AlchemyVision, que foi descontinuado.

Os classificadores customizados que foram criados enquanto o serviço estava em Beta devem ser recriados em uma instância GA do serviço.

As mudanças e atualizações a seguir foram feitas no serviço {{site.data.keyword.visualrecognitionshort}}:

- **Data da versão:** para utilizar os recursos desta liberação, use `2016-05-20` como o valor para o parâmetro `version`.
- **Classes e classificadores:** os classificadores únicos são agora chamados "classes". Em GA, um grupo de classes é chamado de "classificador".
- **Classificação:** use os métodos `POST` ou `GET /v3/classify` para identificar de forma rápida e precisa uma variedade de assuntos e cenários com classes padrão.
- **Detecção de face:** use os métodos `POST` ou `GET /v3/detect_faces` para detectar faces em imagens e obter informações sobre elas, como onde a face está localizada na imagem e a faixa de idade estimada e o gênero para cada face. O serviço também pode identificar várias celebridades por nome e pode fornecer um gráfico de conhecimento para que seja possível executar agregações interessantes em conceitos de nível superior.
- **Classificadores customizados com múltiplas máscaras:** agora é possível criar e treinar classificadores altamente especializados que são definidos por várias classes. Por exemplo, é possível criar um classificador "new\_red\_car" que é definido pelas classes "new\_cars" e "red\_cars". Para saber mais sobre como criar classificadores com diversas máscaras, veja [Estrutura dos dados de treinamento](/docs/services/visual-recognition/customizing.html#structure).
- **Treinamento assíncrono:** o treinamento de classificadores customizados é agora assíncrono, então as chamadas de treinamento são concluídas rapidamente enquanto seu classificador customizado continua a aprender no segundo plano. Para verificar o status de treinamento de seu classificador customizado e descobrir quando ele está disponível para uso, chame o método `GET /v3/classifiers/{classifier_id}` e verifique o parâmetro de resposta `status`.

### 2 de dezembro de 2015
{: #2december2015}

A liberação mais nova do serviço {{site.data.keyword.visualrecognitionshort}} é uma mudança significativa que introduz uma nova versão da API do {{site.data.keyword.visualrecognitionshort}} (v2). A Versão 1 do serviço {{site.data.keyword.visualrecognitionshort}} está disponível para uso até que o serviço saia do beta.

Para começar a usar imediatamente a versão 2 da API, entenda e atualize seu código para refletir essas mudanças:

- Na versão 1 do serviço, você analisou imagens por rótulos. Na versão 2 do serviço, os rótulos são chamados **classificadores**. Os classificadores têm um ID de classificador exclusivo indicado pelo parâmetro `classifier_id` e um nome abreviado indicado pelo parâmetro `name`.
- O método `POST /v1/recognize` para analisar uma imagem é agora o método [`POST /v2/classify` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}. O parâmetro `labels_to_check` é renomeado para `classifier_ids`.
- O método `GET /v1/tag/labels` para recuperar uma lista de rótulos na V1 é agora o método [`GET /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} para recuperar uma lista de classificadores.
- Além de recuperar uma lista de classificadores, também é possível recuperar detalhes para um classificador específico com o novo método [`GET /v2/classifiers/{classifier_id}` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window}.
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta permite que você crie classificadores customizados com o novo método [`POST /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window}. Para saber mais sobre como criar classificadores customizados, veja [Criando classificadores customizados](/docs/services/visual-recognition/customizing.html).
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta também permite excluir classificadores customizados com o novo método [`DELETE /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window}.
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta requer o parâmetro `version`. Especifique a data de liberação da versão da API que você deseja usar no formato `MM-DD-YYYY`.
