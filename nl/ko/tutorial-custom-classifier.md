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

# 사용자 정의 모델 작성
{: #tutorial-custom-classifier}

"시작하기 튜토리얼"에서 이미지 분석을 완료했으면 사용자 정의 모델을 훈련 및 작성할 준비가 된 것입니다. 사용자 정의 모델을 사용하면 비즈니스 요구사항에 맞게 이미지를 분류하도록 {{site.data.keyword.visualrecognitionshort}} 서비스를 훈련시킬 수 있습니다.
{: shortdesc}

## 1단계: 인증 정보 복사
{: #copy-credentials}

"시작하기 튜토리얼"에서 복사한 인증 정보를 사용하십시오. 서비스 인스턴스를 작성하지 않은 경우에는 [시작하기 전에](/docs/services/visual-recognition?topic=visual-recognition-getting-started-tutorial#prerequisites) 절에서 해당 단계를 모두 실행하십시오.

## 2단계: 사용자 정의 모델 작성
{: #create}

{{site.data.keyword.visualrecognitionshort}}은 새 다면 모델을 작성하기 위해 사용자가 업로드한 예제 이미지에서 학습할 수 있습니다. 각각의 예제 파일은 해당 호출의 기타 파일에 대해 훈련되며, 긍정 예제는 클래스로서 저장됩니다. 이러한 클래스는 그룹화되어 단일 모델을 정의하고 자체 점수를 리턴합니다. 부정 예제 파일은 클래스로서 저장되지 않습니다.

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="외부링크 아이콘 " title="외부 링크 아이콘"></a> 및 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a> 예제 훈련 파일을 다운로드하십시오.
1.  다음 명령으로 `POST /v3/classifiers` 메소드를 호출하십시오. 이 명령은 훈련 데이터를 업로드하고 `dogs` 사용자 정의 모델을 작성합니다. 
    - `{your_api_key}`를 첫 번째 단계에서 복사한 서비스 인증 정보로 대체하십시오. 
    - .zip 파일이 저장된 위치를 지시하도록 `{class}_positive_examples`의 위치를 수정하십시오.

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

    긍정 예제 파일 이름에는 접미부 `_positive_examples`가 필요합니다. 이 예제에서 파일 이름은 `beagle_positive_examples`, `goldenretriever_positive_examples` 및 `husky_positive_examples`입니다. 접두부(beagle, goldenretriever 및 husky)는 클래스의 이름으로서 리턴됩니다.
    {:tip }

    응답에는 새 분류자 ID 및 상태가 포함됩니다. 예를 들어, 다음과 같습니다.

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

1.  `ready` 상태가 보일 때까지 훈련 상태를 주기적으로 확인하십시오. 훈련은 즉시 시작되며 시용자가 모델을 조회할 수 있기 전에 종료되어야 합니다. `{your_api_key}` 및 `{classifier_id}`를 사용자의 정보로 대체하십시오. 

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 3단계: 기존 사용자 정의 모델 업데이트
{: #tutorial-custom-classifier-update}

클래스를 모델에 추가하거나 이미지를 기존 클래스에 추가하여 사용자 정의 모델을 업데이트할 수 있습니다. 여기서는 분류 가능한 "개" 유형에 *달마티안* 클래스를 추가하여 2단계에서 작성한 모델을 개선합니다. 또한 고양이 이미지를 "개" 사용자 정의 모델에 대해 설정된 부정 예제에 추가합니다. 

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a> 및 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a> 샘플 훈련 파일을 다운로드하십시오.
1.  다음 cURL 명령으로 `POST /v3/classifiers/{classifier_id}` 메소드를 호출하십시오. 이 명령은 훈련 데이터를 업로드하고 사용자 정의 모델 "dogs\_1941945966"을 업데이트합니다. 
    - `{your_api_key}`를 첫 번째 단계에서 복사한 서비스 인증 정보로 대체하십시오. 
    - `{classifier_id}`를 업데이트할 사용자 정의 모델의 ID로 대체하십시오. 
    - .zip 파일이 저장된 위치를 지시하도록 `{class}_positive_examples`의 위치를 수정하십시오.

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

    기존의 "개" 사용자 정의 모델이 동일한 classifier_id의 재훈련된 사용자 정의 모델로 대체됩니다. 응답은 새 클래스 세트 및 현재 상태를 나열합니다. 예를 들어, 다음과 같습니다.

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

    훈련이 즉시 시작됩니다. 새 훈련이 사용 가능하면 상태가 `ready`로 변경됩니다.

    현재 상태 이후 `ready` 상태까지는 다른 재훈련 요청을 실행하지 마십시오. 모델 재훈련 요청이 여러 개 있을 경우 재훈련은 한 번만 적용됩니다. `updated`라는 시간소인은 모델이 가장 최근에 업데이트된 시간을 표시합니다. 모델을 재훈련하는 동안 `/classify` 메소드를 호출하면 이전 모델 정의가 사용됩니다.
    {: tip}
1.  `ready` 상태가 보일 때까지 훈련 상태를 주기적으로 확인하십시오. `{your_api_key}` 및 `{classifier_id}`를 사용자의 정보로 대체하십시오. 

    ```bash
    curl -X GET -u "apikey:{your_api_key}" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
    ```
    {: pre}

## 4단계: 사용자 정의 모델로 이미지 분류
{: #tutorial-custom-classifier-classify}

새 모델이 준비되면 이 모델을 호출하여 어떻게 수행되는지 확인하십시오. 

1.  <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>를 다운로드하십시오.
1.  `POST /v3/classify` 메소드를 사용하여 사용자 정의 사용자 정의 모델 테스트하십시오. 다음 예제는 "dogs\_1941945966" 사용자 정의 모델 및 기본 제공 `default` 일반 모델에 대해 `dogs.jpg` 이미지를 분류합니다. 
    - `{your_api_key}`를 첫 번째 단계에서 복사한 서비스 인증 정보로 대체하십시오. 

    ```bash
    curl -X POST -u "apikey:{your_api_key}" \
    --form "images_file=@dogs.jpg" \
    --form "classifier_ids=dogs__1941945966,default" \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/classify?version=2018-03-19"
    ```
    {: pre}

    기본 제공 일반 모델에 대해서만 분류하려면 `classifier_ids` 매개변수를 생략하십시오.     {: tip}

    응답에는 분류자(모델), 해당 클래스 및 각 클래스에 대한 점수가 포함됩니다. 점수의 범위는 0 - 1이며, 보다 높은 점수는 보다 큰 상관 관계를 표시합니다. 높은 점수의 클래스가 식별된 경우, `/v3/classify` 호출은 기본적으로 낮은 점수의 클래스를 제외시킵니다. 호출에서 `threshold` 매개변수에 대한 부동 소수점 값을 지정하여 표시할 최소 점수를 설정할 수 있습니다.

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

1.  결과를 검토하십시오.

이제 다 마쳤습니다! {{site.data.keyword.visualrecognitionshort}}으로 사용자 정의 모델을 작성, 훈련 및 조회했습니다. 

### 사용자 정의 모델 삭제
{: #tutorial-custom-classifier-delete}

정리된 인스턴스로 애플리케이션 개발을 시작하기 위해 사용자 정의 모델을 삭제하고자 할 수 있습니다. 

모델을 삭제하려면 `DELETE /v3/classifiers/{classifier_id}` 메소드를 호출하십시오. `{your_api_key)` 및 `classifier_id`를 사용자의 정보로 대체하십시오. 

```bash
curl -X DELETE -u "apikey:{your_api_key}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?version=2018-03-19"
```
{: pre}

## 다음 단계
{: #tutorial-custom-classifier-next-steps}

사용자 정의 모델을 사용하는 기본적인 방법을 살펴보았으므로 이제 심층 학습을 수행할 수 있습니다. 

- [사용자 정의 분류자의 우수 사례 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}에 대해 학습합니다.
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition){: new_window}에서 API에 대해 읽어봅니다.

### 저작권
{: #tutorial-custom-classifier-attributions}

이 페이지에 사용된 모든 이미지는 Flikr에서 가져왔으며 [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용됩니다. 이러한 이미지는 변경되지 않았습니다.
