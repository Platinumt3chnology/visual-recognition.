---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: migrating Visual Recognition,migrating

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

# 마이그레이션
{: #migrating}

현재 모델(분류자)을 마이그레이션하려면 {{site.data.keyword.visualrecognitionshort}} 서비스의 새 인스턴스를 프로비저닝하십시오. 사용자 정의 모델의 경우 이전 모델에서 이미지가 있는 다른 모델(분류자)을 작성하여 모델을 재훈련하십시오.
{: shortdesc}

2018년 5월 23일 **이전에** 작성된 {{site.data.keyword.visualrecognitionfull}} 서비스 인스턴스는 `gateway-a.watsonplatform.net`이라는 호스트 URL을 사용합니다. 이러한 인스턴스를 계속 사용하려면 해당 인스턴스를 새로운 {{site.data.keyword.visualrecognitionshort}} 서비스 인스턴스로 마이그레이션해야 합니다.
{: deprecated}

1.  {{site.data.keyword.visualrecognitionshort}} 서비스의 다른 인스턴스를 작성하십시오. 
    1.  카탈로그에서 [{{site.data.keyword.visualrecognitionshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/visual-recognition){: new_window} 페이지로 이동하십시오. 
    1.  플랜을 선택하고 **작성**을 클릭하십시오. 
1.  새 인증할 인증 정보를 서비스 인스턴스로 복사하십시오. 
    1.  **관리** 페이지에서 **인증 정보 표시**를 클릭하십시오. 
    1.  `API Key` 값을 복사하십시오. 
1.  {{site.data.keyword.visualrecognitionshort}} 서비스의 새 인스턴스에서 [사용자 정의 모델을 다시 작성하고 재훈련](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier)하십시오. 
1.  서비스 호출 방법을 수정하십시오. 

    서비스 인스턴스에 대해 IAM(Identity and Access Management) 키 또는 액세스 토큰을 제공하십시오. 토큰은 정기적으로 갱신해야 하므로 뛰어난 보안을 제공하며 호출 시마다 서비스 인증 정보를 임베드하지 않고도 요청을 지원합니다. API 키는 기본 인증을 사용하며 만료되지 않습니다. 

    - IAM 토큰에 대한 자세한 정보는 [IAM 토큰을 사용한 인증](/docs/services/watson?topic=watson-iam#iam)을 참조하십시오. 
    - IAM API 키 사용에 대한 자세한 정보는 [API 참조서](https://{DomainName}/apidocs/visual-recognition/#authentication)를 참조하십시오. 
