---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Text recognition,Visual Recognition beta Text model,Text model,recognize text

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}

# 이미지에서 텍스트 인식
{: #tutorial-recognize-text}

이 튜토리얼은 {{site.data.keyword.visualrecognitionshort}} 베타 텍스트 모델로 처음 호출하여 이미지에서 영문 텍스트를 감지하고 인식하는 방법을 안내합니다.
{: shortdesc}

텍스트 모델은 개인용 베타 기능이므로 모델을 호출하려면 {{site.data.keyword.IBM_notm}}에서 제공한 권한이 있어야 합니다. [액세스를 요청 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://datasciencex.typeform.com/to/nU6efl){: new_window}하십시오. 베타 기능에 대한 자세한 내용은 [릴리스 정보](/docs/services/visual-recognition?topic=visual-recognition-release-notes#beta)를 참조하십시오.
{: important}

## 시작하기 전에
{: #tutorial-recognize-text-prerequisites}

1.  {{site.data.keyword.Bluemix_notm}} Catalog에서 [{{site.data.keyword.visualrecognitionshort}}![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 페이지로 이동하십시오. 
    1.  무료 {{site.data.keyword.Bluemix_notm}} 계정을 등록하거나 로그인하십시오. 
    1.  **작성**을 클릭하십시오. 
- 서비스 인스턴스를 인증하기 위한 인증 정보 복사:
    1.  **표시**를 클릭하여 인증 정보를 확인하십시오. 
    1.  **API 키** 값을 복사하십시오. 

## 1단계: 이미지에서 텍스트 인식
{: #tutorial-recognize-text-recognize-text}

1.  다음 호출을 실행하여 [이미지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg){: new_window}에 있는 텍스트를 인식하십시오. `{your_api_key}`를 앞에서 복사한 API 키 값으로 대체하십시오. 

    ```bash
    curl -u "apikey:{your_api_key}"{: apikey} \
    "https://gateway.watsonplatform.net/visual-recognition/api/v3/recognize_text?url=https://watson-developer-cloud.github.io/doc-tutorial-downloads/visual-recognition/lookButDontTouch.jpg&version=2018-03-19"
    ```
    {: pre}

    응답에는 인식된 텍스트 및 텍스트에 있는 단어의 위치가 각 단어에 대한 신뢰도 점수와 함께 포함되어 있습니다. 위치 정보는 단어 주변에 경계 상자를 그리는 데 사용할 수 있습니다. 

    ```json
    {
      "images": [
        {
          "image": "lookButDontTouch.jpg",
          "text": "look but\ndont\ntouch",
          "words": [
            {
              "word": "look",
              "location": {
                "height": 651,
                "width": 1235,
                "left": 914,
                "top": 1591
              },
              "score": 0.9718,
              "line_number": 0
            },
            {
              "word": "but",
              "location": {
                "height": 651,
                "width": 939,
                "left": 2148,
                "top": 1591
              },
              "score": 0.9246,
              "line_number": 0
            },
            {
              "word": "dont",
              "location": {
                "height": 586,
                "width": 1594,
                "left": 1220,
                "top": 2240
              },
              "score": 0.5823,
              "line_number": 1
            },
            {
              "word": "touch",
              "location": {
                "height": 629,
                "width": 1701,
                "left": 1193,
                "top": 2824
              },
              "score": 0.8806,
              "line_number": 2
            }
          ]
        }
      ],
      "images_processed": 1
    }
    ```
    {: codeblock}

## 다음 단계

이미지에서 텍스트를 인식하는 기본적인 방법을 살펴보았습니다. 이제 심층 학습을 수행합니다. 

- [개요](/docs/services/visual-recognition?topic=visual-recognition-text-recognition-in-natural-scenes-beta-#text-recognition-in-natural-scenes-beta-)를 검토하십시오. 
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/visual-recognition-v3-text#recognize-text-in-an-image-get-beta){: new_window}에서 텍스트 모델 메소드를 살펴보십시오. 

### 저작권
{: #tutorial-recognize-text-attributions}

- [lookButDontTouch ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://unsplash.com/photos/WrvDSkS2yu4?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}는 [Lubo Minar ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://unsplash.com/@bubo){: new_window}에 의해 [Unsplash![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText){: new_window}에서 사용되었습니다.  이 이미지는 변경되지 않았습니다.
