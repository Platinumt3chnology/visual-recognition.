---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-11"

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

# 发行说明

下面是服务可用的新功能和更改。
{: shortdesc}

## Beta 功能
{: #beta}

{{site.data.keyword.IBM_notm}} 发布的供您评估的服务、功能和语言支持分类为 Beta。这些功能可能不稳定、会频繁更改，也可能会临时通知停止使用。此外，Beta 功能提供的性能和兼容性水平可能与一般可用功能提供的不同，并且不适用于生产环境。仅在 [developerWorks Answers ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window} 上支持 Beta 功能。

## 更改
{: #changelog}

下面是服务可用的新功能和更改。

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
      <img src="images/antarctica-iceberg.jpg" alt="南极洲的冰山">
      <table>
        <tr>
          <th>原始标记</th>
          <th>更多标记</th>
        </tr>
        <tr>
          <td>
          标记：冰山<br/>
          分数：0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          标记：冰体<br/>
          分数：0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          标记：自然<br/>
          分数：0.770</td>
        </tr>
        <tr>
          <td>
          标记：蓝色<br/>
          分数：0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          标记：雪白色<br/>
          分数：0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Beta 中新增显式模型</strong>
      <p>
        Beta 版本中发布的显式模型用于确定是否将图像分类为色情内容，不适合一般用途。可以将显式模型与其他模型一起用于进行组合分析。例如，在请求中同时包含 `default` 和 `explicit` 分类器标识可返回图像标记，以及确定图像是否包含显式内容。
      <p>
        有关 API 调用的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image) 中的**图像分类**方法，或者在 [API Explorer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify) 中试用模型。
      </p>
    </li>
    <li>
      <strong>支持更大的文件大小</strong>
      <p>
        现在，<strong>图像分类</strong>方法支持的最大图像文件为 10 MB，最大 .zip 文件为 100 MB。
    </li>
    <li>
      <strong>传递分类器标识时需要数组</strong>
      <p>
        现在，将 `classifier_ids` 作为**图像分类**方法中的**参数**对象的一部分传入时，API 会强制使用数组。先前，可以将分类器标识作为字符串传递。有关更多信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image) 中的参数描述和示例文件。
      </p>
    </li>
</ul>

