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

# 사용자 정의 오브젝트 감지(베타)
{: #object-detection-overview}

{{site.data.keyword.visualrecognitionfull}} 사용자 정의 오브젝트 감지(베타)는 이미지에서 항목과 항목의 위치를 식별합니다. 이 서비스는 사용자가 제공한 레이블 지정된 훈련 데이터를 사용하여 이미지 세트를 기반으로 이러한 항목을 발견합니다.
{: shortdesc}

사용자 정의 오브젝트 감지는 개인용 베타 기능이므로 모델을 호출하려면 {{site.data.keyword.IBM_notm}}에서 제공한 권한이 있어야 합니다. [액세스를 요청 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://datasciencex.typeform.com/to/c70Ak5){: new_window}하십시오. 베타 기능에 대한 자세한 내용은 [릴리스 정보](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)를 참조하십시오.
{: important}

워크플로우 또는 도메인에 중요한 오브젝트를 인식하도록 오브젝트 감지 모델을 훈련시키십시오. 예를 들어 자동차 손상 감지, 유지보수가 필요한 기계 찾기 또는 현장에서 육안 검사 등을 수행하십시오. 오브젝트 감지를 사용하여 오브젝트를 계수하거나 인벤토리를 관리할 수도 있습니다. 

## 오브젝트 감지 및 분류 비교
{: #obj-detect-comparison}

사용자 정의 오브젝트 감지 모델은 {{site.data.keyword.visualrecognitionshort}}의 최신 기능으로, 분류 기능을 포함하고 있습니다. 

분류 및 오브젝트 감지는 유사하지만 용도가 다릅니다. 일반적으로 이미지에서 오브젝트의 존재를 예측하려는 경우에 분류가 사용되고, 이미지에서 오브젝트를 찾거나 계수하려는 경우에 오브젝트 감지가 사용됩니다. 

### 분류
{: #obj-detect-classify}

이미지를 분류하면 서비스는 특정 오브젝트가 해당 이미지에 있을 확률로 응답합니다. 기본 제공 모델(일반, 음식, 명시)을 사용하거나 고유한 사용자 정의 모델을 작성할 수 있습니다. 

예를 들어, 다음 이미지와 같은 쿠키 이미지를 분류할 때 서비스는 95% 신뢰도로 이미지에 쿠키가 있다고 예측합니다. 

![분류 응답 이미지](images/cookies-tag.png "분류를 보여주는 이미지")

### 오브젝트 감지
{: #obj-detect-detect}

사용자 정의 오브젝트 감지는 사용자 정의 분류와 유사하지만, 이 서비스는 이미지에서 항목의 위치를 식별합니다. 분류와 마찬가지로, 응답에는 감지된 각 항목의 레이블과 식별에 대한 신뢰도가 포함되어 있습니다. 

감지된 항목은 오브젝트 감지 모델을 훈련시킬 때 제공한 정보를 기반으로 합니다. 

다음 이미지에서 사용자 정의 오브젝트 감지의 **이미지 분석** 메소드는 이미지에서 쿠키의 위치를 식별합니다. 감지된 각 오브젝트에는 위치 및 신뢰도 점수와 함께 레이블(이 경우 `Cookie`)이 포함되어 있습니다. 

![오브젝트 감지 응답 이미지](images/cookies-bbox.png "오브젝트 감지를 보여주는 이미지")

## 사용자 정의 오브젝트 감지를 사용하는 방법
{: #object-detection-sequence}

{{site.data.keyword.visualrecognitionshort}} 사용자 정의 오브젝트 감지를 사용하려면 이 일련의 단계를 수행하여 사용자 정의 오브젝트 감지 모델을 설정하십시오. 

1.  콜렉션을 작성하십시오. 콜렉션은 이미지 및 훈련 데이터용 컨테이너입니다. v4 API 참조서에서 [콜렉션 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#create-a-collection){: new_window}을 참조하십시오. 
1.  콜렉션에 이미지를 추가하십시오. URL 또는 파일로 단일 이미지를 추가하거나, 이미지의 `.zip` 파일을 업로드할 수 있습니다. v4 API 참조서에서 [이미지 추가 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#add-images){: new_window}를 참조하십시오. 
1.  이미지에 훈련 데이터를 추가하십시오. [훈련 데이터 준비](#object-detection-preparation)를 참조하십시오. 
1.  콜렉션을 교육시키십시오. 충분한 훈련 데이터가 생기면 콜렉션의 이미지에 대한 훈련을 시작하십시오. v4 API 참조서에서 [콜렉션 훈련 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window}을 참조하십시오. 

이러한 단계를 완료하고 콜렉션을 훈련시킨 후에는 콜렉션에 대해 이미지를 분석할 수 있습니다. 

### 훈련 데이터 준비
{: #object-detection-preparation}

설정 프로세스의 가장 중요한 부분은 훈련 데이터를 준비하고 어셈블하는 것입니다. 이미지 분류를 위해 [사용자 정의 모델을 작성](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)할 때와 마찬가지로, 감지하려는 오브젝트를 나타내는 이미지 세트를 어셈블하십시오.

이미지 세트 이외에도 각 이미지에 대한 훈련 데이터도 제공하십시오. 오브젝트 감지의 경우 훈련 데이터는 {{site.data.keyword.visualrecognitionshort}}에서 인식할 이미지에 있는 오브젝트의 레이블 및 위치 세트입니다. 한 이미지에 둘 이상의 오브젝트가 있을 수 있습니다. 

레이블은 오브젝트가 무엇인지 식별합니다. 위치는 이미지에서 오브젝트가 있는 위치를 식별합니다. 위치를 식별하려면 오브젝트 주변의 _경계 상자_를 끈 다음 해당 상자의 위쪽 및 왼쪽 픽셀 좌표를 픽셀 단위의 너비 및 높이와 함께 제공하십시오. 

다음 예는 `BurntCookie`라는 오브젝트의 훈련 데이터를 보여줍니다. 

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

이 초기 베타 릴리스에서는 위치 정보를 직접 작성하거나 이미지 어노테이션 도구를 사용하여 작성하십시오. 

일반적으로 사용자가 학습 데이터에 제공하는 이미지와 경계 상자가 많을수록 좋습니다. 시작하는 데 필요한 훈련 데이터 가이드라인은 다음과 같습니다. 

- 각 이미지의 높이와 너비는 최소 500픽셀입니다. 
- 콜렉션의 레이블 지정된 오브젝트 각각에는 최소 100개의 위치(경계 상자)가 있습니다. 
- 콜렉션의 각 이미지에는 최대 10개의 경계 상자가 있습니다. 
- 각 경계 상자의 크기는 이미지 치수의 15%보다 큽니다. 
- API는 이미지에서 EXIF 방향 태그를 읽습니다. `location` 좌표가 해당 방향과 일치하는지 확인하십시오. 방향을 조정하려면 경계 상자를 추가하기 전에 ImageMagick과 같은 도구를 사용하여 이미지의 _방향을 자동 지정_하십시오. 

**이미지에 훈련 데이터 추가** 메소드에 대한 자세한 정보는 [v4 API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#add-training-data-to-an-image){: new_window}을 참조하십시오. 

### 콜렉션 훈련
{: #object-detection-train}

콜렉션의 이미지에 훈련 데이터를 추가한 후 최종 설정 단계는 오브젝트 감지 모델을 훈련시키는 것입니다. API를 한 번 호출하면 훈련이 시작되며, 응답에 상태 정보가 포함됩니다. 예를 들어 다음 상태는 훈련이 시작되었지만 아직 완료되지 않았음을 나타냅니다. 

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

훈련 데이터를 업데이트한 후 호출을 다시 실행하여 모델을 재훈련시킬 수 있습니다.

자세한 정보는 v4 API 참조서에서 [콜렉션 훈련 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#train-a-collection){: new_window}을 참조하십시오. 

## 이미지 분석
{: #object-detection-analyze}

사용자 정의 오브젝트 감지 모델을 설정하고 훈련이 완료된 후에는 다른 이미지에서 오브젝트를 감지할 수 있습니다. 분류와 마찬가지로, 이미지 또는 이미지의 `.zip` 파일 및 선택적 **임계값**을 제공하여 감지된 오브젝트의 최소 점수를 설정하십시오. 자세한 정보는 [v4 API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition-v4#analyze-images)에서 **이미지 분석** 메소드를 참조하십시오.


## 다음 단계
{: #object-detection-next-steps}

- [v4 API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")][api-ref-v4]{: new_window}에서 API에 대해 익힙니다. 
