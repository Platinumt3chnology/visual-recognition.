---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-13"

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

# 자연 환경에서 텍스트 인식

베타 텍스트 모델을 사용하여 이미지에서 영문 텍스트를 감지하고 이를 인식할 수 있습니다. 텍스트 모델은 문서의 조밀한 텍스트가 아닌 이미지의 인쇄된 장면 텍스트를 인식하도록 디자인되었습니다. 

텍스트 모델은 베타 기능이며 프로덕션 환경에서 사용하는 용도는 아닙니다. 자세한 정보는 [릴리스 정보](/docs/services/visual-recognition/release-notes.html#beta)의 "베타 기능"을 참조하십시오.
{: tip}

텍스트 모델은 짧은 텍스트 문자열에서 최상으로 작동됩니다. 예를 들어, 텍스트 모델의 일반적인 사용은 도로 표지판 읽기입니다. 

![감지된 단어를 중심으로 경계 상자가 있는 도로 표지판](images/road-sign-text-detection.png)

![도로 표지판 이미지에서 감지된 단어 및 신뢰 점수](images/road-sign-text-response.png)

흰색 상자는 모델이 이미지에서 감지한 각각의 단어를 예시합니다. 

## 응답

응답에는 감지된 문자열이 포함되며, 해당 문자열 내의 각 단어는 다음 정보로 식별됩니다. 

- 감지된 단어
- 감지된 단어의 정확도로 신뢰를 표시하는 점수
- 단어를 중심으로 경계 상자의 위치. 상자는 단어가 이미지에서 차지하는 위치를 표시합니다. 
- 단어가 발견된 라인 번호

## 올바른 텍스트 인식을 위한 가이드라인

다음 가이드라인을 준수하면 이미지의 텍스트를 보다 잘 인식할 수 있습니다. 

- 텍스트는 제품 코드 등의 문자열이 아니라 주로 전체 단어입니다. 이 모델은 개별 문자가 아닌 단어를 인식하며, 한 문자의 "단어"나 숫자를 버릴 수 있습니다. 
- 텍스트는 고급 형식의 글꼴이 아닌 표준 글꼴로 인쇄됩니다. 예를 들어, 자동차 번호판의 텍스트나 영화 포스터의 제목은 인식되지 않을 수 있습니다. 마찬가지로, 손으로 쓰여진 텍스트도 인식되지 않을 수 있습니다. 
- 텍스트는 이미지의 최소한 5% 이상을 차지합니다. 
- 텍스트의 기울기는 수평으로부터 45도를 초과하지 않습니다. 베타 텍스트 모델은 EXIF 태그를 읽고 이미지를 회전시킵니다. 그러나 처리량을 최대화하려면 서비스에 의한 회전이 필요 없는 이미지(EXIF **방향** 태그가 `1`로 설정됨)를 전송하십시오. 
- 텍스트 모델은 영어 단어로 학습됩니다. 기타 언어의 텍스트는 인식되지 않을 수 있습니다. 

## 다음 단계

[API 탐색기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://text-model-api-explorer.mybluemix.net/apis/visual-recognition-v3#/Text){: new_window}의 API와 익숙해지십시오.

텍스트 모델에 대한 질문이나 의견이 있으면 Kevin Gong(kgong@us.ibm.com)에게 문의하십시오. 

---

기본 [문서](/docs/services/visual-recognition/index.html)로 이동하십시오. 