### 2017 年 9 月 8 日
{: #8september2017}

- **Beta 相似度搜索和集合已结束**：截至 2017 年 9 月 8 日，“相似度搜索”的 beta 期间已结束。有关更多信息，请参阅 [Visual Recognition API - Similarity Search Update ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}。

### 2017 年 6 月 30 日
{: #30june2017}

- **改进了标记**：我们增加了缺省分类器的培训图像数量。培训图像数量的增加提高了准确识别图像整体“场景”的能力。有关详细信息，请参阅 [Further Enhancements for General Tagging Feature ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **更多语言**：现在，除了英语、阿拉伯语、西班牙语和日语外，**图像分类**方法还支持韩语、意大利语和德语。

    有关 API 调用的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 外部链接图标中的**图像分类**方法。

### 2017 年 5 月 16 日
{: #16may2017}

- **新增食品分类器：Beta**

    新的 Beta 食品识别模型增强了食品项图像的特征和准确性。**图像分类**方法支持将新分类器“food”添加到 `classifier_ids` 参数。

### 2017 年 4 月 5 日
{: #5april2017}

- **新增 {{site.data.keyword.visualrecognitionshort}} 工具：Beta**

    在 [https://watson-visual-recognition.ng.bluemix.net/ ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-visual-recognition.ng.bluemix.net/){: new_window} 上提供了新的 Beta 功能 {{site.data.keyword.visualrecognitionshort}} 工具。此工具有助于您更轻松地使用 {{site.data.keyword.visualrecognitionshort}} 服务。您可以在 GUI 中，通过输入 {{{site.data.keyword.cloud_notm}} API 密钥来访问“通用标记”和“人脸检测”功能，还可以无缝地创建、重新培训和删除与 API 密钥关联的定制分类器，而无需进行编码。

### 2017 年 3 月 8 日
{: #8march2017}

- **更新了对通用分类器标记的语言支持**

    现在，通用分类器可返回所有受支持语言的标记。

- **已知问题**

    **2017 年 4 月 13 日已修订**：在培训或重新培训过程中反复调用 `GET /classifiers` 来检查状态，这可能导致培训作业终止。要解决此问题，请使用 `GET /classifiers/{classifier_id}` 来轮询新分类器的状态。换句话说，使用分类器 `GET` 而不是 `GET /classifiers` 来获取单个分类器标识，后者会获取所有分类器，从而触发此问题。请注意，`GET /classifiers/{classifier_id}` 的运行速度也更快。

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

    IBM 降低了 {{site.data.keyword.visualrecognitionshort}} 服务上定制分类器的价格，并增加了免费套餐中的可用分类器。有关更多信息，请参阅 [{{site.data.keyword.visualrecognitionshort}} 定价](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)页面。

### 2016 年 10 月 7 日
{: #7october2016}

- **增强了人脸检测功能**

    服务采用新的人脸检测算法，改进了 `GET` 和 `POST /v3/detect_faces` 方法的响应。该服务调整了对低置信度的年龄、姓名和性别人脸检测的过滤。因此，可以找到更多的人脸，并返回更大范围的置信度。

### 2016 年 9 月 8 日
{: #8september2016}

- **相似度搜索 BETA**

    现在，用户可以上传自己的图像集合，使用图像来搜索相似图像的集合，然后服务会返回前 100 个最相似的图像。相似度搜索可以用于任何目的，并且用户可以基于集合定制培训服务，每个集合最多可以有 100 万个图像。有关使用新的相似度搜索功能的更多信息，请参阅[教程](/docs/services/visual-recognition/tutorial-collections.html)和 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 页面。

- **文本识别现在为封闭 Beta 版**

    `POST` 和 `GET /v3/recognize_text` 方法已经回到封闭 Beta 版。IBM 期待继续支持使用该服务的 Beta 客户机，目前还没有其他公开 Beta 套餐。

### 2016 年 8 月 1 日

- **推广期定价结束**

    定制分类器培训和重新培训、定制图像分类和定制分类器存储不再免费提供。有关定价的信息，请参阅 {{site.data.keyword.visualrecognitionshort}} 服务的 [定价](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)页面。

### 2016 年 7 月 5 日
{: #5july2016}

- **更新定制分类器**

    定制分类器不再限于一组固定的培训数据。现在，用户可以使用新的图像来更新现有分类器，或者向现有已培训分类器添加其他正面或负面示例分类器。通过提供更多示例图像供 Watson 学习，该服务可以使用户的分类器更加准确。现在，定制分类器可以随时间不断学习，持续改进对视觉信息的理解。

- **已知问题**

    **2017年 4 月 13 日已修订**：更新现有分类器后，用户可能会在 30 秒或 90 秒后收到 500 错误代码。
尽管出现此错误，但重新培训请求仍有很大可能成功完成。请至少等待 2 分钟，然后使用 `GET classifiers/{classifier\_id}` 方法来检查分类器的状态。如果状态为“准备就绪”并且“重新培训时间”时间戳记已更新，说明生成 500 代码的重新培训请求成功。否则，如果“重新培训时间”时间戳记未更新，那么会向响应添加解释，说明为什么重新培训失败，并且服务会把分类器还原到发出重新培训请求之前的版本。

### 2016 年 5 月 20 日
{: #20 may 2016}

这是 {{site.data.keyword.visualrecognitionshort}} 服务的一般可用性发行版。此发行版引入了该服务的 V3 版本，并且属于重大更改。此发行版包含 AlchemyVision 服务（已弃用）的功能。

在服务处于 Beta 版本时创建的任何定制分类器都必须在服务的 GA 实例中重新创建。

对 {{site.data.keyword.visualrecognitionshort}} 服务进行了以下更改和更新：

- **版本日期**：要利用此发行版的功能，请使用 `2016-05-20` 作为 `version` 参数的值。
- **类和分类器**：现在，单个分类器称为“类”。在 GA 中，一组类称为“分类器”。
- **分类**：使用 `POST` 或 `GET /v3/classify` 方法及缺省类可快速、准确地识别各种主题和场景。
- **人脸检测**：使用 `POST` 或 `GET /v3/detect_faces` 方法可检测到图像中的人脸并获取有关人脸的信息，例如人脸在图像中的位置以及每张人脸的估计年龄范围和性别。该服务还可以通过姓名来识别许多名人，并且可以提供知识图，以便您可以将相关内容聚合成更高级别的概念。
- **多构面定制分类器**：现在，可以创建和培训由多个类定义的高度专业化分类器。例如，可以创建由“new\_cars”和“red\_cars”类定义的“new\_red\_car”分类器。要了解有关创建多构面分类器的更多信息，请参阅[培训数据结构](/docs/services/visual-recognition/customizing.html#structure)。
- **异步培训**：现在，定制分类器的培训为异步执行，所以培训会快速完成，而定制分类器会在后台继续学习。要检查定制分类器的培训状态并了解其何时可用，请调用 `GET /v3/classifiers/{classifier_id}` 方法并检查 `status` 响应参数。

### 2015 年 12 月 2 日
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 服务的最新发行版属于重大更改，引入了 {{site.data.keyword.visualrecognitionshort}} API (V2) 的新版本。{{site.data.keyword.visualrecognitionshort}} V1 服务会保持可用，直到该服务退出 Beta。

要立即开始使用 API V2，请了解并更新代码以反映以下更改：

- 在 V1 服务中，是按标签分析图像。在 V2 服务中，标签称为**分类器**。分类器具有由 `classifier_id` 参数指示的唯一分类器标识以及由 `name` 参数指示的短名称。
- 现在，用于分析图像的 `POST /v1/recognize` 方法为 [`POST /v2/classify` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 方法。`labels_to_check` 参数已重命名为 `classifier_ids`。
- 在 V1 中用于检索标签列表的 `GET /v1/tag/labels` 方法现在为用于检索分类器列表的 [`GET /v2/classifiers` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} 方法。
- 除了检索分类器列表外，还可以使用新的 [`GET /v2/classifiers/{classifier_id}` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window} 方法来检索特定分类器的详细信息。
- Beta {{site.data.keyword.visualrecognitionshort}} API V2 支持使用新的 [`POST /v2/classifiers` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window} 方法来创建定制分类器。要了解有关创建定制分类器的更多信息，请参阅[创建定制分类器](/docs/services/visual-recognition/customizing.html)。
- Beta {{site.data.keyword.visualrecognitionshort}} API V2 还支持使用新的 [`DELETE /v2/classifiers ` ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window} 方法来删除定制分类器。
- B。eta {{site.data.keyword.visualrecognitionshort}} API V2 需要 `version` 参数。请使用 `MM-DD-YYYY` 格式指定要使用的 API 版本的发布日期。
