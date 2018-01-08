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

# 创建定制分类器

在“入门教程”中对图像进行分类后，即可开始培训并创建定制分类器（或模型）。使用定制分类器，可以培训 {{site.data.keyword.visualrecognitionshort}} 服务，以根据您的业务需求对图像进行分类。
{: shortdesc}

## 步骤 1：复制凭证
{: #copy-credentials}

使用您在“入门教程”中复制的凭证。如果没有创建服务实例，请执行[开始之前](/docs/services/visual-recognition/getting-started.html#prerequisites)部分中的那些步骤。

## 步骤 2：创建定制分类器
{: #create}

{{site.data.keyword.visualrecognitionshort}} 可以通过上传的示例图像进行学习，从而创建新的多构面分类器。每个示例文件都会根据该调用中的其他文件进行培训，并且正面示例会存储为类。这些类分组后可定义单个分类器，并返回其自己的分数。负面示例文件不会存储为类。

1.  下载 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 和 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 示例培训文件。
1.  使用以下命令调用 `POST /v3/classifiers` 方法，此方法用于上传培训数据并创建 `dogs` 分类器：
    - 将 `{api-key}` 替换为第一步中复制的服务凭证。
    - 修改 `{class}_positive_examples` 的位置，使其指向 .zip 文件的保存位置。

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

    正面示例文件名需要后缀 `_positive_examples`。在此示例中，文件名为 `beagle_positive_examples`、`goldenretriever_positive_examples` 和 `husky_positive_examples`。前缀（beagle、goldenretriever 和 husky）作为类名返回。
    {:tip }

    响应包含新的分类器标识和状态，例如：

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
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

1.  定期检查培训状态，直到看到 `ready` 状态。培训会立即开始，并且必须完成后，才能查询分类器。将 `{api  key}` 和 `{classifier_id}` 替换为您的信息：

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 步骤 3：更新现有定制分类器

不能使用免费 API 密钥来更新定制分类器。如果你拥有的是免费密钥，可以升级到标准套餐。有关详细信息，请参阅[更改套餐](https://console.bluemix.net/docs/pricing/changing_plan.html)。
{: tip}

可以通过向分类器添加类或向现有类添加图像来更新定制分类器。在此，通过将*斑点狗*类添加到可分类的狗类型，可改进在步骤 2 中创建的分类器。您还可以将猫的图像添加到“dogs”分类器的负面示例集。

1.  下载 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 和 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 样本培训文件。
1.  使用以下 curl 命令调用 `POST /v3/classifiers/{classifier_id}` 方法，此方法用于上传培训数据并更新“dogs\_1941945966”分类器：
    - 将 `{api-key}` 替换为第一步中复制的服务凭证。
    - 将 `{classifier_id}` 替换为要更新的分类器的标识。
    - 修改 `{class}_positive_examples` 的位置，使其指向 .zip 文件的保存位置。

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    现有“dogs”分类器替换为具有相同 classifier_id 但经过重新培训的分类器。响应会列出一组新类及其当前状态。例如：

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
          "class": "beagle"
        }
      ]
    }
    ```
    {: codeblock}

    培训会立即开始。新分类器可用后，状态会更改为 `ready`。

    在当前状态变为 `ready` 前，不要发出其他重新培训请求。即便发出多个分类器重新培训请求，也只会执行单个重新培训请求。名为 `retrained` 的时间戳记会显示上次完成分类器重新培训的时间。如果在分类器正在重新培训期间调用 `/classify` 方法，那么将使用分类器的旧定义。
    {: tip}
1.  定期检查培训状态，直到看到 `ready` 状态。将 `{api  key}` 和 `{classifier_id}` 替换为您的信息：

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 步骤 4：使用定制分类器对图像分类
{: #classify}

在新分类器准备就绪后，调用该分类器以查看其执行情况。

1.  创建名为 `myparams.json` 的 JSON 文件，该文件包含用于调用的参数，例如新分类器和通用模型分类器（使用 `default` classifier_id）的 `classifier_id`。简单的 JSON 文件类似于以下内容：

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  下载 <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a>。
1.  使用 `POST /v3/classify` 方法来测试定制分类器。以下示例根据“dogs\_1941945966”分类器对 `dogs.jpg` 图像分类：
    - 将 `{api-key}` 替换为第一步中复制的服务凭证。

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    要仅根据内置通用模型分类，请省略 `parameters` 参数。
    {: tip}

    响应包括分类器、分类器的类以及每个类的分数。分数范围为 0-1，分数越高，表示相关性越大。缺省情况下，如果识别到高分数的类，`/v3/classify` 调用会省略低分数的类。可以通过在调用中指定 `threshold` 参数的浮点值来设置要显示的最低分数。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
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
              "classes": [
                {
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
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

1.  复查结果。

完成！您已使用 {{site.data.keyword.visualrecognitionshort}} 创建、培训和查询定制分类器。

### 删除定制分类器

您可能希望删除定制分类器，以便使用干净的实例开始开发应用程序。

要删除分类器，请调用 `DELETE /v3/classifiers/{classifier_id}` 方法。将 `{api-key}` 和 `classifier_id` 替换为您的信息：

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## 后续步骤

现在，您已经对如何使用定制分类器有了基本的了解，接着可以更深入地探索以下内容：

- 
了解有关[定制分类器最佳做法 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window} 的更多信息。
- 阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window} 中有关 API 的信息。

### 出处
{: #attributions}

此页面上使用的所有图像均来自 Flikr，并依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。这些图像未进行任何更改。
