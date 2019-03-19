---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: Visual Recognition languages,language support,supported languages

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

# 지원되는 언어

## 이미지 분류
{: #language-support}

{{site.data.keyword.visualrecognitionfull}}의 **이미지 분류** 메소드는 영어(`en`), 아랍어(`ar`), 독일어(`de`), 스페인어(`es`), 프랑스어(`fr`), 이탈리아어(`it`), 일본어(`ja`), 한국어(`ko`), 브라질 포르투갈어(`pt-br`), 중국어(간체)(`zh-cn`), 대만어(`zh-tw`)를 지원합니다. 

이러한 언어들은 모든 기본 제공 모델인 `default`(일반 모델이라고도 함), `food`, `explicit`의 출력 클래스에서 사용됩니다. 

API 호출에 대한 세부사항은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}에서 **이미지 분류** 메소드를 참조하십시오. 

## 얼굴 감지
{: #detect_faces}

**얼굴 감지** 메소드는 성별에 대한 영어 단어("Male" 및 "Female")의 번역을 응답에 리턴합니다. **Accept-Language** 요청 헤더로 언어를 설정하십시오. 

자세한 내용은 [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}에서 **얼굴 감지** 메소드를 참조하십시오.

