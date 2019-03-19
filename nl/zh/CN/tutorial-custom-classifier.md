---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: custom model,custom classifier,samples,training a custom model

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
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# 创建定制模型
{: #tutorial-custom-classifier}

在“入门教程”中分析图像后，即可开始训练并创建定制模型。使用定制模型，可以训练 {{site.data.keyword.visualrecognitionshort}} 服务，以根据您的业务需求对图像进行分类。
{: shortdesc}

## 步骤 1：复制凭证
{: #copy-credentials}

使用您在“入门教程”中复制的凭证。如果没有创建服务实例，请执行[开始之前](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites)部分中的那些步骤。

## 步骤 2：创建定制模型
{: #create}

{{site.data.keyword.visualrecognitionshort}} 可以通过上传的示例图像进行学习，从而创建新的多构面模型。每个示例文件都会根据该调用中的其他文件进行训练，并且正面示例会存储为类。这些类分组后可定义单个模型，并返回其自己的分数。负面示例文件不会存储为类。

1.  下载 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a>、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 和 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 示例训练文件。
1.  使用以下命令调用 `POST /v3/classifiers` 方法，此方法用于上传训练数据并创建 `dogs` 定制模型：
    - 将 `{your_api_key}` 替换为在第一步中复制的服务凭证。
    - 修改 `{class}_positive_examples` 的位置，使其指向 .zip 文件的保存位置。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "beagle_positive_examples=@beagle.zip" \
    --form "husky_positive_examples=@husky.zip" \
    --form "goldenretriever_positive_examples=@golden-retriever.zip" \
    --form "negative_examples=@cats.zip" \
    --form "name=dogs" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
    ```
    {: pre}

    正面示例文件名需要后缀 `_positive_examples`。在此示例中，文件名为 `beagle_positive_examples`、`goldenretriever_positive_examples` 和 `husky_positive_examples`。前缀（beagle、goldenretriever 和 husky）作为类名返回。
    {:tip }

    响应包含新的分类器标识和状态，例如：

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "training",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
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
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

1.  定期检查训练状态，直到看到 `ready` 状态。训练会立即开始，并且必须完成后，才能查询模型。将 `{your_api_key}` 和 `{classifier_id}` 替换为您的信息：

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 步骤 3：更新现有定制模型
{: #tutorial-custom-classifier-update}

可以通过向模型添加类或向现有类添加图像来更新定制模型。在此，通过将 *Dalmatian* 类添加到可分类的狗类型，可改进在步骤 2 中创建的模型。您还可以将猫的图像添加到“dogs”定制模型的负面示例集。

1.  下载 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 和 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 样本训练文件。
1.  使用以下 curl 命令调用 `POST /v3/classifiers/{classifier_id}` 方法，此方法用于上传训练数据并更新“dogs\_1941945966”定制模型：
    - 将 `{your_api_key}` 替换为在第一步中复制的服务凭证。
    - 将 `{classifier_id}` 替换为要更新的定制模型的标识。
    - 修改 `{class}_positive_examples` 的位置，使其指向 .zip 文件的保存位置。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    现有“dogs”定制模型替换为具有相同 classifier_id 但经过重新训练的模型。响应会列出一组新类及其当前状态。例如：

    ```json
    {
      "classifier_id": "dogs_1941945966",
      "name": "dogs",
      "status": "retraining",
      "owner": "xxxx-xxxxx-xxx-xxxx",
      "created": "2018-03-17T19:01:30.536Z",
      "updated": "2018-03-17T19:01:30.536Z",
      "classes": [
        {
          "class": "husky"
        },
        {
          "class": "goldenretriever"
        },
        {
          "class": "beagle"
        },
        {
          "class": "dalmatian"
        }
      ],
      "core_ml_enabled": true
    }
    ```
    {: codeblock}

    训练会立即开始。新分类器可用后，状态会更改为 `ready`。

    在当前状态变为 `ready` 前，不要发出其他重新训练请求。即便发出多个模型重新训练请求，也只会执行一次重新训练。名为 `updated` 的时间戳记显示最近更新模型的时间。如果在模型正在重新训练期间调用 `/classify` 方法，那么将使用模型的旧定义。
    {: tip}
1.  定期检查训练状态，直到看到 `ready` 状态。将 `{your_api_key}` 和 `{classifier_id}` 替换为您的信息：

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 步骤 4：使用定制模型对图像分类
{: #tutorial-custom-classifier-classify}

在新模型准备就绪后，调用该模型以查看其表现情况。

1.  下载 <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a>。
1.  使用 `POST /v3/classify` 方法来测试定制模型。以下示例根据“dogs\_1941945966”定制模型和内置 `default`“通用”模型对 `dogs.jpg` 图像分类：
    - 将 `{your_api_key}` 替换为在第一步中复制的服务凭证。

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    要仅根据内置“通用”模型进行分类，请省略 `classifier_ids` 参数。
    {: tip}

    响应包括分类器（模型）、其类以及每个类的分数。分数范围为 0-1，分数越高，表示相关性越大。缺省情况下，如果识别到高分数的类，`/v3/classify` 调用会省略低分数的类。可以通过在调用中指定 `threshold` 参数的浮点值来设置要显示的最低分数。

    ```json
    {
      "images": [
        {
          "classifiers": [
            {
              "classifier_id": "dogs_1941945966",
              "name": "dogs",
              "classes": [
                {
                  "class": "goldenretriever",
                  "score": 0.513638
                }
              ]
            },
            {
              "classifier_id": "default",
              "name": "default",
              "classes": [
                {
                  "class": "guide dog",
                  "score": 0.86,
                  "type_hierarchy": "/animal/domestic animal/dog/guide dog"
                },
                {
                  "class": "dog",
                  "score": 0.927
                },
                {
                  "class": "domestic animal",
                  "score": 0.927
                },
                {
                  "class": "animal",
                  "score": 0.927
                },
                {
                  "class": "beagling (dog)",
                  "score": 0.508,
                  "type_hierarchy": "/animal/domestic animal/dog/beagling (dog)"
                },
                {
                  "class": "golden retriever dog",
                  "score": 0.5,
                  "type_hierarchy": "/animal/domestic animal/dog/retriever dog/golden retriever dog"
                },
                {
                  "class": "retriever dog",
                  "score": 0.572
                },
                {
                  "class": "light brown color",
                  "score": 0.982
                }
              ]
            }
          ],
          "image": "dogs.jpg"
        }
      ],
      "images_processed": 1,
      "custom_classes": 1
    }
    ```
    {: codeblock}

1.  复查结果。

完成！您已使用 {{site.data.keyword.visualrecognitionshort}} 创建、训练和查询定制模型。

### 删除定制模型
{: #tutorial-custom-classifier-delete}

您可能希望删除定制模型，以便使用干净的实例开始开发应用程序。

要删除模型，请调用 `DELETE /v3/classifiers/{classifier_id}` 方法。将 `{your_api_key)` 和 `classifier_id` 替换为您的信息：

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## 后续步骤
{: #tutorial-custom-classifier-next-steps}

既然您已经对如何使用定制模型有了基本了解，接着可以更深入地探索以下内容：

- 
了解有关[定制分类器最佳做法 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window} 的更多信息。
- 阅读 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition){: new_window} 中有关 API 的信息。

### 出处
{: #tutorial-custom-classifier-attributions}

此页面上使用的所有图像均来自 Flikr，并依据 [Creative Commons Attribution 2.0 许可证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 使用。这些图像未进行任何更改。
