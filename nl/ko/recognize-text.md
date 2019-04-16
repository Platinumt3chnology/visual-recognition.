---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-16"

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

# 자연스러운 장면에서 텍스트 인식(베타)
{: #recognize-text}

{{site.data.keyword.visualrecognitionshort}} 베타 텍스트 모델을 사용하여 이미지에서 영문 텍스트를 감지하고 인식할 수 있습니다. 텍스트 모델은 문서의 조밀한 텍스트가 아닌 이미지의 장면 텍스트를 인식하도록 설계되었습니다. 

텍스트 모델은 개인용 베타 기능이므로 모델을 호출하려면 {{site.data.keyword.IBM_notm}}에서 제공한 권한이 있어야 합니다. [액세스를 요청 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://datasciencex.typeform.com/to/nU6efl){: new_window}하십시오. 베타 기능에 대한 자세한 내용은 [릴리스 정보](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)를 참조하십시오.
{: important}

텍스트 모델은 짧은 텍스트 문자열에서 최상으로 작동됩니다. 예를 들어, 텍스트 모델의 일반적인 용도는 표지판 읽기입니다. 

![인식된 단어 주변에 경계 상자가 있는 도로 표지판. Unsplash에서 Annie Spratt가 찍은 사진](images/walk-signal-detection.png) ![도로 표지판 이미지에서 감지된 단어 및 신뢰도 점수](images/walk-signal-response.png)

흰색 상자는 모델이 이미지에서 감지한 각각의 단어를 보여줍니다. 

## 응답
{: #recognize-text-response}

응답에는 감지된 문자열이 포함되며, 해당 문자열 내의 각 단어는 다음 정보로 식별됩니다.

- 인식된 단어
- 인식된 단어의 신뢰도를 나타내는 점수
- 단어를 중심으로 경계 상자의 위치. 상자는 단어가 이미지에서 차지하는 위치를 표시합니다.
- 단어가 발견된 라인 번호

## 적절한 텍스트 인식을 위한 가이드라인
{: #recognize-text-guidelines}

다음 가이드라인을 준수하면 이미지의 텍스트를 보다 잘 인식할 수 있습니다.

- 텍스트는 제품 코드 등의 문자열이 아니라 주로 전체 단어입니다. 이 모델은 개별 문자가 아닌 단어를 인식하며, 한 문자의 "단어"나 숫자를 버릴 수 있습니다. 
- 텍스트는 고급 형식의 글꼴이 아닌 표준 글꼴로 인쇄됩니다. 예를 들어, 자동차 번호판의 텍스트나 영화 포스터의 제목은 인식되지 않을 수 있습니다. 마찬가지로, 손으로 쓰여진 텍스트도 인식되지 않을 수 있습니다.
- 텍스트 모델은 주로 영어 단어로 훈련됩니다. 따라서 다른 언어로 된 텍스트는 인식되지 않을 수 있습니다. 

## 다음 단계
{: #recognize-text-next-steps}

- 이미지에서 텍스트를 인식하기 위해 [호출을 수행](/docs/services/visual-recognition?topic=visual-recognition-tutorial-recognize-text#tutorial-recognize-text)합니다. 
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text){: new_window}에서 API에 대해 익힙니다. 
