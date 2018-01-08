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

# 关于分类器

对图像分类时，Visual Recognition 会返回在图像中找到的一组类。它是从培训它所使用的图像中派生出这些信息的。分类器是一组类。

Visual Recognition 包含多个内置分类器，不必执行培训就能提供准确性很高的结果。此外，还可以培训定制分类器来创建专业化类。

Clarifai 入门
> 预测的类型取决于通过什么模型运行输入。例如，如果是通过“食品”模型运行的输入，那么返回的预测将包含“食品”模型所了解的概念。如果是通过“颜色”模型运行的输入，那么会返回有关图像中主色的预测。

Clarifai
> Clarifai 提供了许多不同的模型，这些模型以不同的方式“看”世界。模型包含一组概念。模型只会看到其包含的概念。
>
> 有时，您会希望拥有一个模型以您的方式看世界。借助此 API，您可以做到这一点。您可以创建自己的模型，并使用自己的图像和概念进行培训。如果通过培训使模型能够以您希望的方式看世界，那么就可以使用该模型进行预测了。

## 内置分类器

Visual Recognition 包含一组分类器，无需培训就能提供准确性很高的结果。当前的内置分类器名为 `default`、`food` 和 `explicit`。

### default 分类器

default 分类器会从组织成类别和子类别的数千个可能的标记中返回类。可能会返回以下顶级类别：

- 动物（包含鸟类、爬行类、两栖类等）
- 人和以人为中心的信息和活动
- 食品（包括熟食和饮料）
- 植物（包括树、灌木、水生植物和蔬菜）
- 体育运动
- 自然（包括许多类型的自然形态和地质结构）
- 交通运输（陆运、水运和空运）
- 其他更多类别，包括家具、水果、乐器、工具、颜色、小配件、设备、仪器、武器、建筑物、结构和人造物品、服装和花卉等等。

### food 分类器

虽然缺省分类器可以识别食品和饮料，但也可以指定内置 `food` 分类器用于...

### explicit 分类器

Visual Recognition 可以通过分类来确定图像是否适合一般用途。`explicit` 分类器当前用于识别哪些内容可能会视为色情图像。此分类的通用缩写为 _NSFW_，意即_不适合工作场所_。

高于或低于特定数字的分数并不能保证图像是否露骨。但是，可以将响应用作图像的初始过滤器，并对过滤后的内容进行更多分析。

响应：
```json
{
  "images": [
    {
      "classifiers": [
        {
          "classes": [
            {
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
  ],
  "images_processed": 1
}
```
{: codeblock}

## 组合分类器


## 响应中的类层次结构

`/v3/classify` 方法用于将图像分类到相关类的层次结构中。例如，比格犬的照片可分类为“动物”以及相关的“狗”和“比格犬”。与相关类别（在本例中为“狗”和“比格犬”）的正面匹配提升了父响应的分数。在此示例中，响应包括所有三个类：“动物”、“狗”和“比格犬”。父类（“动物”）的分数因为与相关类（“狗”和“比格犬”）相匹配而得到提升。父代还是“type\_hierarchy”，以表明这是该层次结构的父代。

## 大量分类准则

提交大量图像时，可以通过以下方式尽可能提高服务的效率和性能：

- 将图像裁剪或调整为 224 x 224 像素。服务目前已针对此大小进行了优化，但有可能此大小会更改。
    - 如果图像的宽高比大于 2:1 或小于 1:2，请裁剪图像。
    - 考虑将图像裁剪成多个方形图像，或仅包含图像中心，具体取决于您最想使用哪个部分。
- 在单个 .zip 文件中最多提交 20 个图像。不需要使用任何压缩，因为 JPEG 和 PNG 图像本身就是压缩文件。
- 使用 **classifier_ids** 参数以仅指定要使用的分类器。
- 虽然服务会读取 EXIF 标记并旋转图像，但为了获得最佳吞吐量，请发送不需要服务进行旋转的图像（EXIF **方向**标记设置为 `1`）。
