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

# 릴리스 정보
{: #release-notes}

서비스에 대해 다음의 새 기능과 변경사항이 제공될 수 있습니다.
{: shortdesc}

## 서비스 API 버전화
{: version}

API 요청에는 `version=YYYY-MM-DD` 형식의 날짜를 사용하는 버전 매개변수가 필요합니다. API를 이전 버전과 호환되는 방식으로 변경할 때마다 API의 부 버전이 새로 릴리스됩니다. 

API 요청이 있을 때마다 버전 매개변수를 전송하십시오. 서비스는 지정한 날짜에 해당하는 API 버전이나 해당 날짜 이전의 최신 버전을 사용합니다. 현재 날짜를 기본값으로 설정하지 마십시오. 대신, 사용자의 앱과 호환되는 버전과 일치하는 날짜를 지정하고 이후 버전의 앱이 준비될 때까지 변경하지 마십시오. 

현재 버전은 `2018-03-19`입니다. 

## 베타 기능
{: #beta}

{{site.data.keyword.IBM_notm}}은 베타로 분류된 평가에 대해 서비스, 기능 및 언어 지원을 릴리스합니다. 이러한 기능은 불안정하고 자주 변경될 수 있으며 충분한 예고 없이 중단될 수 있습니다. 또한 베타 기능은 일반적으로 사용되는 기능에서 제공하는 것과 동일한 레벨의 성능이나 호환성을 제공하지 않을 수 있으며, 프로덕션 환경에서 사용하도록 제공되지는 않습니다. 베타 기능은 [IBM Developer Answers ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}에서만 지원됩니다. 

## 변경사항
{: #changelog}

서비스에 대해 다음의 새 기능과 변경사항이 제공될 수 있습니다.

### 2019년 1월 15일
{: #15january2019}

- **얼굴 감지에서 성별에 대한 번역**
    - **Accept-Language** 요청 헤더에 언어를 제공하면 이제 **얼굴 감지** 메소드가 "Male" 및 "Female"에 대해 번역된 레이블을 리턴합니다. 자세한 내용은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}를 참조하십시오. 

### 2018년 10월 1일
{: #01october2018}

- **2018년 5월 23일 이전에 작성된 서비스가 삭제됩니다.** 

    - 이전에 공지한 바와 같이, 2018년 5월 23일 이전에 작성된 모든 {{site.data.keyword.visualrecognitionshort}} 인스턴스는 더 이상 활성화되지 않습니다. 해당 인스턴스의 데이터가 이제 삭제됩니다. 새로운 서비스 인스턴스로 이동하는 자세한 방법은 [마이그레이션](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)을 참조하십시오. 
    - 이 날짜 이후에 작성된 서비스 인스턴스는 영향을 받지 않습니다. 
    - 문의 사항이 있을 경우 [IBM 지원 센터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/ibmcloudsupport){: new_window}에 문의하십시오. 

### 2018년 8월 1일
{: #01august2018}

- **음식 모델 및 명시 모델의 GA(General Availability)**

    음식 모델 및 명시 모델이 베타에서 GA(General Availability)로 이동되었습니다. 음식 모델은 일반(기본) 모델에 비해 더 많은 음식과 식사를 인식합니다. 명시 모델은 포르노 이미지로 간주될 수 있는 이미지를 식별합니다. 

    코드 변경은 필요하지 않습니다. Lite 플랜을 사용할 경우 두 모델 모두 무료이며, 표준 플랜을 사용할 경우 이미지당 0.002달러의 비용이 청구됩니다. 

    자세한 정보는 <em>Watson 블로그</em>에서 [Watson Visual Recognition에 대한 업데이트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/visrec-price-reduction){: new_window}를 참조하십시오. 

### 2018년 7월 1일
{: #01july2018}

- **사용자 정의 모델에 대한 새로운 가격**
    -  2018년 7월 1일부터 이미지를 사용자 정의 모델로 분류하는 비용이 이전 가격의 절반으로 제공되어 이제 이미지당 0.002달러입니다. 자세한 정보 및 기타 중요한 정보는 <em>Watson 블로그</em>에서 [Watson Visual Recognition에 대한 업데이트 \- 사용자 정의 분류 가격 절감 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/visrec-price-reduction){: new_window}을 참조하십시오. 

### 2018년 6월 21일
{: #21june2018}

- **추가 언어 지원**

    - **분류** 메소드가 이제 `default`(일반) 모델 클래스의 출력에서 중국어(간체 및 번체)와 포루투갈어(브라질)를 지원합니다. 전체 언어 목록은 [지원되는 언어](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)를 참조하십시오. 
    - 이제 **음식** 모델 및 **명시** 모델의 응답에서 모든 언어가 지원됩니다. 


### 2018년 5월 22일
{: #22may2018}

- **새로운 API 인증 프로세스**:

    이제 새 엔드포인트에서 IAM(Identity and Access Management)으로 인증을 수행합니다. 

    - 새 인스턴스에 다른 엔드포인트 URL을 사용하십시오. 기본 엔드포인트는 `https:/gateway.watsonplatform.net/visual-recognition/api/`입니다. 서비스 인스턴스의 URL을 찾으려면 {{site.data.keyword.cloud_notm}} [대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/dashboard/apps?watson){: new_window}에서 인스턴스를 클릭하여 인증 정보를 확인하십시오.
    - API 인증 방식을 수정하십시오. 서비스 인스턴스에 대해 IAM 키 또는 액세스 토큰을 제공하십시오. 예는 [마이그레이션](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)을 참조하십시오. 

    2018년 5월 23일 이전에 작성된 서비스 인스턴스의 경우 인증 프로세스와 엔드포인트가 변경되지 않았습니다. `api_key` 조회 매개변수를 제공하여 인증하십시오. 

- **Lite 플랜 관련 업데이트 사항**

    2018년 5월 22일 이후에 작성된 Lite 플랜이 다음과 같이 변경됩니다. 

    - Lite 플랜 인스턴스를 매달 사용하는 경우 30일 이후에 새 인스턴스를 계속 사용할 수 있습니다. 
    - 새 Lite 플랜을 사용할 경우 두 개의 사용자 정의 모델을 작성하고 재훈련할 수 있습니다. 
    - Lite 플랜에는 한 달에 최대 1,000개의 이벤트가 포함됩니다. 분류, 감지 또는 훈련을 위해 전송한 각 이미지가 이벤트입니다. Core ML 모델 다운로드는 이벤트 한계 계산에 포함되지 않습니다. 

    Lite 플랜을 초과할 경우 청구 가능 계정으로 업데이트하십시오. 가격 플랜을 [탐색 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window}하십시오. 

- **정보 보안**:

    데이터 개인정보처리방침에 대한 새로운 세부사항을 포함하도록 문서를 업데이트했습니다. [정보 보안](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security)에서 세부사항을 검토하십시오. 

### 2018년 4월 12일
{: #12april2018}

- **Lite 플랜에서 사용자 정의 모델 재훈련 지원**

    Lite 플랜을 사용할 경우 모델을 업데이트하거나 재훈련하려 할 때 다른 사용자 정의 모델을 삭제하고 작성할 필요가 없습니다. 이제 플랜의 일별 및 월별 [한계](https://console.bluemix.net/catalog/services/visual-recognition)를 초과하지 않는 한 사용자 정의 모델을 업데이트할 수 있습니다. 

    여러 모델이 필요하거나 동일한 모델의 여러 버전이 필요한 경우 Lite 플랜에서 청구 가능 계정으로 업데이트하십시오. 

- **CORS 지원 관련 새로운 부 버전**

    **버전:** `2018-03-19`

    이제 요청에 `version=2018-03-19`를 지정하면 CORS(Cross-Origin Resource Sharing) 헤더가 지원됩니다. 

### 2018년 4월 5일
{: #5april2018}

- **얼굴 모델 점수 문제 해결**

  얼굴 모델의 연령 점수 범위가 원래 범위인 0 - 1로 복원되었습니다. 자세한 내용은 2018년 4월 2일의 [알려진 문제](#2april2018)를 참조하십시오. 

- **새로운 form-data 매개변수**

    **이미지 분류** 및 **이미지에서 얼굴 인식** 메소드가 새로운 form-data 매개변수를 지원합니다. 이미지 분류는 별도의 `url`, `classifier_ids`, `threshold`, `owners` 매개변수를 지원하고, 얼굴 감지는 `url`을 지원합니다. 

    과거에는 값을 JSON 문자열로 인코딩하고 **매개변수**에 form-data 매개변수를 전달했습니다. 모든 애플리케이션 개발에 대해 이러한 값을 별도의 form-data 매개변수에 전달하는 새로운 방법을 사용할 수 있습니다. 자세한 내용은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition){: new_window}를 참조하십시오. 

### 2018년 4월 2일
{: #2april2018}

- **향상된 얼굴 모델의 GA(General Availability)**

    업데이트된 얼굴 감지 모델이 이제 GA(General Availability) 상태입니다. 

    이 향상된 모델은 연령 및 성별에 맞춰 얼굴 감지의 정확도를 향상시키기 위해 더 광범위한 훈련 데이터 세트를 사용합니다. 예를 들어 `min` 및 `max` 간의 범위를 줄여 연령 예측이 향상되었습니다. 이전 모델에서 수정된 9살 연령 범위가 동적이면서 더 작은 범위로 바뀌었습니다. 평균 연령 범위는 4.9년입니다. 

    - API 변경사항

    향상된 얼굴 모델과 이전 얼굴 모델 간 기타 차이점: 
        - 향상된 모델은 .gif 및 .tif 이미지 형식을 지원합니다. 
        - 향상된 모델은 대용량 파일 크기를 지원합니다. 이미지 파일의 경우 최대 10MB, .zip 파일의 경우 최대 100MB가 지원됩니다. 
        - 향상된 모델의 응답에는 `FaceIdentity` 정보가 포함되지 않습니다. ID 정보는 사람의 `name`, `score` 및 `type_hierarchy` 지식 그래프를 참조합니다. 

    API에 대한 자세한 내용은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}를 참조하십시오. 

    - 알려진 문제

        - 양식 매개변수에 **Content-Type**이 포함될 수 없습니다. 예를 들어 다음 요청에 `;type=text/plain`이 포함되어 있으므로 해당 요청이 **url** 매개변수를 분석하는 데 실패합니다. 

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - 연령 점수의 범위가 0 - 0.3입니다. 원래 범위인 0 - 1로 복원하기 위해 작업 중입니다. 

    - 베타 엔드포인트가 더 이상 사용되지 않음

    `/v3/detect_faces_beta`의 베타 엔드포인트가 더 이상 사용되지 않으므로 2018년 5월 17일 이후에는 액세스할 수 없습니다. 요청이 `/v3/detect_faces`를 가리키는지 확인하십시오. 

### 2018년 3월 20일
{: #20march2018}

- **Apple Core ML과 통합**

    {{site.data.keyword.visualrecognitionshort}}은 이제 Apple Core ML 모델 형식에 대한 지원을 제공합니다. iOS 앱에서 {{site.data.keyword.visualrecognitionshort}} 모델의 Core ML 버전을 사용할 수 있습니다. 

    **개발 시작**: {{site.data.keyword.visualrecognitionshort}} 및 Core ML로 개발을 시작하려면 GitHub에서 다음 프로젝트를 확인하십시오. 

    - 로컬에서 이미지 분류: [Core ML과 함께 {{site.data.keyword.visualrecognitionshort}} 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - {{site.data.keyword.discoveryfull}}를 결과와 통합: [Core ML과 함께 {{site.data.keyword.visualrecognitionshort}} 및 Discovery 사용 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - SDK 탐색: [Swift SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **API 변경사항**

    이전 버전과 호환되는 다음과 같은 API 변경사항이 통합에 포함되었습니다. 

    - 분류자 모델을 Core ML 모델로 다운로드할 수 있는지 여부를 나타내는 새로운 `core_ml_enabled` 필드. 이 필드는 `GET and POST /v3/classifiers` 및 `GET /v3/classifiers/{classifier_id}` 호출에 대한 응답에 리턴됩니다. 
    - Core ML 모델을 .mlmodel 파일로 다운로드하는 새로운 `GET /v3/classifiers/{classifier_id}/core_ml_model` 메소드. 3월 19일 이후에 작성된 사용자 정의 모델에 대한 Core ML 모델 파일을 다운로드할 수 있습니다. 
    - 모델의 최신 훈련 날짜가 포함된 새로운 `updated` 필드. `updated` 필드는 `retrained` 필드 또는 `created` 필드와 일치합니다. 

    Core ML에 대한 자세한 API 변경사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}를 참조하십시오. 

- **새로운 도구 사용 가능: Watson Studio**

    [Watson Studio ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")][watson-studio-reg]{: new_window}는 베타 {{site.data.keyword.visualrecognitionshort}}의 대체 도구를 제공하는 새로운 통합 환경입니다. Watson Studio는 {{site.data.keyword.visualrecognitionshort}}뿐 아니라 다른 여러 {{site.data.keyword.cloud_notm}} 서비스와 리소스도 지원합니다. 기존의 모든 {{site.data.keyword.visualrecognitionshort}} 인스턴스 및 분류자와 함께 Watson Studio를 사용할 수 있습니다. 

     Watson Studio는 클라우드에서 협업 환경을 제공합니다. Watson Studio를 사용할 경우 개발자, 관련 주제 전문가, 데이터 과학자 등은 {{site.data.keyword.visualrecognitionshort}} 및 다른 AI 모델을 빌드하고 훈련시킬 수 있습니다. 또한 Watson Studio를 사용하여 기본 제공 일반 모델 및 얼굴 모델에 액세스할 수 있습니다. 

     Watson Studio는 또한 Core ML도 지원합니다. 사용자 정의 모델의 Core ML 모델 파일을 다운로드할 수 있습니다. 

    Watson Studio로 [![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")][watson-studio-reg]{: new_window} 시작하기

- **사용자 정의 모델에 대한 딥 러닝 아키텍처가 업데이트됨**

    {{site.data.keyword.visualrecognitionshort}}이 이제 더 빠르고 더 효율적인 딥 러닝 네트워크 아키텍처를 분류에 사용합니다. 업데이트된 모델은 또한 최상위 클래스와 나머지 클래스를 더 강력하게 구분할 수 있습니다. 이러한 접근법은 다소 긴 훈련 시간을 초래할 수 있습니다. 새로운 사용자 정의 모델을 훈련하는 데는 새 아키텍처가 사용됩니다. 기존의 이전 모델을 재훈련할 경우에는 원래 아키텍처가 사용됩니다. 

    다음 예는 새 아키텍처와의 차이를 보여줍니다. 

    ![남자 양궁 활과 화살 - Unsplash에서 Annie Spratt가 찍은 사진](images/archery.jpg)

    <table>
      <tr>
        <th>원래 클래스 및 점수</th>
        <th>업데이트된 클래스 및 점수</th>
      </tr>
      <tr>
        <td>양궁</br>0.99 </td>
        <td><strong>양궁<strong></br>0.9</td>
      </tr>
      <tr>
        <td>자동차 경주</br>0.996398</td>
        <td><strong>자전거</strong></br>0.004</td>
      </tr>
      <tr>
        <td>자전거</br>0.0500174</td>
        <td><strong>낚시</strong></br>0.001</td>
      </tr>
      <tr>
        <td>낚시</br>0.11029</td>
        <td><strong>골프</strong></br>0.031</td>
      </tr>
      <tr>
        <td>골프</br>0.0980796</td>
        <td><strong>체조</strong></br>0.029</td>
      </tr>
      <tr>
        <td>체조</br>0.964391</td>
        <td><strong>유도</strong></br>0.021</td>
      </tr>
      <tr>
        <td>유도</br>0.339119</td>
        <td><strong>경주</strong></br>0.002</td>
      </tr>
      <tr>
        <td>스케이팅</br>0.0393602</td>
        <td><strong>스케이팅</strong></br>0.061</td>
      </tr>
      <tr>
        <td>스키</br>0.0310527</td>
        <td><strong>스키</strong></br>0.003</td>
      </tr>
      <tr>
        <td>트랙 및 필드</br>0.208147</td>
        <td><strong>트랙</strong></br>0.035</td>
      </tr>
    </table>

- **프랑스어 지원**

    **분류** 메소드가 이제 `default` 모델 클래스의 출력에서 프랑스어를 지원합니다. 전체 언어 목록은 [지원되는 언어](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages)를 참조하십시오. 

### 2018년 2월 23일
{: #23february2018}

- **베타에서 향상된 얼굴 모델 사용 가능**

    업데이트된 얼굴 감지 모델이 사용 가능합니다. 이 베타 모델은 연령 및 성별에 맞춰 얼굴 감지의 정확도를 향상시키기 위해 더 광범위한 훈련 데이터 세트를 사용합니다. 자세한 정보는 [IBM Watson {{site.data.keyword.visualrecognitionshort}} 서비스의 정확도 향상 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} 및 [AI 모델에서 편향 완화 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}를 참조하십시오. 

    - 업데이트된 모델의 결과는 [데모 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")][demo]{: new_window} 및 베타 [Visual Recognition 도구 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}에서 볼 수 있습니다. 
    - 베타 모델은 `/v3/detect_faces_beta`에서 사용 가능합니다. 

    베타 모델과 GA(General Availability) 모델 간의 차이점: 
    - 베타 모델은 .gif 및 .tif 이미지 형식을 지원합니다. 이 개선사항은 GA 모델에 적용될 예정입니다. 
    - 베타 모델은 대용량 파일 크기를 지원합니다. 이미지 파일의 경우 최대 10MB, .zip 파일의 경우 최대 100MB가 지원됩니다. 이 개선사항은 GA 모델에 적용될 예정입니다. 
    - 베타 얼굴 감지의 응답에는 `FaceIdentity` 정보가 포함되지 않습니다. 
    - 베타 모델의 POST 요청에는 비어 있지 않은 파일 이름이 필요합니다. GA 얼굴 모델에는 이 제한조건이 적용되지 않습니다. 
    - 베타 모델의 POST 요청은 별도의 양식 매개변수인 `url`을 지원합니다. GA 모델은 `parameters` JSON 오브젝트에 해당 정보를 포함하고 있습니다. 자세한 내용은 [API 탐색기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-api-explorer.mybluemix){: new_window}를 참조하십시오. 

- **얼굴 ID가 더 이상 사용되지 않음**

    GA 얼굴 모델의 응답에 있는 ID 정보가 더 이상 사용되지 않으므로 **2018년 4월 2일**에 API에서 제거될 예정입니다. ID 정보는 사람의 `name`, `score` 및 `type_hierarchy` 지식 그래프를 참조합니다. 

### 2018년 1월 16일
{: #16january2018}

- **Lite 계정 및 플랜이 무료 플랜으로 대체됨**

    Lite 계정은 무료이므로 신용카드가 필요하지 않습니다. 그러나 Lite 플랜 서비스 인스턴스는 30일 후에 삭제됩니다. 

    Lite 플랜으로 수행할 수 있는 최대 호출 수는 무료 플랜의 최대 호출 수와 약간 다릅니다. Lite 플랜의 경우 일일 250개 호출, 매월 최대 7,500개 API 호출이 가능합니다. 

    사용자 정의 분류자가 있을 때 청구 가능 계정으로 업데이트하려면 다른 서비스 인스턴스를 작성하고 사용자 정의 분류자를 다시 작성하십시오. 

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
      <img src="images/tree-flower.jpg" alt="진달래속 사진">
      <table>
        <tr>
          <th>원래 태그</th>
          <th>추가 태그</th>
        </tr>
        <tr>
          <td></td>
          <td>
          태그: 트리<br/>
          점수: 0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          태그: 꽃<br/>
          점수: 0.792</td>
        </tr>
        <tr>
          <td>
          태그: 알프스 진달래속<br/>
          점수: 0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          태그: 식물<br/>
          점수: 0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          태그: 진달래속<br/>
          점수: 0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            태그: 비스코숨 철쭉<br/>
          점수: 0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            태그: 진한 주황색<br/>
          점수: 0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>베타에서 새 명시 모델 사용 가능</strong>
      <p>
        베타로 실행되는 명시 모델은 이미지에 포르노 컨텐츠가 포함되어 있는지와 일반 용도로 부적절한지 여부를 분류합니다. 통합 분석을 위해 기타 모델에 명시 모델을 포함시킬 수 있습니다. 예를 들어, 이미지 태그 및 이미지에 명시 컨텐츠가 포함되는지 여부를 리턴하려면 요청에 `default` 및 `explicit` 분류자 ID를 모두 포함하십시오.
      <p>
API 호출에 대한 세부사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#classify-images)에서 **이미지 분류** 메소드를 참조하십시오. </p>
    </li>
    <li>
      <strong>대형 파일 크기 지원</strong>
      <p>
        <strong>이미지 분류</strong> 메소드는 이제 최대 10MB의 이미지 파일과 최대 100MB의 .zip 파일을 지원합니다.
    </li>
    <li>
      <strong>분류자 ID 전달 시에 배열이 필요함</strong>
      <p>
        API는 이제 **이미지 분류** 메소드의 **매개변수** 오브젝트의 일부로서 `classifier_ids`에서 전달될 때 배열을 적용합니다. 이전에는 분류자 ID를 문자열로서 전달할 수 있었습니다. 자세한 정보는 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#classify-images)의 매개변수 설명과 예제 파일을 참조하십시오.
      </p>
    </li>
</ul>

### 2017년 9월 8일
{: #8september2017}

- **베타 유사성 검색 및 콜렉션이 마감됨**: 2017년 9월 8일 현재, 유사성 검색의 베타 기간이 마감되었습니다. 자세한 정보는 [Visual Recognition API – 유사성 검색 업데이트 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}를 참조하십시오.

### 2017년 6월 30일
{: #30june2017}

- **개선된 태그 지정**: 기본 분류자에 대해 훈련 이미지의 수를 늘렸습니다. 이러한 증가에 따라 이미지의 전체 '장면'을 정확하게 인식하는 기능이 개선되었습니다. 세부사항은 [일반 태그 지정 기능에 대한 추가 개선사항 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}을 참조하십시오.
- **추가된 언어**: **이미지 분류** 메소드는 이제 영어, 아랍어, 스페인어, 일본어와 함께 한국어, 이태리어, 독일어를 지원합니다.

    API 호출에 대한 세부사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}의 **이미지 분류** 메소드를 참조하십시오.

### 2017년 5월 16일
{: #16may2017}

- **새 음식 분류자 사용 가능: 베타**

    새 베타 음식 인식 모델은 음식 항목의 이미지에 대한 개선된 특수성과 정확성을 제공합니다. **이미지 분류** 메소드를 사용하면 이 새로운 "음식" 분류자를 `classifier_ids` 매개변수에 추가할 수 있습니다.

### 2017년 4월 5일
{: #5april2017}

- **새 {{site.data.keyword.visualrecognitionshort}} 도구 사용 가능: 베타**

    새 베타 기능인 {{site.data.keyword.visualrecognitionshort}} 도구는 [https://watson-visual-recognition.ng.bluemix.net/ ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}에서 사용 가능합니다. 이 도구를 사용하면 {{site.data.keyword.visualrecognitionshort}} 서비스 관련 작업을 보다 쉽게 수행하는 데 도움이 됩니다. {{site.data.keyword.cloud_notm}} API 키를 입력하면 GUI를 사용하여 일반 태그 지정 및 얼굴 감지 기능에 액세스할 수 있습니다. 또한 코딩을 수행하지 않고도 API 키와 연관된 사용자 정의 분류자를 완벽하게 작성, 재훈련 및 삭제할 수도 있습니다.

### 2017년 3월 8일
{: #8march2017}

- **일반 분류자 태그 지정에 대해 업데이트된 언어 지원**

    일반 분류자는 이제 지원되는 모든 언어에서 태그를 리턴합니다.

- **알려진 문제**

    **FIXED 04-13-2017**: 상태 확인을 위해 훈련 및 재훈련이 진행 중인 동안 `GET /classifiers`를 반복 호출하면 훈련 작업이 강제 종료될 수 있습니다. 이 문제를 임시로 해결하려면 `GET /classifiers/{classifier_id}`를 사용하여 새 분류자의 상태를 폴링하십시오. 다시 말하면, 모든 분류자를 가져오고 이 문제를 트리거할 수 있는 `GET /classifiers` 대신에 단일 분류자 ID에 대해 분류자 `GET`을 사용하십시오. 참고로, `GET /classifiers/{classifier_id}`는 속도도 더 빠릅니다.

### 2016년 12월 15일
{: #15december2016}

- **개선된 일반 분류자 태그 지정**

    - 일반 분류자의 딥 러닝 알고리즘이 업데이트되었습니다. 모든 언어에 대해 태그 품질이 상당히 개선되었으며, 서비스가 리턴하는 영어 태그의 볼륨이 상당히 증가되었습니다. 이러한 고품질 태그 출력은 자체 사용자 정의 분류자를 작성할 때도 사용 가능합니다.
    - 색상 태그 지정이 추가되었습니다. 서비스는 이제 이미지에서 맨 위의 1 - 2개 색상을 리턴합니다.

- **알려진 문제**

    - EXIF 메타데이터 태그와 함께 데모에 제출된 이미지가 서비스에 대해 올바르게 방향(가로 대 세로)을 지정하지 않습니다. iPhone 업로드된 이미지에는 EXIF 메타데이터 태그가 포함될 수 있습니다. 이에 대한 임시 해결책은 EXIF 메타데이터 태그에 의존하여 이미지의 방향을 지정하지 않도록 이미지 메타데이터를 업데이트하는 것입니다. 보통은 단지 컴퓨터에서 이미지를 열고 이를 저장함으로써 이 작업을 수행할 수 있습니다. 예를 들어, Mac에서는 미리보기에서 열기를 수행한 후에 이미지를 저장하면 올바른 방향 태그가 설정됩니다.
    - 8, 3 또는 6의 [EXIF 태그 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://en.wikipedia.org/wiki/Exif){: new_window} 값으로 {{site.data.keyword.visualrecognitionshort}} 서비스에 이미지를 전송하면 대기 시간이 추가될 수 있습니다. 이 서비스는 이미지의 픽셀을 인코딩된 관점으로 회전시킵니다. {{site.data.keyword.visualrecognitionshort}} 태스크에 중요하지 않은 경우에는 EXIF 헤더를 제거하거나 이미지를 미리 회전시켜서 시간을 절약할 수 있습니다.

### 2016년 12월 1일
{: #1december2016}

- **새 가격**

    {{site.data.keyword.IBM_notm}}은 {{site.data.keyword.visualrecognitionshort}} 서비스에서 사용자 정의 분류자의 가격을 낮게 책정했으며 무료 플랜에서 사용 가능한 항목을 늘렸습니다. 자세한 정보는 [{{site.data.keyword.visualrecognitionshort}} 가격 페이지](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)를 참조하십시오.

### 2016년 10월 7일
{: #7october2016}

- **얼굴 감지 개선사항**

    서비스에는 `GET` 및 `POST /v3/detect_faces` 메소드의 응답을 개선시키는 새 얼굴 감지 알고리즘이 있습니다. 이 서비스는 낮은 신뢰도의 연령, 이름 및 성별 얼굴 감지의 필터링을 조정했습니다. 결과적으로, 추가로 얼굴이 감지되며 보다 큰 범위의 신뢰도가 리턴됩니다.

### 2016년 9월 8일
{: #8september2016}

- **유사성 검색 베타**

    사용자는 이제 이미지의 자체 콜렉션을 업로드하고 이미지를 사용하여 해당 콜렉션에서 유사한 이미지를 검색할 수 있으며, 이 서비스는 최상위 100개의 가장 유사한 이미지를 리턴합니다. 유사성 검색은 임의의 용도로 활용될 수 있으며, 각각 최대 100만개 이미지의 콜렉션에 대해 서비스의 사용자 정의된 훈련이 가능합니다. 새 유사성 검색 기능의 사용에 대한 자세한 정보는 [튜토리얼](/docs/services/visual-recognition/tutorial-collections.html) 및 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window} 페이지를 참조하십시오.

- **텍스트 인식이 이제 베타를 마감함**

    `POST` 및 `GET /v3/recognize_text` 메소드는 마감된 베타로 돌아갔습니다. {{site.data.keyword.IBM_notm}}은 다른 오픈 베타에 대한 현재 플랜 없이 서비스를 사용하는 베타 클라이언트를 계속 지원할 수 있기를 기대합니다. 

### 2016년 8월 1일

- **출시 기념 특별가 종료**

    사용자 정의 분류자 훈련 및 재훈련, 사용자 정의 이미지 분류 및 사용자 정의 분류자 스토리지는 더 이상 무료가 아닙니다. 가격에 대한 정보는 {{site.data.keyword.visualrecognitionshort}} 서비스 [가격 페이지](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block)를 참조하십시오.

### 2016년 7월 5일
{: #5july2016}

- **사용자 정의 분류자 업데이트**

    사용자 정의 분류자는 더 이상 고정된 훈련 데이터 세트로 제한되지 않습니다. 사용자는 이제 기존 분류자를 새 이미지로 업데이트하거나 긍정 또는 부정 예제 분류자를 기존의 훈련된 분류자에 더 추가할 수 있습니다. Watson이 학습할 수 있도록 추가적인 예제 이미지를 제공함으로써 이 서비스는 사용자의 분류자를 보다 정확하게 만들 수 있습니다. 사용자 정의 분류자는 이제 시간의 흐름에 따른 지속적 학습이 가능하며, 계속해서 시각적 정보를 보다 잘 이해할 수 있게 됩니다.

- **알려진 문제**

    **FIXED 04-13-2017**: 기존 분류자를 업데이트할 때 사용자가 30 또는 90초 후에 500개의 오류 코드를 받을 수 있습니다. 오류에도 불구하고, 재훈련 요청이 정상적으로 완료될 가능성이 많습니다. 최소한 2분 동안 기다린 후에 `GET classifiers/{classifier\_id}` 메소드를 사용하여 분류자의 상태를 확인하십시오. 상태가 "준비"이며 "재훈련됨" 시간소인이 업데이트된 경우에는 500개 코드를 생성한 재훈련 요청이 성공한 것입니다. 혹은 "재훈련된" 시간소인이 업데이트되지 않은 경우, 재훈련이 실패한 이유를 알리는 설명이 응답에 추가되며 서비스는 재훈련 요청이 발행되기 전의 이전 버전으로 분류자를 되돌립니다.

### 2016년 5월 20일
{: #20 may 2016}

이는 {{site.data.keyword.visualrecognitionshort}} 서비스의 GA(General Availability) 릴리스입니다. 이 릴리스에서는 서비스의 버전 3이 도입되며, 이는 파괴적 변경사항입니다. 이 릴리스는 더 이상 사용되지 않는 AlchemyVision 서비스의 기능을 구현합니다.

서비스가 베타인 동안 작성된 사용자 정의 분류자는 서비스의 GA 인스턴스에서 재작성되어야 합니다.

{{site.data.keyword.visualrecognitionshort}} 서비스가 다음과 같이 변경되고 업데이트되었습니다.

- **버전 날짜** 이 릴리스의 기능을 활용하려면 `2016-05-20`을 `version` 매개변수의 값으로 사용하십시오.
- **클래스 및 분류자:** 단일 분류자를 이제는 "클래스"라고 합니다. GA에서는 클래스의 그룹을 "분류자"라고 합니다.
- **분류:** `POST` 또는 `GET /v3/classify` 메소드를 사용하여 기본 클래스로 다양한 대상과 장면을 빠르고 정확하게 식별할 수 있습니다.
- **얼굴 감지:** `POST` 또는 `GET /v3/detect_faces` 메소드를 사용하여 이미지에서 얼굴을 감지하고 이에 대한 정보를 가져올 수 있습니다(예: 이미지에서 얼굴이 차지하는 위치 및 각 얼굴의 예상된 연령 범위와 성별). 이 서비스는 이름으로 많은 유명 인사를 식별할 수도 있으며, 사용자가 상위 레벨 개념으로 흥미로운 집계를 수행할 수 있도록 지식 그래프를 제공할 수 있습니다. 
- **다면 사용자 정의 분류자:** 이제 여러 클래스로 정의된 매우 특수한 분류자를 작성하고 훈련시킬 수 있습니다. 예를 들어, "new\_cars" 및 "red\_cars" 클래스로 정의된 "new\_red\_car" 분류자를 작성할 수 있습니다. 다면 분류자 작성에 대해 자세히 학습하려면 [훈련 데이터의 구조](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure)를 참조하십시오.
- **비동기 훈련:** 사용자 정의 분류자의 훈련이 이제 비동기이므로, 사용자 정의 분류자가 백그라운드에서 계속해서 학습하는 동안 훈련 호출이 빠르게 완료됩니다. 사용자 정의 분류자의 훈련 상태를 확인하고 언제 사용 가능한지 알아보려면 `GET /v3/classifiers/{classifier_id}` 메소드를 호출하고 `status` 응답 매개변수를 확인하십시오.

### 2015년 12월 2일
{: #2december2015}

{{site.data.keyword.visualrecognitionshort}} 서비스의 최신 릴리스는 {{site.data.keyword.visualrecognitionshort}} API의 새 버전(v2)이 도입된 파괴적 변경사항입니다. {{site.data.keyword.visualrecognitionshort}} 서비스의 버전 1은 서비스가 베타를 종료할 때까지 사용 가능합니다.

API의 버전 2 사용을 바로 시작하려면 다음 변경사항을 반영하는 코드를 이해하고 업데이트하십시오.

- 서비스의 버전 1에서는 레이블로 이미지를 분석했습니다. 서비스의 버전 2에서는 레이블을 **분류자**라고 합니다. 분류자에는 `classifier_id` 매개변수로 표시된 고유 분류자 ID 및 `name` 매개변수로 표시된 단축 이름이 있습니다.
- 이미지 분석을 위한 `POST /v1/recognize` 메소드는 이제 [`POST /v2/classify` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window} 메소드입니다. `labels_to_check` 매개변수는 `classifier_ids`로 이름이 변경되었습니다.
- V1에서 레이블의 목록을 검색하기 위한 `GET /v1/tag/labels` 메소드는 이제 분류자의 목록을 검색하기 위한 [`GET /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window} 메소드입니다.
- 분류자 목록의 검색에 추가하여, 새 [`GET /v2/classifiers/{classifier_id}` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window} 메소드로 특정 분류자에 대한 세부사항을 검색할 수도 있습니다.
- 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2를 사용하여 새 [`POST /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window} 메소드로 사용자 정의 분류자를 작성할 수 있습니다. 사용자 정의 분류자 작성에 대해 자세히 학습하려면 [사용자 정의 분류자 작성](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)을 참조하십시오.
- 또한 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2를 사용하여 새 [`DELETE /v2/classifiers` ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window} 메소드로 사용자 정의 분류자를 삭제할 수도 있습니다.
- 베타 {{site.data.keyword.visualrecognitionshort}} API의 버전 2에서는 `version` 매개변수가 필요합니다. `MM-DD-YYYY` 형식으로 사용할 API 버전의 릴리스 날짜를 지정하십시오.
