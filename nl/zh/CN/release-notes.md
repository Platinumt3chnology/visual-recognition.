---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

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

# 发行说明
{: #release-notes}

下面是服务可用的新功能和更改。
{: shortdesc}

## 服务 API 版本控制
{: version}

API 请求需要采用日期的 version 参数，格式为 `version=YYYY-MM-DD`。每当我们以向后不兼容方式更改 API 时，都会发布该 API 的新的次版本。

随每个 API 请求一起发送 version 参数。服务会使用您指定日期的 API 版本，或该日期之前的最新版本。不要缺省使用当前日期。而是改为指定与兼容您应用程序的版本相匹配的日期，并使其保持不变，直到应用程序准备好用于更高版本。

当前版本为 `2018-03-19`。

## Beta 功能
{: #beta}

{{site.data.keyword.IBM_notm}} 发布的供您评估的服务、功能和语言支持分类为 Beta。这些功能可能不稳定、会频繁更改，也可能会临时通知停止使用。此外，Beta 功能提供的性能和兼容性水平可能与一般可用功能提供的不同，并且不适用于生产环境。仅在 [IBM Developer Answers ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} 上支持 Beta 功能。

## 更改
{: #changelog}

下面是服务可用的新功能和更改。

### 2019 年 1 月 15 日
{: #15january2019}

- **“检测人脸”中性别的翻译**
    - 现在，当您在 **Accept-Language** 请求头中提供语言时，**Detect Faces** 方法会返回“Male”和“Female”的翻译标签。有关详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}。

### 2018 年 10 月 1 日
{: #01october2018}

- **删除了在 2018 年 5 月 23 日之前创建的服务实例。**

    - 如先前所通知，2018 年 5 月 23 日之前创建的所有 {{site.data.keyword.visualrecognitionshort}} 实例不再处于活动状态。现在删除了实例的数据。请参阅[迁移](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)以获取有关如何移至新服务实例的详细信息。
    - 在此日期之后创建的服务实例不受影响。
    - 如果有任何问题，请联系 [IBM 支持 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/ibmcloudsupport){: new_window}。

### 2018 年 8 月 1 日
{: #01august2018}

- **“食品”和“露骨”模型的一般可用性**

    “食品”和“露骨”模型已从 Beta 移至一般可用性 (GA)。“食品”模型识别的食品和食材比“通用”（缺省）模型多。“露骨”模型识别哪些内容可能会视为色情图像。

    无需更改代码。这两个模型在轻量套餐下免费，在标准套餐下每个图像 0.002 美元。

    有关更多信息，请参阅 <em>Watson 博客</em>中的 [Updates to Watson Visual Recognition ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/visrec-price-reduction){: new_window}。

### 2018 年 7 月 1 日
{: #01july2018}

- **定制模型的新定价**
    - 自 2018 年 7 月 1 日起，使用定制模型对图像分类比之前的费率便宜一半，现在为每个图像 0.002 美元。有关详细信息和其他重要信息，请参阅 <em>Watson 博客</em>中的 [Updates to Watson Visual Recognition \- Price reduction for Custom Classification ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/visrec-price-reduction){: new_window}。

### 2018 年 6 月 21 日
{: #21june2018}

- **其他语言支持**

    - 现在，**Classify** 方法在 `default`（通用）模型类的输出中支持简体中文、繁体中文和巴西葡萄牙语。有关语言的完整列表，请参阅[受支持的语言](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)。
    - **食品**和**露骨**模型的响应中现在也支持所有语言。


### 2018 年 5 月 22 日
{: #22may2018}

- **新的 API 认证过程**：

    现在，在新端点使用 Identity and Access Management (IAM) 进行认证：

    - 将不同端点 URL 用于新实例。缺省端点为 `https:/gateway.watsonplatform.net/visual-recognition/api/`。要查找服务实例的 URL，请通过从 {{site.data.keyword.cloud_notm}} [仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/dashboard/apps?watson){: new_window} 单击该实例来检查凭证。
    - 修改向 API 进行认证的方式。针对服务实例提供 IAM 密钥或访问令牌。请参阅[迁移](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)以获取示例。

    对于 2018 年 5 月 23 日之前创建的服务实例，认证过程和端点不变。通过提供 `api_key` 查询参数进行认证。

- **对轻量套餐的更新**

    2018 年 5 月 22 日之后创建的轻量套餐发生更改：

    - 如果每个月都使用，那么新的轻量套餐实例在 30 天后继续可用。
    - 您可以在新轻量套餐下创建和重新训练两个定制模型。
    - 轻量套餐每月最多包含 1,000 个事件。针对分类、检测或训练发送的每个图像是一个事件。下载核心 ML 模型不计入事件限制。

    如果需求超出轻量套餐，请更新到计费帐户。[探索 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} 价格套餐。

- **信息安全**：

    我们更新了文档以包含一些有关数据隐私的新的详细信息。请阅读[信息安全](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security)中的详细信息。

### 2018 年 4 月 12 日
{: #12april2018}

- **支持在轻量套餐中重新训练定制模型**

    在轻量套餐下，当您想要更新或重新训练模型时，不再需要删除并创建另一个定制模型。现在，只要保持在套餐的每日和每月[限制](https://console.bluemix.net/catalog/services/visual-recognition)内，即可更新定制模型。

    如果需要多个模型或同一模型的多个版本，请从轻量套餐更新到计费帐户。

- **支持 CORS 的新的次版本**

    **版本：**`2018-03-19`

    现在，在请求中指定 `version=2018-03-19` 时支持“跨源资源共享”(CORS) 头。

### 2018 年 4 月 5 日
{: #5april2018}

- **修复“人脸”模型评分问题**

  “人脸”模型中的年龄评分的范围复原为原始范围 0 到 1。有关详细信息，请参阅 2018 年 4 月 2 日的[已知问题](#2april2018)。

- **新的 form-data 参数**

    **Classify images** 和 **Detect faces in images** 方法支持新的 form-data 参数。“图像分类”支持单独的 `url`、`classifier_ids`、`threshold` 和 `owners` 参数，“检测人脸”支持 `url`。

    过去，您需要在 JSON 字符串中对值进行编码并传递 **parameters** form-data 参数。可以使用新方法在单独的 form-data 参数中传递这些值以用于所有应用程序开发。有关详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition){: new_window}。

### 2018 年 4 月 2 日
{: #2april2018}

- **增强型“人脸”模型的一般可用性**

    更新的人脸检测模型现在具备一般可用性 (GA)。

    此增强型模型使用更广泛的训练数据集以提高人脸检测在年龄和性别方面的准确性。例如，通过减小 `min` 和 `max` 之间的范围，改进了年龄预测。先前模型中固定的 9 年年龄范围替换为动态的更小范围。平均年龄范围现在为 4.9 年。

    - 对 API 的更改

    增强型和先前“人脸”模型之间的其他差异：
        - 增强型模型支持 .gif 和 .tif 图像格式。
        - 增强型模型支持更大的文件大小：图像文件最大为 10 MB，.zip 文件最大为 100 MB。
        - 增强型模型不在响应中包含 `FaceIdentity` 信息。身份信息是指人员的 `name`、`score` 和 `type_hierarchy` 知识图。

    有关 API 的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}。

    - 已知问题

        - 表单参数不能包含 **Content-Type**。例如，以下请求无法分析 **url** 参数，因为它包含 `;type=text/plain`：

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - 年龄评分范围为 0 到 0.3。我们正在设法恢复原始范围 0 到 1。

    - 不推荐使用 Beta 端点

    不推荐使用 `/v3/detect_faces_beta` 处的 Beta 端点，并且在 2018 年 5 月 17 日后将无法访问。确保请求指向 `/v3/detect_faces`。

### 2018 年 3 月 20 日
{: #20march2018}

- **集成 Apple Core ML**

    {{site.data.keyword.visualrecognitionshort}} 现在包含针对 Apple Core ML 模型格式的支持。您可以在 iOS 应用程序上使用 {{site.data.keyword.visualrecognitionshort}} 模型的 Core ML 版本。

    **开始开发**：要使用 {{site.data.keyword.visualrecognitionshort}} 和 Core ML 开始开发，请检查 GitHub 上的这些项目：

    - 在本地对图像分类：[{{site.data.keyword.visualrecognitionshort}} with Core ML ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}。
    - 将 {{site.data.keyword.discoveryfull}} 与结果相集成：[{{site.data.keyword.visualrecognitionshort}} and Discovery with Core ML ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}。
    - 探索 SDK：[Swift SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}。

- **对 API 的更改**

    集成中包含对 API 的以下向后兼容性更改：

    - 新的 `core_ml_enabled` 字段，指示是否可将分类器模型下载为 Core ML 模型。在 `GET and POST /v3/classifiers` 和 `GET /v3/classifiers/{classifier_id}` 调用的响应中将返回该字段。
    - 新的 `GET /v3/classifiers/{classifier_id}/core_ml_model` 方法，用于将 Core ML 模型下载为 .mlmodel 文件。您可以针对 3 月 19 日之后创建的定制模型下载 Core ML 模型文件。
    - 新的 `updated` 字段，包含模型的最新训练日期。`updated` 字段匹配 `retrained` 字段或 `created` 字段。

    有关针对 Core ML 的 API 更改的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}。

- **可用的新工具：Watson Studio**

    [Watson Studio ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} 是新的集成环境，其中包含 Beta {{site.data.keyword.visualrecognitionshort}} 工具的替代项。Watson Studio 不仅支持 {{site.data.keyword.visualrecognitionshort}}，而且还支持大量其他 {{site.data.keyword.cloud_notm}} 服务和资源。您可以将 Watson Studio 与所有现有 {{site.data.keyword.visualrecognitionshort}} 实例和分类器一起使用。

     Watson Studio 在云中提供一个协作环境。利用 Watson Studio，开发者、主题专家、数据研究员和其他人员可构建和训练 {{site.data.keyword.visualrecognitionshort}} 以及其他 AI 模型。您还可以使用 Watson Studio 来访问内置“通用”和“人脸”模型。

     Watson Studio 还支持 Core ML。您可以针对定制模型下载 Core ML 模型文件。

    [开始使用 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} Watson Studio。

- **更新了定制模型的深度学习体系结构**

    {{site.data.keyword.visualrecognitionshort}} 现在使用更快且更高效的深度学习网络体系结构来进行分类。更新的模型还能够更明确区分顶级类和其他类。此方法可能导致训练时间略长。将使用新的体系结构来训练新的定制模型。在重新训练现有旧模型时，将使用原始体系结构。

    以下示例显示与新体系结构的差异：

    ![弓箭手射箭。Annie Spratt 在 Unsplash 上发布的照片](images/archery.jpg)

    <table>
      <tr>
        <th>原始类和分数</th>
        <th>更新的类和分数</th>
      </tr>
      <tr>
        <td>Archery</br>0.99 </td>
        <td><strong>archery<strong></br>0.9</td>
      </tr>
      <tr>
        <td>Auto Racing</br>0.996398</td>
        <td><strong>biking</strong></br>0.004</td>
      </tr>
      <tr>
        <td>Biking</br>0.0500174</td>
        <td><strong>fishing</strong></br>0.001</td>
      </tr>
      <tr>
        <td>Fishing</br>0.11029</td>
        <td><strong>golf</strong></br>0.031</td>
      </tr>
      <tr>
        <td>Golf</br>0.0980796</td>
        <td><strong>gymnastics</strong></br>0.029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0.964391</td>
        <td><strong>judo</strong></br>0.021</td>
      </tr>
      <tr>
        <td>Judo</br>0.339119</td>
        <td><strong>racing</strong></br>0.002</td>
      </tr>
      <tr>
        <td>Skating</br>0.0393602</td>
        <td><strong>skating</strong></br>0.061</td>
      </tr>
      <tr>
        <td>Skiing</br>0.0310527</td>
        <td><strong>skiing</strong></br>0.003</td>
      </tr>
      <tr>
        <td>Track and Field</br>0.208147</td>
        <td><strong>track</strong></br>0.035</td>
      </tr>
    </table>

- **法语语言支持**

    现在，**Classify** 方法在 `default` 模型类的输出中支持法语。有关语言的完整列表，请参阅[受支持的语言](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)。

### 2018 年 2 月 23 日
{: #23february2018}

- **Beta 中提供了增强型“人脸”模型**

    提供了更新的人脸检测模型。此 Beta 模型使用更广泛的训练数据集以提高人脸检测在年龄和性别方面的准确性。有关更多信息，请参阅 [Increasing the Accuracy of IBM’s Watson {{site.data.keyword.visualrecognitionshort}} service ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} 和 [Mitigating Bias in AI Models ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}。

    - 您可以在[演示 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/services/visual-recognition/demo){: new_window} 和 Beta [Visual Recognition Tool ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} 中查看更新的模型的结果。
    - Beta 模型位于 `/v3/detect_faces_beta`。

    Beta 和一般可用性 (GA) 模型之间的差异：
    - Beta 模型支持 .gif 和 .tif 图像格式；此增强功能预期将应用于 GA 模型。
    - Beta 模型支持更大的文件大小：图像文件最大为 10 MB，.zip 文件最大为 100 MB。此增强功能预期将应用于 GA 模型。
    - Beta 人脸检测不在响应中包含 `FaceIdentity` 信息。
    - Beta 模型的 POST 请求需要非空文件名。GA“人脸”模型不强制实施此约束。
    - Beta 模型的 POST 请求支持名为 `url` 的单独的表单参数。GA 模型将该信息包含在 `parameters` JSON 对象中。有关详细信息，请参阅 [API reference ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-api-explorer.mybluemix){: new_window}。

- **不推荐使用人脸身份**

    不推荐使用 GA“人脸”模型的响应中的身份信息，并且将于 **2018 年 4 月 2 日**从 API 中除去。身份信息是指人员的 `name`、`score` 和 `type_hierarchy` 知识图。

### 2018 年 1 月 16 日
{: #16january2018}

- **轻量帐户和套餐将替换免费套餐**

    轻量帐户免费；无需信用卡。但是，轻量套餐服务实例将在 30 天后删除。

    使用轻量套餐可进行的 API 调用的最大数量与免费套餐略有不同。在轻量套餐中，每月最多可进行 7,500 次 API 调用，每天最多 250 次调用。

    要在使用定制分类器时更新为计费帐户，请创建另一个服务实例，然后重新创建定制分类器。

### 2017 年 12 月 11 日
{: #11december2017}

<ul>
  <li>
    <strong>利用通用模型来提高准确性和输出</strong>
      <p>
        现在，包含数千个标记的通用模型可以检测到更多辅助对象，并提高了场景检测水平。这些改进有助于识别图像中不太突出的方面。此外，每个图像返回的平均标记数增加到了 10 个。
      </p>
      <p>
        下图显示更新之前返回的标记示例和现在返回的更多标记的示例。
      </p>
      <img src="images/tree-flower.jpg" alt="杜鹃花植物的照片">
      <table>
        <tr>
          <th>原始标记</th>
          <th>更多标记</th>
        </tr>
        <tr>
          <td></td>
          <td>
          标记：tree<br/>
          分数：0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          标记：flower<br/>
          分数：0.792</td>
        </tr>
        <tr>
          <td>
          标记：alpine azalea<br/>
          分数：0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          标记：plant<br/>
          分数：0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          标记：azalea<br/>
          分数：0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            标记：swamp azalea<br/>
          分数：0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            标记：reddish orange color<br/>
          分数：0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Beta 中新增“露骨”模型</strong>
      <p>
        Beta 版本中发布的“露骨”模型用于确定是否将图像分类为色情内容，不适合一般用途。可以将“露骨”模型与其他模型一起用于进行组合分析。例如，在请求中同时包含 `default` 和 `explicit` 分类器标识可返回图像标记，以及确定图像是否包含露骨内容。
      <p>
有关 API 调用的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#classify-images) 中的**图像分类**方法。</p>
    </li>
    <li>
      <strong>支持更大的文件大小</strong>
      <p>
        现在，<strong>Classify images</strong> 方法支持的最大图像文件为 10 MB，最大 .zip 文件为 100 MB。
    </li>
    <li>
      <strong>传递分类器标识时需要数组</strong>
      <p>
        现在，将 `classifier_ids` 作为 **Classify images** 方法中的**参数**对象的一部分传入时，API 会强制使用数组。先前，可以将分类器标识作为字符串传递。有关更多信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#classify-images) 中的参数描述和示例文件。
      </p>
    </li>
</ul>

### 2017 年 9 月 8 日
{: #8september2017}

- **Beta 相似度搜索和集合已结束**：截至 2017 年 9 月 8 日，“相似度搜索”的 beta 期间已结束。有关更多信息，请参阅 [Visual Recognition API - Similarity Search Update ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}。

### 2017 年 6 月 30 日
{: #30june2017}

- **改进了标记**：我们增加了缺省分类器的训练图像数量。训练图像数量的增加提高了准确识别图像整体“场景”的能力。有关详细信息，请参阅 [Further Enhancements for General Tagging Feature ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **更多语言**：现在，除了英语、阿拉伯语、西班牙语和日语外，**Classify images** 方法还支持韩语、意大利语和德语。

    有关 API 调用的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window} 中的 **Classify an image** 方法。

### 2017 年 5 月 16 日
{: #16may2017}

- **新增食品分类器：Beta**

    新的 Beta 食品识别模型增强了食品项图像的特征和准确性。**Classify an image** 方法支持将新分类器“food”添加到 `classifier_ids` 参数。

### 2017 年 4 月 5 日
{: #5april2017}

- **新增 {{site.data.keyword.visualrecognitionshort}} 工具：Beta**

    在 [https://watson-visual-recognition.ng.bluemix.net/ ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} 上提供了新的 Beta 功能 {{site.data.keyword.visualrecognitionshort}} 工具。此工具有助于您更轻松地使用 {{site.data.keyword.visualrecognitionshort}} 服务。您可以在 GUI 中，通过输入 {{site.data.keyword.cloud_notm}} API 密钥来访问“通用标记”和“人脸检测”功能，还可以无缝地创建、重新训练和删除与 API 密钥关联的定制分类器，而无需进行编码。

### 2017 年 3 月 8 日
{: #8march2017}

- **更新了对通用分类器标记的语言支持**

    现在，通用分类器可返回所有受支持语言的标记。

- **已知问题**

    **2017 年 4 月 13 日已修订**：在训练或重新训练过程中反复调用 `GET /classifiers` 来检查状态，这可能导致训练作业终止。要解决此问题，请使用 `GET /classifiers/{classifier_id}` 来轮询新分类器的状态。换句话说，使用分类器 `GET` 而不是 `GET /classifiers` 来获取单个分类器标识，后者会获取所有分类器，从而触发此问题。请注意，`GET /classifiers/{classifier_id}` 的运行速度也更快。

### 2016 年 12 月 15 日
{: #15december2016}

- **改进了通用分类器标记**

    - 更新了通用分类器的深度学习算法。所有语言的标记质量都有显著改进，并且服务返回的英文标记量大大增加。创建自己的定制分类器时，也可以使用此高质量标记输出。
    - 添加了颜色标记。现在，服务可返回图像中最多的一种或两种颜色。

- **已知问题**

    - 提交给演示的具有 EXIF 元数据标记的图像未对服务正确指定方向（横向和纵向）。iPhone 上传的图像可能包含 EXIF 元数据标记。解决此问题的变通方法是更新图像元数据，使其不依赖于 EXIF 元数据标记来指定图像方向。通常，只需在计算机上打开图像并保存即可解决此问题。例如，在 Mac 上，在“预览”中打开并保存图像，即可设置正确的方向标记。
    - 将具有 [EXIF 标记 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://en.wikipedia.org/wiki/Exif){: new_window} 值 8、3 或 6 的图像发送给 {{site.data.keyword.visualrecognitionshort}} 服务可能会增加等待时间。该服务会将图像的像素旋转到编码的视图点。您可以通过预先旋转图像，或者删除对 {{site.data.keyword.visualrecognitionshort}} 任务不重要的 EXIF 头来节省时间。

### 2016 年 12 月 1 日
{: #1december2016}

- **新定价**

    {{site.data.keyword.IBM_notm}} 降低了 {{site.data.keyword.visualrecognitionshort}} 服务上定制分类器的价格，并增加了免费套餐中的可用分类器。有关更多信息，请参阅 [{{site.data.keyword.visualrecognitionshort}} 定价](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)页面。

### 2016 年 10 月 7 日
{: #7october2016}

- **增强了人脸检测功能**

    服务采用新的人脸检测算法，改进了 `GET` 和 `POST /v3/detect_faces` 方法的响应。该服务调整了对低置信度的年龄、姓名和性别人脸检测的过滤。因此，可以找到更多的人脸，并返回更大范围的置信度。

### 2016 年 9 月 8 日
{: #8september2016}

- **相似度搜索 BETA**

    现在，用户可以上传自己的图像集合，使用图像来搜索相似图像的集合，然后服务会返回前 100 个最相似的图像。相似度搜索可以用于任何目的，并且用户可以基于集合定制训练服务，每个集合最多可以有 100 万个图像。有关使用新的相似度搜索功能的更多信息，请参阅[教程](/docs/services/visual-recognition/tutorial-collections.html)和 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 页面。

- **文本识别现在为封闭 Beta 版**

    `POST` 和 `GET /v3/recognize_text` 方法已经回到封闭 Beta 版。{{site.data.keyword.IBM_notm}} 打算继续支持使用该服务的 Beta 客户机，目前尚无开发其他开放 Beta 版的计划。

### 2016 年 8 月 1 日

- **推广期定价结束**

    定制分类器训练和重新训练、定制图像分类和定制分类器存储不再免费提供。有关定价的信息，请参阅 {{site.data.keyword.visualrecognitionshort}} 服务的 [定价](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)页面。

### 2016 年 7 月 5 日
{: #5july2016}

- **更新定制分类器**

    定制分类器不再限于一组固定的训练数据。现在，用户可以使用新的图像来更新现有分类器，或者向现有已训练分类器添加其他正面或负面示例分类器。通过提供更多示例图像供 Watson 学习，该服务可以使用户的分类器更加准确。现在，定制分类器可以随时间不断学习，持续改进对视觉信息的理解。

- **已知问题**

    **2017年 4 月 13 日已修订**：更新现有分类器后，用户可能会在 30 秒或 90 秒后收到 500 错误代码。
尽管出现此错误，但重新训练请求仍有很大可能成功完成。请至少等待 2 分钟，然后使用 `GET classifiers/{classifier\_id}` 方法来检查分类器的状态。如果状态为“准备就绪”并且“重新训练时间”时间戳记已更新，说明生成 500 代码的重新训练请求成功。否则，如果“重新训练时间”时间戳记未更新，那么会向响应添加解释，说明为什么重新训练失败，并且服务会把分类器还原到发出重新训练请求之前的版本。

### 2016 年 5 月 20 日
{: #20 may 2016}

这是 {{site.data.keyword.visualrecognitionshort}} 服务的一般可用性发行版。此发行版引入了该服务的 V3 版本，并且属于重大更改。此发行版包含 AlchemyVision 服务（已弃用）的功能。

在服务处于 Beta 版本时创建的任何定制分类器都必须在服务的 GA 实例中重新创建。

对 {{site.data.keyword.visualrecognitionshort}} 服务进行了以下更改和更新：

- **版本日期**：要利用此发行版的功能，请使用 `2016-05-20` 作为 `version` 参数的值。
- **类和分类器**：现在，单个分类器称为“类”。在 GA 中，一组类称为“分类器”。
- **分类**：使用 `POST` 或 `GET /v3/classify` 方法及缺省类可快速、准确地识别各种主题和场景。
- **人脸检测**：使用 `POST` 或 `GET /v3/detect_faces` 方法可检测到图像中的人脸并获取有关人脸的信息，例如人脸在图像中的位置以及每张人脸的估计年龄范围和性别。该服务还可以通过姓名来识别许多名人，并且可以提供知识图，以便您可以将相关内容聚合成更高级别的概念。
- **多构面定制分类器**：现在，可以创建和训练由多个类定义的高度专业化分类器。例如，可以创建由“new\_cars”和“red\_cars”类定义的“new\_red\_car”分类器。要了解有关创建多构面分类器的更多信息，请参阅[训练数据结构](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure)。
- **异步训练**：现在，定制分类器的训练为异步执行，所以训练会快速完成，而定制分类器会在后台继续学习。要检查定制分类器的训练状态并了解其何时可用，请调用 `GET /v3/classifiers/{classifier_id}` 方法并检查 `status` 响应参数。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 服务的最新发行版属于重大更改，引入了 {{site.data.keyword.visualrecognitionshort}} API (V2) 的新版本。{{site.data.keyword.visualrecognitionshort}} V1 服务会保持可用，直到该服务退出 Beta。

要立即开始使用 API V2，请了解并更新代码以反映以下更改：

- 在 V1 服务中，是按标签分析图像。在 V2 服务中，标签称为**分类器**。分类器具有由 `classifier_id` 参数指示的唯一分类器标识以及由 `name` 参数指示的短名称。
- 现在，用于分析图像的 `POST /v1/recognize` 方法为 [`POST /v2/classify` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window} 方法。`labels_to_check` 参数已重命名为 `classifier_ids`。
- 在 V1 中用于检索标签列表的 `GET /v1/tag/labels` 方法现在为用于检索分类器列表的 [`GET /v2/classifiers` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} 方法。
- 除了检索分类器列表外，还可以使用新的 [`GET /v2/classifiers/{classifier_id}` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window} 方法来检索特定分类器的详细信息。
- Beta {{site.data.keyword.visualrecognitionshort}} API V2 支持使用新的 [`POST /v2/classifiers` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window} 方法来创建定制分类器。要了解有关创建定制分类器的更多信息，请参阅[创建定制分类器](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)。
- Beta {{site.data.keyword.visualrecognitionshort}} API V2 还支持使用新的 [`DELETE /v2/classifiers ` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window} 方法来删除定制分类器。
- B。eta {{site.data.keyword.visualrecognitionshort}} API V2 需要 `version` 参数。请使用 `MM-DD-YYYY` 格式指定要使用的 API 版本的发布日期。
