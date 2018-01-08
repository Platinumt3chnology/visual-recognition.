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

# 릴리스 정보

서비스에 대해 다음의 새 기능과 변경사항이 제공될 수 있습니다.
{: shortdesc}

## 베타 기능
{: #beta}

{{site.data.keyword.IBM_notm}}은 베타로 분류된 평가에 대해 서비스, 기능 및 언어 지원을 릴리스합니다. 이러한 기능은 불안정하고 자주 변경될 수 있으며 충분한 예고 없이 중단될 수 있습니다. 또한 베타 기능은 일반적으로 사용되는 기능에서 제공하는 것과 동일한 레벨의 성능이나 호환성을 제공하지 않을 수 있으며, 프로덕션 환경에서 사용하도록 제공되지 않습니다. 베타 기능은 [developerWorks Answers ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}에서만 지원됩니다. 

## 변경사항
{: #changelog}

서비스에 대해 다음의 새 기능과 변경사항이 제공될 수 있습니다. 

### 2017년 12월 11일
{: #11december2017}

<ul>
  <li>
    <strong>일반 모델에서 정확도와 출력 증가</strong>
      <p>
        수 천개의 태그가 포함된 일반 모델은 이제 추가로 부차적인 물체를 감지하며, 개선된 장면 감지 기능을 보유합니다. 이러한 개선사항을 이용하면 이미지의 눈에 잘 띄지 않는 측면을 인식하는 데 도움이 됩니다. 또한 이미지당 리턴되는 평균 태그 수가 10개로 증가되었습니다.
      </p>
      <p>
        다음 이미지에서는 업데이트 이전에 리턴된 태그와 현재 리턴되는 추가적인 태그의 예제를 보여줍니다.
      </p>
      <img src="images/antarctica-iceberg.jpg" alt="남극 대륙의 빙산">
      <table>
        <tr>
          <th>원래 태그</th>
          <th>추가 태그</th>
        </tr>
        <tr>
          <td>
          태그: 빙산<br/>
          점수: 0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          태그: 얼음 덩어리<br/>
          점수: 0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          태그: 자연<br/>
          점수: 0.770</td>
        </tr>
        <tr>
          <td>
          태그: 파란색<br/>
          점수: 0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          태그: 설화석고색<br/>
          점수: 0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>베타에서 새 명시 모델 사용 가능</strong>
      <p>
        베타로 실행되는 명시 모델은 이미지에 포르노 컨텐츠가 포함되어 있는지와 일반 용도로 부적절한지 여부를 분류합니다. 통합 분석을 위해 기타 모델에 명시 모델을 포함시킬 수 있습니다. 예를 들어, 이미지 태그 및 이미지에 명시 컨텐츠가 포함되는지 여부를 리턴하려면 요청에 `default` 및 `explicit` 분류자 ID를 모두 포함하십시오.
      <p>
        API 호출에 대한 세부사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image)의 **이미지 분류** 메소드를 참조하거나 [API 탐색기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify)에서 모델을 사용해 보십시오.
      </p>
    </li>
    <li>
      <strong>대형 파일 크기 지원</strong>
      <p>
        <strong>이미지 분류</strong> 메소드는 이제 최대 10MB의 이미지 파일과 최대 100MB의 .zip 파일을 지원합니다.
    </li>
    <li>
      <strong>분류자 ID 전달 시에 배열이 필요함</strong>
      <p>
        API는 이제 **이미지 분류** 메소드의 **매개변수** 오브젝트의 일부로서 `classifier_ids`에서 전달될 때 배열을 적용합니다. 이전에는 분류자 ID를 문자열로서 전달할 수 있었습니다. 자세한 정보는 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image)의 매개변수 설명과 예제 파일을 참조하십시오.
      </p>
    </li>
</ul>

### 2017년 9월 8일
{: #8september2017}

- **베타 유사성 검색 및 콜렉션이 종료됨**: 2017년 9월 8일 현재, 유사성 검색의 베타 기간이 종료되었습니다. 자세한 정보는 [Visual Recognition API – 유사성 검색 업데이트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}를 참조하십시오. 

### 2017년 6월 30일
{: #30june2017}

- **개선된 태그 지정**: 기본 분류자에 대한 학습 이미지의 수를 늘렸습니다. 이러한 증가에 따라 이미지의 전체 '장면'을 정확하게 인식하는 기능이 개선되었습니다. 세부사항은 [일반 태그 지정 기능에 대한 추가 개선사항 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}을 참조하십시오. 
- **추가된 언어**: **이미지 분류** 메소드는 이제 영어, 아랍어, 스페인어, 일본어와 함께 한국어, 이탈리아어, 독일어를 지원합니다. 

    API 호출에 대한 세부사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 외부 링크 아이콘의 **이미지 분류** 메소드를 참조하십시오. 

### 2017년 5월 16일
{: #16may2017}

- **새 음식 분류자 사용 가능: 베타**

    새 베타 음식 인식 모델은 음식 항목의 이미지에 대한 개선된 특수성과 정확성을 제공합니다. **이미지 분류** 메소드를 사용하면 이 새로운 "음식" 분류자를 `classifier_ids` 매개변수에 추가할 수 있습니다. 

### 2017년 4월 5일
{: #5april2017}

- **새 {{site.data.keyword.visualrecognitionshort}} 도구 사용 가능: 베타**

    새 베타 기능인 {{site.data.keyword.visualrecognitionshort}} 도구는 [https://watson-visual-recognition.ng.bluemix.net/ ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}에서 사용 가능합니다. 이 도구를 사용하면 {{site.data.keyword.visualrecognitionshort}} 서비스 관련 작업을 보다 쉽게 수행하는 데 도움이 됩니다. {{{site.data.keyword.cloud_notm}} API 키를 입력하면 GUI를 사용하여 일반 태그 지정 및 얼굴 감지 기능에 액세스할 수 있습니다. 또한 코딩을 수행하지 않고도 API 키와 연관된 사용자 정의 분류자를 완벽하게 작성, 재학습 및 삭제할 수도 있습니다. 

### 2017년 3월 8일
{: #8march2017}

- **일반 분류자 태그 지정에 대해 업데이트된 언어 지원**

    일반 분류자는 이제 지원되는 모든 언어에서 태그를 리턴합니다. 

- **알려진 문제**

    **FIXED 04-13-2017**: 상태 확인을 위해 학습 및 재학습이 진행 중인 동안 `GET /classifiers`를 반복 호출하면 학습 작업이 강제 종료될 수 있습니다. 이 문제를 임시로 해결하려면 `GET /classifiers/{classifier_id}`를 사용하여 새 분류자의 상태를 폴링하십시오. 다시 말하면, 모든 분류자를 가져오고 이 문제를 트리거할 수 있는 `GET /classifiers` 대신에 단일 분류자 ID에 대해 분류자 `GET`을 사용하십시오. 참고로, `GET /classifiers/{classifier_id}`는 속도도 더 빠릅니다. 

### 2016년 12월 15일
{: #15december2016}

- **개선된 일반 분류자 태그 지정**

    - 일반 분류자의 딥 러닝 알고리즘이 업데이트되었습니다. 모든 언어에 대해 태그 품질이 상당히 개선되었으며, 서비스가 리턴하는 영어 태그의 볼륨이 상당히 증가되었습니다. 이러한 고품질 태그 출력은 고유의 사용자 정의 분류자를 작성할 때도 사용 가능합니다. 
    - 색상 태그 지정이 추가되었습니다. 서비스는 이제 이미지에서 맨 위의 1 - 2개 색상을 리턴합니다. 

- **알려진 문제**

    - EXIF 메타데이터 태그와 함께 데모에 제출된 이미지가 서비스에 대해 올바르게 방향(가로 대 세로)을 지정하지 않습니다. iPhone 업로드된 이미지에는 EXIF 메타데이터 태그가 포함될 수 있습니다. 이에 대한 임시 해결책은 EXIF 메타데이터 태그에 의존하여 이미지의 방향을 지정하지 않도록 이미지 메타데이터를 업데이트하는 것입니다. 보통은 단지 컴퓨터에서 이미지를 열고 이를 저장함으로써 이 작업을 수행할 수 있습니다. 예를 들어, Mac에서는 미리보기에서 열기를 수행한 후에 이미지를 저장하면 올바른 방향 태그가 설정됩니다. 
    - 8, 3 또는 6의 [EXIF 태그 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://en.wikipedia.org/wiki/Exif){: new_window} 값으로 {{site.data.keyword.visualrecognitionshort}} 서비스에 이미지를 전송하면 대기 시간이 추가될 수 있습니다. 이 서비스는 이미지의 픽셀을 인코딩된 관점으로 회전시킵니다. {{site.data.keyword.visualrecognitionshort}} 태스크에 중요하지 않은 경우에는 EXIF 헤더를 제거하거나 이미지를 미리 회전시켜서 시간을 절약할 수 있습니다. 

### 2016년 12월 1일
{: #1december2016}

- **새 가격 책정**

    IBM은 {{site.data.keyword.visualrecognitionshort}} 서비스에서 사용자 정의 분류자의 가격을 낮게 책정했으며 무료 사용제에서 사용 가능한 항목을 늘렸습니다. 자세한 정보는 [{{site.data.keyword.visualrecognitionshort}} 가격 책정 페이지](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)를 참조하십시오. 

### 2016년 10월 7일
{: #7october2016}

- **얼굴 감지 개선사항**

    서비스에는 `GET` 및 `POST /v3/detect_faces` 메소드의 응답을 개선시키는 새 얼굴 감지 알고리즘이 있습니다. 이 서비스는 낮은 신뢰도의 연령, 이름 및 성별 얼굴 감지의 필터링을 조정했습니다. 결과적으로, 추가로 얼굴이 감지되며 보다 큰 범위의 신뢰도가 리턴됩니다. 

### 2016년 9월 8일
{: #8september2016}

- **유사성 검색 베타**

    사용자는 이제 고유 이미지 콜렉션을 업로드하고 이미지를 사용하여 해당 콜렉션에서 유사한 이미지를 검색할 수 있으며, 이 서비스는 가장 유사한 상위 100개의 이미지를 리턴합니다. 유사성 검색은 임의의 용도로 활용될 수 있으며, 각각 최대 100만개 이미지의 콜렉션에 대해 서비스의 사용자 정의된 학습이 가능합니다. 새 유사성 검색 기능의 사용에 대한 자세한 정보는 [튜토리얼](/docs/services/visual-recognition/tutorial-collections.html) 및 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 페이지를 참조하십시오. 

- **텍스트 인식이 이제 베타를 마감함**

    `POST` 및 `GET /v3/recognize_text` 메소드는 마감된 베타로 돌아갔습니다. IBM은 다른 오픈 베타에 대한 현재 플랜 없이 서비스를 사용하는 베타 클라이언트의 지원을 계속할 수 있기를 기대합니다. 

### 2016년 8월 1일

- **출시 기념 특별가 종료**

    사용자 정의 분류자 학습 및 재학습, 사용자 정의 이미지 분류 및 사용자 정의 분류자 스토리지는 더 이상 무료가 아닙니다. 가격 책정에 대한 정보는 {{site.data.keyword.visualrecognitionshort}} 서비스 [가격 책정 페이지](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)를 참조하십시오. 

### 2016년 7월 5일
{: #5july2016}

- **사용자 정의 분류자 업데이트**

    사용자 정의 분류자는 더 이상 고정된 학습 데이터 세트로 제한되지 않습니다. 사용자는 이제 기존 분류자를 새 이미지로 업데이트하거나 긍정 또는 부정 예제 분류자를 기존의 학습된 분류자에 더 추가할 수 있습니다. Watson이 학습할 수 있도록 추가적인 예제 이미지를 제공함으로써 이 서비스는 사용자의 분류자를 보다 정확하게 만들 수 있습니다. 사용자 정의 분류자는 이제 시간의 흐름에 따른 지속적 학습이 가능하며, 계속해서 시각적 정보를 보다 잘 이해할 수 있게 됩니다. 

- **알려진 문제**

    **FIXED 04-13-2017**: 기존 분류자를 업데이트할 때 사용자가 30 또는 90초 후에 500개의 오류 코드를 받을 수 있습니다. 오류에도 불구하고, 재학습 요청이 정상적으로 완료될 가능성이 많습니다. 최소한 2분 동안 기다린 후에 `GET classifiers/{classifier\_id}` 메소드를 사용하여 분류자의 상태를 확인하십시오. 상태가 "준비"이며 "재학습됨" 시간소인이 업데이트된 경우에는 500개 코드를 생성한 재학습 요청이 성공한 것입니다. 혹은 "재학습된" 시간소인이 업데이트되지 않은 경우, 재학습이 실패한 이유를 알리는 설명이 응답에 추가되며 서비스는 재학습 요청이 발행되기 전의 이전 버전으로 분류자를 되돌립니다. 

### 2016년 5월 20일
{: #20 may 2016}

이는 {{site.data.keyword.visualrecognitionshort}} 서비스의 GA(General Availability) 릴리스입니다. 이 릴리스에서는 서비스의 버전 3이 도입되며, 이는 파괴적 변경사항입니다. 이 릴리스는 더 이상 사용되지 않는 AlchemyVision 서비스의 기능을 구현합니다. 

서비스가 베타인 동안 작성된 사용자 정의 분류자는 서비스의 GA 인스턴스에서 재작성되어야 합니다. 

{{site.data.keyword.visualrecognitionshort}} 서비스가 다음과 같이 변경되고 업데이트되었습니다. 

- **버전 날짜** 이 릴리스의 기능을 활용하려면 `2016-05-20`을 `version` 매개변수의 값으로 사용하십시오. 
- **클래스 및 분류자:** 단일 분류자를 이제는 "클래스"라고 합니다. GA에서는 클래스의 그룹을 "분류자"라고 합니다. 
- **분류:** `POST` 또는 `GET /v3/classify` 메소드를 사용하여 기본 클래스로 다양한 대상과 장면을 빠르고 정확하게 식별할 수 있습니다. 
- **얼굴 감지:** `POST` 또는 `GET /v3/detect_faces` 메소드를 사용하여 이미지에서 얼굴을 감지하고 이에 대한 정보를 가져올 수 있습니다(예: 이미지에서 얼굴이 차지하는 위치 및 각 얼굴의 예상된 연령 범위와 성별). 이 서비스는 이름으로 많은 유명 인사를 식별할 수도 있으며, 사용자가 상위 레벨 개념으로 흥미로운 집계를 수행할 수 있도록 지식 그래프를 제공할 수 있습니다. 
- **다면 사용자 정의 분류자:** 이제 여러 클래스로 정의된 매우 특수한 분류자를 작성하고 학습시킬 수 있습니다. 예를 들어, "new\_cars" 및 "red\_cars" 클래스로 정의된 "new\_red\_car" 분류자를 작성할 수 있습니다. 다면 분류자 작성에 대해 자세히 학습하려면 [학습 데이터의 구조](/docs/services/visual-recognition/customizing.html#structure)를 참조하십시오. 
- **비동기 학습:** 사용자 정의 분류자의 학습이 이제 비동기 상태이므로, 사용자 정의 분류자가 백그라운드에서 계속해서 학습하는 동안 학습 호출이 빠르게 완료됩니다. 사용자 정의 분류자의 학습 상태를 확인하고 언제 사용 가능한지 알아보려면 `GET /v3/classifiers/{classifier_id}` 메소드를 호출하고 `status` 응답 매개변수를 확인하십시오. 

### 2015년 12월 2일
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 서비스의 최신 릴리스는 {{site.data.keyword.visualrecognitionshort}} API의 새 버전(v2)이 도입된 파괴적 변경사항입니다. {{site.data.keyword.visualrecognitionshort}} 서비스의 버전 1은 서비스가 베타를 종료할 때까지 사용 가능합니다. 

API의 버전 2 사용을 바로 시작하려면 다음 변경사항을 반영하는 코드를 이해하고 업데이트하십시오. 

- 서비스의 버전 1에서는 레이블로 이미지를 분석했습니다. 서비스의 버전 2에서는 레이블을 **분류자**라고 합니다. 분류자에는 `classifier_id` 매개변수로 표시된 고유 분류자 ID 및 `name` 매개변수로 표시된 단축 이름이 있습니다. 
- 이미지 분석을 위한 `POST /v1/recognize` 메소드는 이제 [`POST /v2/classify` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window} 메소드입니다. `labels_to_check` 매개변수는 `classifier_ids`로 이름이 변경되었습니다. 
- V1에서 레이블의 목록을 검색하기 위한 `GET /v1/tag/labels` 메소드는 이제 분류자의 목록을 검색하기 위한 [`GET /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window} 메소드입니다. 
- 분류자 목록의 검색에 추가하여, 새 [`GET /v2/classifiers/{classifier_id}` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window} 메소드로 특정 분류자에 대한 세부사항을 검색할 수도 있습니다. 
- 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2를 사용하여 새 [`POST /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window} 메소드로 사용자 정의 분류자를 작성할 수 있습니다. 사용자 정의 분류자 작성에 대해 자세히 학습하려면 [사용자 정의 분류자 작성](/docs/services/visual-recognition/customizing.html)을 참조하십시오. 
- 또한 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2를 사용하여 새 [`DELETE /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window} 메소드로 사용자 정의 분류자를 삭제할 수도 있습니다. 
- 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2에서는 `version` 매개변수가 필요합니다. `MM-DD-YYYY` 형식으로 사용할 API 버전의 릴리스 날짜를 지정하십시오. 
