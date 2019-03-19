---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

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

[watson-studio-reg]: https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs
[demo]: https://www.ibm.com/watson/services/visual-recognition/demo

# Nota sobre a Liberação
{: #release-notes}

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.
{: shortdesc}

## Versão da API de Serviço
{: version}

As solicitações de API requerem um parâmetro version que use uma data no formato `version=YYYY-MM-DD`. Sempre que mudamos a API de uma maneira incompatível com versões anteriores, lançamos uma nova versão secundária da API.

Envie o parâmetro version com cada solicitação de API. O serviço usa a versão da API para a data que você especificar ou a versão mais recente antes dessa data. Não padronar para a data atual. Em vez disso, especifique uma data que corresponda a uma versão que seja compatível com seu aplicativo e não a mude até que o aplicativo esteja pronto para uma versão mais recente.

A versão atual é  ` 2018-03-19 `.

## Recursos beta
{: #beta}

O {{site.data.keyword.IBM_notm}} libera os serviços, os recursos e o suporte ao idioma para sua avaliação que são classificados como beta. Esses recursos podem ficar instáveis, podem mudar frequentemente e podem ser descontinuados com breve aviso. Os recursos beta podem também não fornecer o mesmo nível de desempenho ou compatibilidade que os recursos geralmente disponíveis fornecem e não são destinados ao uso em um ambiente de produção. Os recursos Beta são suportados somente no [IBM Developer Answers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Mudanças
{: #changelog}

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.

### 15 de janeiro de 2019
{: #15january2019}

- ** Tradução para gênero no Detect Faces **
    - Os métodos **Detectar faces** agora retornam rótulos traduzidos para "Masculino" e "Feminino" ao fornecer o idioma no cabeçalho de solicitação **Aceitar idioma**. Para obter detalhes, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}.

### 1º de outubro de 2018
{: #01october2018}

- **As instâncias de serviço criadas antes de 23 de maio de 2018 são excluídas.**

    - Conforme notificado anteriormente, todas as instâncias do {{site.data.keyword.visualrecognitionshort}} criadas antes de 23 de maio de 2018 não estão mais ativas. Os dados das instâncias estão agora excluídos. Consulte [Migrando](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) para obter detalhes sobre como mover para uma nova instância de serviço.
    - As instâncias de serviço criadas após essa data não foram afetadas.
    - Se você tiver perguntas, entre em contato com o [suporte IBM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/ibmcloudsupport){: new_window}.

### 1 de agosto de 2018
{: #01august2018}

- **Disponibilidade geral dos modelos Food e Explicit**

    Os modelos Food e Explicit foram movidos de Beta para Disponibilidade geral (GA). O modelo Food reconhece mais alimentos e refeições que o modelo General (default). O modelo Explicit identifica o que pode ser considerado imagens pornográficas.

    Nenhuma mudança de código é necessária. Ambos os modelos são gratuitos no plano Lite e custam US$ 0,002 por imagem no plano Standard.

    Para obter mais informações, consulte [Atualizações para o Watson Visual Recognition ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/visrec-price-reduction){: new_window} no <em>blog do Watson</em>.

### 1 de julho de 2018
{: #01july2018}

- ** Nova precificação para modelos customizados **
    - A partir de 1º de julho de 2018, a classificação de uma imagem com um modelo customizado custa metade da taxa anterior e agora é de US$ 0,002 por imagem. Para obter detalhes e outras informações importantes, consulte [Atualizações para o Watson Visual Recognition\- Redução de preço para Classificação customizada ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/visrec-price-reduction){: new_window} no <em>blog do Watson</em>.

### 21 de junho de 2018
{: #21june2018}

- ** Suporte ao Idioma Adicional **

    - Os métodos **Classificar** agora suportam o chinês (simplificado e tradicional) e o português (brasileiro) na saída de classes do modelo `default` (General). Para obter a lista completa de idiomas, consulte [Idiomas suportados](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).
    - Todos os idiomas também são suportados agora nas respostas dos modelos **Food** e **Explicit**.


### 22 de maio de 2018
{: #22may2018}

- ** Novo processo de autenticação de API **:

    Agora você é autenticado com o Identity and Access Management (IAM) em um novo terminal:

    - Use uma URL de terminal diferente para novas instâncias. O terminal padrão é `https:/gateway.watsonplatform.net/visual-recognition/api/`. Para localizar a URL para sua instância de serviço, verifique as credenciais clicando na instância do [Painel do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard/apps?watson){: new_window}.
    - Modifique como você se autenticará na API. Você fornece uma chave do IAM ou um token de acesso para sua instância de serviço. Consulte  [ Migrando ](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)  para obter exemplos.

    Para instâncias de serviço criadas antes de 23 de maio de 2018, o processo de autenticação e o terminal não mudaram. Autentique-se fornecendo o parâmetro de consulta `api_key`.

- ** Atualizações para o plano Lite **

    Os planos Lite criados depois de 22 de maio de 2018 estão mudando:

    - As novas instâncias do plano Lite continuarão disponíveis depois de 30 dias, se você as usar todo mês.
    - É possível criar e treinar novamente dois modelos customizados sob o novo plano Lite.
    - Os planos Lite incluem até 1.000 eventos por mês. Cada imagem enviada para classificação, detecção ou treinamento é um evento. O download de um modelo Core ML não é considerado para o limite de eventos.

    Se as suas necessidades excederem o plano Lite, atualize para uma conta faturável. [Explore ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} os planos de precificação.

- ** Segurança de informações **:

    Atualizamos a documentação para incluir alguns novos detalhes sobre privacidade de dados. Leia os detalhes em  [ Segurança de informações ](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security).

### 12 de abril de 2018
{: #12april2018}

- **Suporte para treinar novamente um modelo customizado no plano Lite**

    No plano Lite, você não terá mais que excluir e criar outro modelo customizado quando desejar atualizar ou treinar novamente o modelo. Agora é possível atualizar um modelo customizado desde que você permaneça em [limites](https://console.bluemix.net/catalog/services/visual-recognition) diários e mensais do plano.

    Se for necessário ter múltiplos modelos ou múltiplas versões do mesmo modelo, atualize do plano Lite para uma conta faturável.

- **Nova versão secundária com suporte para CORS**

    ** Versão: **  ` 2018-03-19 `

    Agora suportamos os cabeçalhos Compartilhamento de recurso de origem cruzada (CORS) quando você especifica `version=2018-03-19` em solicitações.

### 5 de abril de 2018
{: #5april2018}

- ** Corrigir o problema de pontuação do modelo Face **

  O intervalo para a pontuação de idade no modelo Face é restaurado para o intervalo original de 0 a 1. Para obter detalhes, consulte os [Problemas conhecidos](#2april2018) de 2 de abril de 2018.

- ** Novos Parâmetros de Dados de Formulário **

    Os métodos **Classificar imagens** e **Detectar faces em imagens** suportam novos parâmetros de dados de formulário. Classificar imagens suporta os parâmetros `url`, `classifier_ids`, `threshold` e `owners` separados e Detectar faces suporta `url`.

    Anteriormente, você codificava os valores em uma sequência JSON e passava o parâmetro de dados de formulário **parameters**. É possível usar o novo método de passagem desses valores em parâmetros de dados de formulário separados para todo o desenvolvimento do aplicativo. Para obter detalhes, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### 2 de abril de 2018
{: #2april2018}

- ** Disponibilidade geral do modelo de Face aprimorada **

    O modelo de detecção facial atualizado está agora em Disponibilidade geral (GA).

    Esse modelo aprimorado usa conjuntos de dados de treinamento mais amplos para maior precisão de detecção facial para idade e sexo. Por exemplo, as previsões de idade são melhoradas reduzindo-se o intervalo entre `min` e `max`. A faixa etária fixa de 9 anos no modelo anterior foi substituída por uma faixa dinâmica e menor. A faixa etária média é agora de 4,9 anos.

    - Mudanças na API

    Outras diferenças entre o modelo Face aprimorado e anterior:
        - O modelo aprimorado suporta os formatos de imagem .gif e .tif.
        - O modelo aprimorado suporta tamanhos de arquivo maiores: até 10 MB para arquivos de imagem e até 100 MB para arquivos .zip.
        - O modelo aprimorado não inclui informações de `FaceIdentity` na resposta. As informações de identificação se referem ao `name` da pessoa, `score` e gráfico de conhecimento de `type_hierarchy`.

    Para obter detalhes sobre a API, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

    - Problemas Conhecidos

        - Os parâmetros de formulário não podem incluir o  ** Content-Type **. Por exemplo, essa solicitação falha ao analisar o parâmetro **url** porque inclui `;type=text/plain`:

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={2}{0}{1}{6}-05-20"
            ```
            {: pre}

        - A pontuação de idade tem um intervalo de 0 a 0,3. Estamos trabalhando para restaurar o intervalo original de 0 a 1.

    - Terminal Beta descontinuado

    O terminal beta em `/v3/detect_faces_beta` foi descontinuado e não estará acessível depois de 17 de maio de 2018. Certifique-se de que suas solicitações apontem para `/v3/detect_faces`.

### 20 de março de 2018
{: #20march2018}

- ** Integração com o Apple Core ML **

    O {{site.data.keyword.visualrecognitionshort}} agora inclui suporte para o formato do modelo Apple Core ML. É possível usar uma versão de Core ML de seu modelo do {{site.data.keyword.visualrecognitionshort}} nos apps iOS.

    **Iniciar o desenvolvimento**: para começar a desenvolver com o {{site.data.keyword.visualrecognitionshort}} e o Core ML, verifique esses projetos no GitHub:

    - Classificar imagens localmente: [{{site.data.keyword.visualrecognitionshort}} com Core ML ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - Integrar o {{site.data.keyword.discoveryfull}} aos resultados: [{{site.data.keyword.visualrecognitionshort}} e Discovery com o Core ML ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - Explorar o SDK: [SDK do Swift ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **Mudanças na API**

    As mudanças na API compatíveis com versões anteriores a seguir estão incluídas na integração:

    - Um novo campo `core_ml_enabled` que indica se um modelo de classificador pode ser transferido por download como um modelo Core ML. O campo é retornado na resposta para chamadas para `GET and POST /v3/classifiers` e `GET /v3/classifiers/{classifier_id}`.
    - Um novo método `GET /v3/classifiers/{classifier_id}/core_ml_model` para fazer download de um modelo Core ML como um arquivo .mlmodel.  É possível fazer download de arquivos do modelo Core ML para modelos customizados criados depois de 19 de março.
    - Um novo campo `updated` com a data de treinamento mais recente do modelo. O campo `updated` corresponde ao campo `retrained` ou ao campo `created`.

    Para obter detalhes sobre as mudanças na API para o Core ML, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}.

- **Nova ferramenta disponível: Watson Studio**

    O [Watson Studio ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")][watson-studio-reg]{: new_window} é o novo ambiente integrado que inclui uma substituição para a ferramenta beta {{site.data.keyword.visualrecognitionshort}}. O Watson Studio suporta não apenas o {{site.data.keyword.visualrecognitionshort}}, mas também muitos outros serviços e recursos do {{site.data.keyword.cloud_notm}}. É possível usar o Watson Studio com todas as suas instâncias e classificadores existentes do {{site.data.keyword.visualrecognitionshort}}.

     O Watson Studio fornece um ambiente colaborativo na nuvem. Com o Watson Studio, desenvolvedores, especialistas no assunto, cientistas de dados e outros podem construir e treinar o {{site.data.keyword.visualrecognitionshort}} e outros modelos de IA. Também é possível usar o Watson Studio para acessar os modelos General e Face integrados.

     O Watson Studio também suporta o Core ML. É possível fazer download de um arquivo de modelo Core ML para seu modelo customizado.

    [Inicie a utilização do ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")][watson-studio-reg]{: new_window} com o Watson Studio.

- **Arquitetura de deep learning atualizada para modelos customizados**

    O {{site.data.keyword.visualrecognitionshort}} agora usa uma arquitetura de rede de deep learning mais rápida e mais eficiente para classificação. Os modelos atualizados também podem diferenciar mais fortemente entre a classe superior e o restante das classes. Essa abordagem pode resultar em tempos de treinamento um pouco mais longos. A nova arquitetura é usada para treinar novos modelos customizados. Ao treinar novamente modelos mais antigos existentes, a arquitetura original é usada.

    O exemplo a seguir mostra a diferenciação com a nova arquitetura:

    ![Homem com arco e flecha praticando tiro ao alvo. Foto de Annie Spratt no Unsplash](images/archery.jpg)

    <table>
      <tr>
        <th>Classe e pontuação originais</th>
        <th>Atualização de classe e pontuação</th>
      </tr>
      <tr>
        <td>Archery</br>0,99 </td>
        <td><strong> archery <strong></br>0,9</td>
      </tr>
      <tr>
        <td>Racing automático</br>0,996398</td>
        <td><strong> biking </strong></br>0,004</td>
      </tr>
      <tr>
        <td>Ciclismo</br>0,0500174</td>
        <td><strong> pescaria </strong></br>0,001</td>
      </tr>
      <tr>
        <td>Pescando</br>0,11029</td>
        <td><strong> golfe </strong></br>0,031</td>
      </tr>
      <tr>
        <td>Golf</br>0,0980796</td>
        <td><strong>ginástica</strong></br>0,029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0,964391</td>
        <td><strong> judô </strong></br>0,021</td>
      </tr>
      <tr>
        <td>Judô</br>0,339119</td>
        <td><strong> corridas </strong></br>0,002</td>
      </tr>
      <tr>
        <td>Patinação</br>0,0393602</td>
        <td><strong> patinando </strong></br>0,061</td>
      </tr>
      <tr>
        <td>Esquiando</br>0,0310527</td>
        <td><strong> esquiando </strong></br>0,003</td>
      </tr>
      <tr>
        <td>Rastreamento e campo</br>0.208147</td>
        <td><strong>rastreamento</strong></br>0,035</td>
      </tr>
    </table>

- ** Suporte ao idioma francês **

    Os métodos **Classificar** agora suportam francês na saída de classes de modelo `default`. Para obter a lista completa de idiomas, consulte [Idiomas suportados](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).

### 23 de fevereiro de 2018
{: #23february2018}

- **Modelo de Face Enhanced disponível em beta**

    Um modelo de detecção facial atualizado está disponível. Esse modelo beta usa conjuntos de dados de treinamento mais amplos para maior precisão de detecção facial para idade e sexo. Para obter mais informações, consulte [Aumentando a precisão do serviço {{site.data.keyword.visualrecognitionshort}} do Watson da IBM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} e [Minimizando a propensão em modelos de IA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}.

    - É possível visualizar resultados do modelo atualizado na [demo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")][demo]{: new_window} e na beta [Visual Recognition Tool ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}.
    - O modelo beta está disponível em `/v3/detect_faces_beta`.

    Diferenças entre os modelos beta e de disponibilidade geral (GA):
    - O modelo beta suporta os formatos de imagem .gif e .tif; espera-se que esse aprimoramento seja aplicado ao modelo GA.
    - O modelo beta suporta tamanhos de arquivo maiores: até 10 MB para arquivos de imagem e até 100 MB para arquivos .zip. Espera-se que esse aprimoramento seja aplicado ao modelo GA.
    - A detecção facial beta não inclui informações de `FaceIdentity` na resposta.
    - A solicitação de POST do modelo beta requer um nome de arquivo não vazio. O modelo Face de GA não aplica essa restrição.
    - A solicitação de POST do modelo beta suporta um parâmetro de formulário separado chamado `url`. O modelo GA anexa essas informações ao objeto JSON `parameters`. Para obter detalhes, consulte o [Explorador de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-api-explorer.mybluemix){: new_window}.

- ** Identidade de face descontinuada **

    As informações de identidade na resposta do modelo Face de GA foram descontinuadas e serão removidas da API em **2 de abril de 2018.** As informações de identificação se referem ao `name` da pessoa, `score` e gráfico de conhecimento de `type_hierarchy`.

### 16 de janeiro de 2018
{: #16january2018}

- **A conta e o plano Lite substituem o plano Grátis**

    Uma conta Lite é grátis; não há necessidade de cartão de crédito. No entanto, as instâncias de serviço do plano Lite são excluídas depois de 30 dias.

    O número máximo de chamadas de API que podem ser feitas com o plano Lite é um pouco diferente do plano Grátis. É possível fazer no máximo 7.500 chamadas de API por mês em 250 chamadas por dia no plano Lite.

    Para atualizar para uma conta faturável quando se tem classificadores customizados, crie outra instância de serviço e recrie os classificadores customizados.

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
      <img src="images/tree-flower.jpg" alt="Fotografia de uma azaleia">
      <table>
        <tr>
          <th>Tags originais</th>
          <th>Tags adicionais</th>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: tree<br/>
          Pontuação: 0,799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: flower<br/>
          Pontuação: 0,792</td>
        </tr>
        <tr>
          <td>
          Tag: alpine azalea<br/>
          Pontuação: 0,696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: plant<br/>
          Pontuação: 0,868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: azalea<br/>
          Pontuação: 0,617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            Tag: swamp azalea<br/>
          Pontuação: 0,5</td>
          </td>
          <td></td>
        <tr>
          <td>
            Marcação: cor laranja avermelhada<br/>
          Pontuação: 0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Novo modelo Explícito disponível em beta</strong>
      <p>
        O modelo Explícito, que é ativado no beta, classifica se uma imagem tem conteúdo pornográfico e é inapropriada para uso geral. É possível incluir o modelo Explícito com outros modelos para análise combinada. Por exemplo, inclua os IDs de classificador `default` e `explicit` em sua solicitação para retornar tags de imagem e se a imagem tem conteúdo explícito.
      <p>
        Para obter detalhes sobre a chamada de API, consulte o método **Classificar imagens** na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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
        A API cumpre agora uma matriz quando você passa `classifier_ids` como parte do objeto **parameters** no método **Classificar imagens**. Anteriormente, era possível passar um ID de classificador como uma sequência. Para obter mais informações, veja a descrição de parâmetros e o arquivo de exemplo na [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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

    Para obter detalhes sobre a chamada API, veja o método **Classificar uma imagem** método na [API de referência ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

### 16 de maio de 2017
{: #16may2017}

- **Um novo classificador de alimento está disponível: beta**

    Um novo modelo de reconhecimento de alimento beta fornece especificidade e precisão aprimoradas para imagens de itens alimentares. O método **Classificar uma imagem** permite incluir esse novo classificador, "food", no parâmetro `classifier_ids`.

### 5 de abril de 2017
{: #5april2017}

- **Uma nova ferramenta {{site.data.keyword.visualrecognitionshort}} está disponível: beta**

    Um novo recurso beta, a ferramenta {{site.data.keyword.visualrecognitionshort}}, está disponível em [https://watson-visual-recognition.ng.bluemix.net/ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Essa ferramenta ajuda a trabalhar mais facilmente com o serviço {{site.data.keyword.visualrecognitionshort}}. Inserindo sua chave API do {{site.data.keyword.cloud_notm}}, é possível usar uma GUI para acessar os recursos Identificação geral e Detecção facial, bem como para criar, retreinar e excluir facilmente classificadores customizados associados à sua chave API, sem necessidade de codificar.

### 8 de março de 2017
{: #8march2017}

- **Atualizado o suporte ao idioma para identificação de classificador geral**

    O classificador geral agora retorna tags em todos os idiomas suportados.

- **Problemas Conhecidos**

    **CORRIGIDO 13-04-2017**: chamar repetidamente `GET /classifiers` enquanto o treinamento ou retreinamento está em andamento, a fim de verificar o status, pode resultar no encerramento da tarefa de treinamento. Como solução alternativa para esse problema, pesquisa o status de um novo classificador usando `GET /classifiers/{classifier_id}`. Em outras palavras, use o classificador `GET` para um único ID de classificador, em vez de `GET /classifiers`, que obtém todos os classificadores e pode acionar esse problema. Observe que `GET /classifiers/{classifier_id}` também é mais rápido.

### 15 de dezembro de 2016
{: #15december2016}

- **Melhoria na identificação do classificador geral**

    - Os algoritmos de aprendizado profundo do classificador geral foram atualizados. Há uma melhoria significativa na qualidade de tag para todos os idiomas e um aumento significativo no volume de tags em inglês retornadas pelo serviço. Essa saída de tag de alta qualidade também está disponível quando você cria seu próprio classificador customizado.
    - A identificação de cor foi incluída. O serviço agora retorna a primeira ou duas cores na imagem.

- **Problemas Conhecidos**

    - As imagens enviadas para a demo com tags de metadados EXIF não especificam orientação (paisagem versus retrato) corretamente para o serviço. As imagens transferidas por upload do iPhone podem conter tags de metadados EXIF. A solução alternativa para isso é atualizar os metadados da imagem para não depender de tags de metadados EXIF para especificar a orientação de sua imagem. Geralmente, é possível fazer isso simplesmente abrindo a imagem em seu computador e salvando-a. Por exemplo, em um Mac, abrir em Visualização e, em seguida, salvar a imagem configura as tags de orientação correta.
    - Enviar imagens para o serviço {{site.data.keyword.visualrecognitionshort}} com os valores de [tag EXIF ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://en.wikipedia.org/wiki/Exif){: new_window} de 8, 3 ou 6 pode incluir latência. O serviço gira os pixels da imagem para o ponto de visualização codificado. É possível economizar tempo girando previamente suas imagens ou removendo os cabeçalhos EXIF se eles não são importantes para sua tarefa do {{site.data.keyword.visualrecognitionshort}}.

### 1 de dezembro de 2016
{: #1december2016}

- **Nova precificação**

    O {{site.data.keyword.IBM_notm}} reduziu a precificação de classificadores customizados no serviço {{site.data.keyword.visualrecognitionshort}} e aumentou o que está disponível no plano grátis. Para obter mais informações, veja a [Página de precificação do {{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 de outubro de 2016
{: #7october2016}

- **Aprimoramentos de detecção facial**

    O serviço tem um novo algoritmo de detecção facial que melhora a resposta dos métodos `GET` e `POST /v3/detect_faces`. O serviço ajustou a filtragem de detecções faciais de idade, nome e sexo de baixa confiança. Como resultado, mais faces são localizadas e um intervalo maior de confianças é retornado.

### 8 de setembro de 2016
{: #8september2016}

- **Procura de similaridade BETA**

    Os usuários podem agora fazer upload de sua própria coleção de imagens, usar uma imagem para procurar essa coleção para imagens similares e, em seguida, o serviço retorna as 100 principais imagens mais semelhantes. A procura de similaridade pode ser utilizada para qualquer propósito e os usuários podem customizar o treinamento do serviço em coleções de até 1 milhão de imagens cada. Para obter mais informações sobre como usar a nova funcionalidade de procura de similaridade, veja as páginas [Tutorial](/docs/services/visual-recognition/tutorial-collections.html) e [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **O reconhecimento de texto está agora no beta encerrado**

    Os métodos `POST` e `GET /v3/recognize_text` voltaram no beta encerrado. A {{site.data.keyword.IBM_notm}} espera continuar a suportar clientes BETA que usam o serviço, sem planos atuais para outro beta aberto.

### 1 de agosto de 2016

- **Término de precificação introdutória**

    O treinamento e o retreinamento de classificador customizado, a classificação de imagem customizada e o armazenamento de classificador customizado não são mais grátis. Para obter informações sobre a precificação, veja a [página de precificação](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) do serviço {{site.data.keyword.visualrecognitionshort}}.

### 5 de julho de 2016
{: #5july2016}

- **Atualizando classificadores customizados**

    Os classificadores customizados não são mais limitados a um conjunto fixo de dados de treinamento. Um usuário pode agora atualizar os classificadores existentes com novas imagens ou incluir classificadores de exemplo positivo ou negativo adicionais em um classificador treinado existente. Fornecendo imagens de exemplo adicionais para o Watson para aprendizado, o serviço pode tornar o classificador de um usuário mais preciso. Os classificadores customizados podem agora aprender ao longo do tempo, melhorando continuamente o entendimento de informações visuais.

- **Problemas Conhecidos**

    **CORRIGIDO 13-04-2017**: os usuários podem obter um código de erro 500 após 30 ou 90 segundos ao atualizar um classificador existente. Apesar do erro, há uma boa chance de que a solicitação de retreinamento seja concluída com êxito. Aguarde pelo menos 2 minutos e, em seguida, verifique o status do classificador usando o método `GET classifiers/{classifier\_id}`. Se o status for "pronto" e o registro de data e hora "retreinado" foi atualizado, a solicitação de retreinamento que gerou o código 500 foi bem-sucedida. Caso contrário, se o registro de data e hora "retreinado" não foi atualizado, há uma explicação incluída na resposta que informa a razão pela qual o retreinamento falhou e o serviço reverterá o classificador para a versão que havia antes de a solicitação de retreinamento ser emitida.

### 20 de maio de 2016
{: #20 may 2016}

Esta é a liberação de Disponibilidade Geral do serviço {{site.data.keyword.visualrecognitionshort}}. Esta liberação introduz a Versão 3 do serviço e é uma mudança significativa. Esta liberação incorpora a funcionalidade do serviço AlchemyVision, que foi descontinuado.

Os classificadores customizados que foram criados enquanto o serviço estava em Beta devem ser recriados em uma instância GA do serviço.

As mudanças e atualizações a seguir foram feitas no serviço {{site.data.keyword.visualrecognitionshort}}:

- **Data da versão:** para utilizar os recursos desta liberação, use `2016-05-20` como o valor para o parâmetro `version`.
- **Classes e classificadores:** os classificadores únicos são agora chamados "classes". Em GA, um grupo de classes é chamado de "classificador".
- **Classificação:** use os métodos `POST` ou `GET /v3/classify` para identificar de forma rápida e precisa uma variedade de assuntos e cenários com classes padrão.
- **Detecção facial:** use os métodos `POST` ou `GET /v3/detect_faces` para detectar faces em imagens e obter informações sobre elas, como onde a face está localizada na imagem, a faixa etária estimada e o sexo de cada face. O serviço também pode identificar muitas celebridades por nome e pode fornecer um gráfico de conhecimento para que você possa executar agregações interessantes em conceitos de nível mais alto.
- **Classificadores customizados com múltiplas máscaras:** agora é possível criar e treinar classificadores altamente especializados que são definidos por várias classes. Por exemplo, é possível criar um classificador "new\_red\_car" que é definido pelas classes "new\_cars" e "red\_cars". Para saber mais sobre como criar classificadores com diversas máscaras, veja [Estrutura dos dados de treinamento](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure).
- **Treinamento assíncrono:** o treinamento de classificadores customizados é agora assíncrono, então as chamadas de treinamento são concluídas rapidamente enquanto seu classificador customizado continua a aprender no segundo plano. Para verificar o status de treinamento de seu classificador customizado e descobrir quando ele está disponível para uso, chame o método `GET /v3/classifiers/{classifier_id}` e verifique o parâmetro de resposta `status`.

### 2 de dezembro de 2015
{: #2december2015}

A liberação mais nova do serviço {{site.data.keyword.visualrecognitionshort}} é uma mudança significativa que introduz uma nova versão da API do {{site.data.keyword.visualrecognitionshort}} (v2). A Versão 1 do serviço {{site.data.keyword.visualrecognitionshort}} está disponível para uso até que o serviço saia do beta.

Para começar a usar imediatamente a versão 2 da API, entenda e atualize seu código para refletir essas mudanças:

- Na versão 1 do serviço, você analisou imagens por rótulos. Na versão 2 do serviço, os rótulos são chamados **classificadores**. Os classificadores têm um ID de classificador exclusivo indicado pelo parâmetro `classifier_id` e um nome abreviado indicado pelo parâmetro `name`.
- O método `POST /v1/recognize` para analisar uma imagem é agora o método [`POST /v2/classify` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window}. O parâmetro `labels_to_check` é renomeado para `classifier_ids`.
- O método `GET /v1/tag/labels` para recuperar uma lista de rótulos na V1 é agora o método [`GET /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} para recuperar uma lista de classificadores.
- Além de recuperar uma lista de classificadores, também é possível recuperar detalhes para um classificador específico com o novo método [`GET /v2/classifiers/{classifier_id}` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window}.
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta permite que você crie classificadores customizados com o novo método [`POST /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window}. Para saber mais sobre como criar classificadores customizados, veja [Criando classificadores customizados](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta também permite excluir classificadores customizados com o novo método [`DELETE /v2/classifiers` ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window}.
- A Versão 2 da API do {{site.data.keyword.visualrecognitionshort}} beta requer o parâmetro `version`. Especifique a data de liberação da versão da API que você deseja usar no formato `MM-DD-YYYY`.
