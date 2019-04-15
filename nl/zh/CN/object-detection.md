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

# 定制对象检测 (Beta)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} 定制对象检测 (Beta) 标识图像中的项及其位置。该服务基于您提供的一组包含标记的训练数据的图像来检测这些项。
{: shortdesc}

“定制对象检测”是专用 Beta 功能，您必须具有来自 {{site.data.keyword.IBM_notm}} 的许可权才能调用此模型。[请求访问权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}。有关 Beta 功能的更多信息，请参阅[发行说明](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)。
{: important}

训练对象检测模型以识别对于您的工作流程或域很重要的对象。例如，检测汽车损坏、查找需要维护的机器或者现场执行目测。您还可以使用对象检测来统计对象数量或管理库存。

## 对象检测和分类比较
{: #obj-detect-comparison}

“定制对象检测”模型是 {{site.data.keyword.visualrecognitionshort}} 服务中的最新功能，其中包含分类。

分类和对象检测类似，但用途不同。通常，如果要预测图像中是否存在对象，请使用分类。如果要查找图像中的对象或统计其数量，请使用对象检测。

### 分类
{: #obj-detect-classify}

在对图像分类时，服务使用特定对象位于该图像中的概率进行响应。您可以使用内置模型（通用、食品或露骨），或者可创建自己的定制模型。

例如，在对 cookie 的图像（例如，以下图像）分类时，服务会以 95% 的置信度预测该图像中有 cookie。

![分类响应图像](images/cookies-tag.png "显示分类的图像")

### 对象检测
{: #obj-detect-detect}

定制对象检测类似于定制分类，但是服务会标识图像中项的位置。与分类类似，响应还包含所检测到的每个项的标签以及对该项进行识别的置信度。

检测到的项基于训练对象检测模型时提供的信息。

在以下图像中，“定制对象检测”的 **Analyze images** 方法标识图像中 cookie 的位置。每个检测到的对象都包含标签（在本例中为 `Cookie`）及其位置和置信度分数。

![对象检测响应图像](images/cookies-bbox.png "显示对象检测的图像")

## 如何使用定制对象检测
{: #object-detection-sequence}

要使用 {{site.data.keyword.visualrecognitionshort}} 定制对象检测，请遵循以下顺序的步骤来设置定制对象检测模型：

1.  创建集合：集合是图像和训练数据的容器。请参阅 V4 API 参考中的[创建集合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window}。
1.  向集合添加图像。您可以按 URL 或文件添加单个图像，或者可上传图像的 `.zip` 文件。请参阅 V4 API 参考中的[添加图像 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window}。
1.  向图像添加训练数据。请参阅[准备训练数据](#object-detection-preparation)。
1.  训练集合。在具有足够的训练数据后，开始对集合中的图像进行训练。请参阅 V4 API 参考中的[训练集合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window}。

完成这些步骤并训练集合后，可根据该集合分析图像。

### 准备训练数据
{: #object-detection-preparation}

设置过程中最重要的部分是准备和组合训练数据。正如在[创建定制模型](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)来对图像分类时那样，您将组合一组表示要检测的对象的图像。

除了一组图像，您还将为每个图像提供训练数据。对于对象检测，训练数据是图像中您希望 {{site.data.keyword.visualrecognitionshort}} 识别的对象的标签和位置集合。一个图像中可以有多个对象。

标签标识对象是什么。位置标识对象在图像中的位置。通过在对象周围绘制_边界框_并提供该框的左上角像素坐标以及宽度和高度（以像素为单位），可识别位置。

以下示例显示标记为 `BurntCookie` 的对象的训练数据。

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

在此初始 Beta 发行版中，手动或者使用图像注释工具创建位置信息。

通常，在训练数据中提供的图像和边界框越多越好。以下是一些入门的训练数据准则：

- 每个图像的高度和宽度至少为 500 像素。
- 集合中每个标记的对象至少有 100 个位置（边界框）。
- 集合中的每个图像的边界框不超过 10 个。
- 每个边界框的大小大于图像尺寸的 15%。
- API 读取图像中的 EXIF 方向标记。确保 `location` 坐标匹配该方向。要调整方向，可以在添加边界框之前，使用工具（例如，ImageMagick）为图像_自动调整方向_。

有关 **Add training data to an image** 方法的更多信息，请参阅 [V4 API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}。

### 训练集合
{: #object-detection-train}

在向集合中的图像添加训练数据后，最终设置步骤是训练对象检测模型。API 的单个调用启动训练，响应包含状态信息。例如，以下状态显示训练已启动，但是尚未完成：

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

在更新训练数据后，可通过重新发出调用来重新训练模型。

有关更多信息，请参阅 V4 API 参考中的[训练集合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window}。

## 分析图像
{: #object-detection-analyze}

在设置定制对象检测模型并且训练完成后，可以检测其他图像中的对象。与分类一样，您将提供一个图像或提供多个图像的 `.zip` 文件，以及用于设置所检测对象的最低分数的可选**阈值**。有关更多信息，请参阅 [V4 API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images) 中的 **Analyze images** 方法。

## 后续步骤
{: #object-detection-next-steps}

- 熟悉 [V4 API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/visual-recognition-v4){: new_window} 中的 API。
