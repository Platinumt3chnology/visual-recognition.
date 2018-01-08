---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-27"

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

# 이미지에서 텍스트 인식

{: shortdesc}

## 시작하기 전에
{: #copy-credentials}

이 튜토리얼의 "시작하기 튜토리얼"에서 복사한 신임 정보를 사용하십시오. 서비스 인스턴스를 작성하지 않은 경우에는 [시작하기 전에](/docs/services/visual-recognition/getting-started.html#prerequisites) 절에서 해당 단계를 실행하십시오. 

## 1단계: 이미지에서 텍스트 인식
{: #recognize-text}

1.  샘플 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/" download="">...<img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 예제 이미지를 다운로드하십시오. 
1.  `POST /v3/recognize_text` 메소드에 대해 다음 명령을 실행하여 이미지를 업로드하고 분석하십시오. 고유 이미지를 사용하는 경우, 최대 크기는 2MB입니다. 
    - `{api-key}`를 이전에 복사한 서비스 신임 정보로 대체하십시오. 
    - 이미지가 저장된 위치를 지시하도록 images\_file의 위치를 수정하십시오. 

    ```bash
    curl -X POST --form "images_file=@prez.jpg" \
    "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/recognize_text?api_key={api-key}&version=2016-05-20"
    ```

    응답에는 위치, 연령 추정치, 성별, ID 및 유형 계층 구조(서비스에서 해당 얼굴을 인식하는 경우) 및 각각에 대한 점수가 포함됩니다. 

    점수의 범위는 0 - 1이며, 보다 높은 점수는 보다 큰 상관 관계를 표시합니다. 모든 얼굴이 감지되지만 얼굴이 10개가 넘는 이미지의 경우에는 연령 및 성별 신뢰 점수가 점수 0으로 리턴될 수 있습니다. 


    ```json
    {
      "images_processed": 1,
      "images": [
        {
          "image": "string",
          "text": "string",
          "words": [
            {
              "word": "string",
              "text_location": {
                "width": 0,
                "height": 0,
                "left": 0,
                "top": 0
              },
              "score": 0,
              "line_number": 0
            }
          ]
        }
      ]
    }
    {: codeblock}

## 다음 단계

{{site.data.keyword.visualrecognitionshort}}에서 기본 분류자를 사용하는 방법에 대한 기본사항을 이해했습니다. 이제 심층 학습을 수행합니다.

- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/){: new_window}에서 API에 대해 읽어봅니다.

### 저작자표시
{: #attributions}

이 페이지에 사용된 모든 이미지는 Flikr에서 가져왔으며 [Creative Commons Attribution 2.0 라이센스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://creativecommons.org/licenses/by/2.0/deed.en){: new_window} 하에서 사용됩니다. 이러한 이미지는 변경되지 않았습니다.
