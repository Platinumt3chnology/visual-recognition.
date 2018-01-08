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

# 사용자 정의 분류자 작성

"시작하기 튜토리얼"에서 이미지의 분류가 완료되면 사용자 정의 분류자(또는 모델)의 학습 및 작성이 준비된 것입니다. 사용자 정의 분류자를 사용하면 비즈니스 요구사항에 맞게 이미지를 분류할 수 있도록 {{site.data.keyword.visualrecognitionshort}} 서비스를 학습시킬 수 있습니다.
{: shortdesc}

## 1단계: 신임 정보 복사
{: #copy-credentials}

"시작하기 튜토리얼"에서 복사한 신임 정보를 사용하십시오. 서비스 인스턴스를 작성하지 않은 경우에는 [시작하기 전에](/docs/services/visual-recognition/getting-started.html#prerequisites) 절에서 해당 단계를 모두 실행하십시오. 

## 2단계: 사용자 정의 분류자 작성
{: #create}

{{site.data.keyword.visualrecognitionshort}}은 새 다면 분류자를 작성하기 위해 사용자가 업로드한 예제 이미지에서 학습할 수 있습니다. 각각의 예제 파일은 해당 호출의 기타 파일에 대해 학습되며, 긍정 예제는 클래스로서 저장됩니다. 이러한 클래스는 그룹화되어 단일 분류자를 정의하고 고유 점수를 리턴합니다. 부정 예제 파일은 클래스로서 저장되지 않습니다. 

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/beagle.zip" download="beagle.zip">beagle.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/husky.zip" download="husky.zip">husky.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>, <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/golden-retriever.zip" download="golden-retriever.zip">golden-retriever.zip <img src="../../icons/launch-glyph.svg" alt="외부링크 아이콘 " title="외부 링크 아이콘" class="style-scope doc-content"></a> 및 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/cats.zip" download="cats.zip">cats.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 예제 학습 파일을 다운로드하십시오. 
1.  다음 명령으로 `POST /v3/classifiers` 메소드를 호출하십시오. 이는 학습 데이터를 업로드하고 `dogs` 분류자를 작성합니다. 
    - `{api-key}`를 첫 번째 단계에서 복사한 서비스 신임 정보로 대체하십시오. 
    - .zip 파일이 저장된 위치를 지시하도록 `{class}_positive_examples`의 위치를 수정하십시오. 

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

    긍정 예제 파일 이름에는 접미부 `_positive_examples`가 필요합니다. 이 예제에서 파일 이름은 `beagle_positive_examples`, `goldenretriever_positive_examples` 및 `husky_positive_examples`입니다. 접두부(beagle, goldenretriever 및 husky)는 클래스의 이름으로서 리턴됩니다.
    {:tip }

    응답에는 새 분류자 ID 및 상태가 포함됩니다. 예를 들어, 다음과 같습니다. 

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

1.  `ready` 상태가 보일 때까지 학습 상태를 주기적으로 확인하십시오. 학습이 즉시 시작되며 시용자가 분류자를 조회하기 전에 종료되어야 합니다. `{api  key}` 및 `{classifier_id}`를 사용자 고유 정보로 대체하십시오. 

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 3단계: 기존 사용자 정의 분류자 업데이트

무료 API 키로는 사용자 정의 분류자를 업데이트할 수 없습니다. 무료 키가 있으면 표준 플랜으로 업그레이드할 수 있습니다. 세부사항은 [계획 변경](https://console.bluemix.net/docs/pricing/changing_plan.html)을 참조하십시오.
{: tip}

클래스를 분류자에 추가하거나 이미지를 기존 클래스에 추가하여 사용자 정의 분류자를 업데이트할 수 있습니다. 여기서는 분류 가능한 "개" 유형에 *달마티안* 클래스를 추가하여 2단계에서 작성된 분류자를 개선합니다. 또한 고양이 이미지를 "개" 분류자에 대해 설정된 부정 예제에 추가합니다. 

1.  <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/dalmatian.zip" download="dalmatian.zip">dalmatian.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 및 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/more-cats.zip" download="more-cats.zip">more-cats.zip <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 샘플 학습 파일을 다운로드하십시오. 
1.  다음 cURL 명령으로 `POST /v3/classifiers/{classifier_id}` 메소드를 호출하십시오. 학습 데이터를 업로드하고 분류자 "dogs\_1941945966"을 업데이트합니다. 
    - `{api-key}`를 첫 번째 단계에서 복사한 서비스 신임 정보로 대체하십시오. 
    - `{classifier_id}`를 업데이트할 분류자의 ID로 대체하십시오. 
    - .zip 파일이 저장된 위치를 지시하도록 `{class}_positive_examples`의 위치를 수정하십시오. 

    ```bash
    curl -X POST \
    --form "dalmatian_positive_examples=@dalmatian.zip" \
    --form "negative_examples=@more-cats.zip" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    기존 "개" 분류자가 동일한 classifier_id의 재학습된 분류자로 대체됩니다. 응답은 새 클래스 세트 및 현재 상태를 나열합니다. 예를 들어, 다음과 같습니다. 

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

    학습이 즉시 시작됩니다. 새 학습이 사용 가능하면 상태가 `ready`로 변경됩니다. 

    현재 상태 이후 `ready` 상태까지는 다른 재학습 요청을 실행하지 마십시오. 분류자를 재학습하기 위한 다중 요청은 단일 재학습 효과의 결과를 가져옵니다. `retrained`라고 하는 시간소인은 분류자 재학습이 완료된 마지막 시간을 표시합니다. 분류자를 재학습하는 동안 `/classify` 메소드를 호출하면 분류자의 이전 정의가 사용됩니다.
    {: tip}
1.  `ready` 상태가 보일 때까지 학습 상태를 주기적으로 확인하십시오. `{api  key}` 및 `{classifier_id}`를 사용자 고유 정보로 대체하십시오. 

    ```bash
    curl -X GET \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

## 4단계: 사용자 정의 분류자로 이미지 분류
{: #classify}

새 분류자가 준비되면 이를 호출하여 어떻게 수행되는지 확인하십시오. 

1.  새 분류자 및 일반 모델 분류자(이는 `default` classifier_id를 사용함) 모두에 대해 `classifier_id` 등의 호출에 대한 매개변수가 포함된 `myparams.json`이라고 하는 JSON 파일을 작성하십시오. 단순 JSON 파일은 아래와 같이 보일 수 있습니다. 

    ```json
    {
      "classifier_ids": ["dogs_1941945966", "default"]
    }
    ```
    {: codeblock}

1.  <a target="_blank" href="https://github.com/watson-developer-cloud/doc-tutorial-downloads/raw/master/visual-recognition/dogs.jpg" download>dogs.jpg <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>를 다운로드하십시오. 
1.  `POST /v3/classify` 메소드를 사용하여 사용자 정의 분류자를 테스트하십시오. 다음 예제는 "dogs\_1941945966" 분류자에 대해 `dogs.jpg` 이미지를 분류합니다. 
    - `{api-key}`를 첫 번째 단계에서 복사한 서비스 신임 정보로 대체하십시오. 

    ```bash
    curl -X POST \
    --form "images_file=@dogs.jpg" \
    --form "parameters=@myparams.json" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classify?api_key={api-key}&version=2016-05-20"
    ```
    {: pre}

    기본 제공 일반 모델에 대해서만 분류하려면 `parameters` 매개변수를 생략하십시오.
    {: tip}

    응답에는 분류자, 해당 클래스 및 각 클래스에 대한 점수가 포함됩니다. 점수의 범위는 0 - 1이며, 보다 높은 점수는 보다 큰 상관 관계를 표시합니다. 높은 점수의 클래스가 식별된 경우, `/v3/classify` 호출은 기본적으로 낮은 점수의 클래스를 제외시킵니다. 호출에서 `threshold` 매개변수에 대한 부동 소수점 값을 지정하여 표시할 최소 점수를 설정할 수 있습니다. 

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

1.  결과를 검토하십시오. 

모두 완료했습니다! {{site.data.keyword.visualrecognitionshort}}으로 사용자 정의 분류자를 작성하고 학습하고 조회했습니다. 

### 사용자 정의 분류자 삭제

정리된 인스턴스로 애플리케이션 개발을 시작하기 위해 사용자 정의 분류자를 삭제하고자 할 수 있습니다. 

분류자를 삭제하려면 `DELETE /v3/classifiers/{classifier_id}` 메소드를 호출하십시오. `{api_key)` 및 `classifier_id`를 사용자 고유 정보로 대체하십시오. 

```bash
curl -X DELETE \
"https://gateway-a.watsonplatform.net/visual-recognition/api/v3/classifiers/{classifier_id}?api_key={api-key}&version=2016-05-20"
```
{: pre}

## 다음 단계

이제 사용자 정의 분류자를 사용하는 방법에 대한 기본사항을 이해했으므로 심층 학습이 가능합니다. 

- [사용자 정의 분류자의 우수 사례 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2016/10/watson-visual-recognition-training-best-practices/){: new_window}에 대해 자세히 살펴봅니다. 
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}에서 API에 대해 읽어봅니다. 

### 저작자표시
{: #attributions}

이 페이지에 사용된 모든 이미지는 Flikr에서 가져왔으며 [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용됩니다. 이러한 이미지는 변경되지 않았습니다. 
