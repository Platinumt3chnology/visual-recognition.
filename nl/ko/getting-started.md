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
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 시작하기 튜토리얼

이 튜토리얼은 {{site.data.keyword.visualrecognitionfull}}의 일부 기본 제공 분류자를 사용하여 이미지를 분류한 후에 이미지에서 얼굴을 감지하는 방법을 안내합니다.
{: shortdesc}

## 시작하기 전에
{: #prerequisites}

- 서비스 인스턴스 작성: 
    - {: download} 이를 보는 경우에는 서비스 인스턴스가 작성된 것입니다. 이제 신임 정보를 가져오십시오. 
    - 서비스에서 프로젝트 작성: 
        1.  {{site.data.keyword.watson}} 개발자 콘솔 [서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/developer/watson/services){: new_window} 페이지로 이동하십시오. 
        1.  {{site.data.keyword.visualrecognitionshort}}을 선택하고 **서비스 추가**를 클릭한 후에 무료 {{site.data.keyword.Bluemix_notm}} 계정에 등록하거나 로그인을 수행하십시오. 
        1.  프로젝트 이름으로 `vision-tutorial`을 입력하고 **프로젝트 작성**을 클릭하십시오. 
- 서비스 인스턴스를 인증하기 위한 신임 정보 복사: 
    - {: download} (현재 보고 있는) 서비스 대시보드에서 다음을 수행하십시오. 
        1.  **서비스 신임 정보** 탭을 클릭하십시오. 
        1.  **조치** 아래에서 **신임 정보 보기**를 클릭하십시오. 
        1.  api-key 값을 복사하십시오.
        {: download}
    - 개발자 콘솔에 있는 **vision-tutorial** 프로젝트의 **신임 정보** 섹션에서 `"visual_recognition"`에 대해 `api-key` 값을 복사하십시오. 

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}}를 사용하는 경우에는 카탈로그의 [{{site.data.keyword.visualrecognitionshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/catalog/services/visual-recognition/){: new_window} 페이지에서 서비스 인스턴스를 작성하십시오. 서비스 신임 정보를 찾는 방법에 대한 세부사항은 [Watson 서비스에 대한 서비스 신임 정보 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}를 참조하십시오. 

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 1단계: 이미지 분류
{: #classify}

1.  샘플 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/fruitbowl.jpg" download="fruitbowl.jpg">fruitbowl.jpg <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 이미지를 다운로드하십시오. 
1.  다음 명령을 실행하여 이미지를 업로드하고 모든 기본 제공 분류자에 대해 이를 분류하십시오. 
    - `{api-key}`를 이전에 복사한 서비스 신임 정보로 대체하십시오. 
    - 이미지가 저장된 위치를 지시하도록 images\_file의 위치를 수정하십시오. 

    ```bash
    curl -X POST --form "images_file=@fruitbowl.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    {{site.data.keyword.Bluemix_notm}} 데디케이티드를 보유하는 경우, 여기의 `gateway-a.watsonplatform.net` 엔드포인트는 사용자의 서비스 엔드포인트가 아닐 수 있습니다. 서비스 대시보드의 **서비스 신임 정보** 페이지에서 `url`을 확인하십시오.
    {: tip}

    응답에는 일반 모델 또는 분류자(`default` classifier_id를 사용함), 이미지에서 식별된 클래스, 그리고 각 클래스에 대한 점수가 포함됩니다. 

    ```json
    {
     "custom_classes": 0,
      "images": [
        {
          "classifiers": [
            {
              "classes": [
                {
                  "class": "banana",
                  "score": 0.81,
                  "type_hierarchy": "/fruit/banana"
                },
                {
                  "class": "fruit",
                  "score": 0.922
                },
                {
                  "class": "mango",
                  "score": 0.554,
                  "type_hierarchy": "/fruit/mango"
                },
                {
                  "class": "olive color"
                  "score": 0.951
                },
                {
                  "class": "olive green color"
                  "score": 0.747
                }
              ],
              "classifier_id": "default",
              "name": "default"
            }
          ],
          "image": "fruitbowl.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

    신뢰 점수의 범위는 0 - 1이며, 보다 높은 점수는 보다 큰 상관 관계를 표시합니다. 기본적으로, `/v3/classify` 호출에는 점수가 `0.5` 미만인 클래스가 포함되지 않습니다. 

## 2단계: 이미지에서 얼굴 감지
{: #detect-faces}

{{site.data.keyword.visualrecognitionshort}}은 이미지에서 얼굴을 감지할 수 있습니다. 응답은 이미지에서 얼굴의 위치, 예상 연령 범위 및 각 얼굴의 성별 등과 같은 정보를 제공합니다. 

이 서비스는 이름으로 많은 유명 인사를 식별할 수도 있으며, 사용자가 상위 레벨 개념을 집계할 수 있도록 *지식 그래프*를 제공할 수 있습니다. 

1.  샘플 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/prez.jpg" download="prez.jpg">prez.jpg <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 이미지를 다운로드하십시오. 
1.  `POST /v3/detect_faces` 메소드에 대해 다음 명령을 실행하여 이미지를 업로드하고 분석하십시오. 고유 이미지를 사용하는 경우, 최대 크기는 2MB입니다. 
    - `{api-key}`를 이전에 복사한 서비스 신임 정보로 대체하십시오. 
    - 이미지가 저장된 위치를 지시하도록 images\_file의 위치를 수정하십시오. 

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    응답에는 위치, 연령 추정치, 성별, ID 및 유형 계층 구조(서비스에서 해당 얼굴을 인식하는 경우) 및 각각에 대한 점수가 포함됩니다. 

    점수의 범위는 0 - 1이며, 보다 높은 점수는 보다 큰 상관 관계를 표시합니다. 모든 얼굴이 감지되지만 얼굴이 10개가 넘는 이미지의 경우에는 연령 및 성별 신뢰 점수가 점수 0으로 리턴될 수 있습니다. 

    ```json
    {
      "images": [
        {
          "faces": [
            {
              "age": {
                "max": 54,
                "min": 45,
                "score": 0.364876
              },
              "face_location": {
                "height": 117,
                "left": 406,
                "top": 149,
                "width": 108
              },
              "gender": {
                "gender": "MALE",
                "score": 0.993307
              },
              "identity": {
                "name": "Barack Obama",
                "score": 0.982014
                "type_hierarchy": "/people/politicians/democrats/barack obama"
              }
            }
          ],
          "image": "prez.jpg"
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 다음 단계

{{site.data.keyword.visualrecognitionshort}}에서 기본 제공되는 기본 분류자를 사용하는 방법에 대한 기본사항을 이해했습니다. 이제 심층 학습을 수행합니다. 

- [사용자 정의 분류자를 빌드](/docs/services/visual-recognition/tutorial-custom-classifier.html)하는 방법에 대해 학습합니다. 
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}에서 API에 대해 읽어봅니다. 

### 저작자표시
{: #attributions}

- [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용된 Flikr 사용자 [Ryan Edwards-Crewe ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.flickr.com/photos/ryanec/){: new_window}의 [과일 바구니 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://flic.kr/p/JPHES){: new_window}. 이 이미지는 변경되지 않았습니다. 
- [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용된 Flikr 사용자 [dcblog ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.flickr.com/photos/12863058@N08/){: new_window}의 [obama ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://bit.ly/1T0DCl9){: new_window}. 이 이미지는 변경되지 않았습니다. 
