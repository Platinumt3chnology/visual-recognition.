---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# 정보 보안
{: #information-security}

IBM은 당사의 고객과 파트너에게 혁신적인 데이터 개인정보처리방침, 보안 및 통제 솔루션을 제공하기 위해 노력하고 있습니다.
{: shortdesc}

**알림:**
고객은 유럽 연합(EU)의 일반 개인정보 보호법률(General Data Protection Regulation)을 포함한 다양한 법령과 규정을 준수해야 할 책임이 있습니다. 고객은 고객의 비즈니스에 영향을 줄 수 있는 관련 법령 및 규정에 대한 확인과 해석,
그러한 법령 및 규정의 준수를 위해 필요한 고객의 모든 조치와 관련하여 적절한 법률 자문을 받아야 할
단독 책임이 있습니다.

여기에서 설명하는 제품, 서비스 및 기타 기능은 일부 고객의 상황에는 해당되지 않을 수 있으며
그 가용성이 제한될 수 있습니다. IBM은 법률, 회계 또는 감사 관련 자문을 제공하지 않으며, IBM의 서비스나 제품 사용이 고객의 관련 법령이나 규정 준수를 보장한다는 진술이나 보증을 제공하지 않습니다.
작성된 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 리소스에 대해 GDPR 지원을 요청해야 하는 경우 다음을 참조하십시오. 

- EU의 경우 [EU에서 작성된 IBM Cloud Watson 리소스에 대한 지원 요청](/docs/services/watson?topic=watson-gdpr-sar#request-EU)을 참조하십시오. 
- EU 이외 지역의 경우 [EU 외부 리소스에 대한 지원 요청](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU)을 참조하십시오. 

## EU의 일반 개인정보 보호법률(GDPR)
{: #gdpr}

IBM은 당사의 고객과 파트너가 GDP를 준수할 수 있도록 혁신적인 데이터 개인정보처리방침, 보안 및 통제 솔루션을 제공하기 위해 노력하고 있습니다. 

IBM의 자체 GDPR 준비 과정 및 고객의 준수를 지원하기 위한 당사의 GDPR 기능과 오퍼링에 대해 알아보려면 [여기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/gdpr){: new_window}를 클릭하십시오. 

## {{site.data.keyword.visualrecognitionshort}}에서 데이터 레이블 지정 및 삭제
{: #gdpr-visrec}

### GDPR 보안 마이그레이션
{: #gdpr-visrec-update}

- **2018년 5월 22일**이전에 작성된 모든 {{site.data.keyword.visualrecognitionfull}} 서비스 인스턴스는 EU 개인정보 보호법률 EU 2016/679(GDPR)을 준수해야 하는 고객에게 적합하지 않습니다. 
- GDPR 적용 대상 고객은 **2018년 5월 22일**에 제공되는 [새로운 {{site.data.keyword.visualrecognitionshort}} 서비스 인스턴스로 마이그레이션](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating)하며 {{site.data.keyword.visualrecognitionshort}} 서비스에 대해 새로운 계약을 채택해야 합니다. 
- 고객이 새로운 {{site.data.keyword.visualrecognitionshort}} 서비스를 이용하려면 새로운 {{site.data.keyword.visualrecognitionshort}} 서비스를 프로비저닝하고 *새 인증 키*를 생성해야 합니다. 
- 고객이 새로운 {{site.data.keyword.visualrecognitionshort}} 서비스를 프로비저닝하지 않을 경우 IBM이 GDPR 적용 대상 고객을 대신하여 어떠한 개인 데이터도 처리하지 않음을 확인하십시오. 
- 2018년 5월 22일부터 2018년 10월 1일까지, 새로운 {{site.data.keyword.visualrecognitionshort}} 서비스로 이동하지 않는 고객의 데이터는 삭제됩니다. 

### 데이터 레이블 지정

개인 고객의 데이터를 여러 고객이 포함된 {{site.data.keyword.visualrecognitionshort}} 서비스 인스턴스에서 제거해야 하는 경우 먼저 데이터를 제공했을 수 있는 개개인에 대해 해당 데이터를 고유한 고객 ID와 연관시켜야 합니다. 

**분류자 작성** 메소드로 전송된 데이터에 대해 고객 ID를 지정하려면 **X-Watson-Metadata: customer_id** 특성을 요청 헤더에 포함시키십시오. 다음 예에서는 고객 ID `my_ID`를 요청과 연관시킵니다. 

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

고객 ID 문자열에는 멀티바이트 문자가 지원됩니다. 헤더(교육 중인 경우) 및 조회 매개변수(삭제 중인 경우)에서 URL 인코딩 문자여야 합니다. ID에는 영숫자와 밑줄(``_``) 문자가 포함될 수 있습니다. 다음 문자는 지원되지 않습니다. ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + 공백``

고객 ID 값을 작성하고 각 ID가 고유한지 확인할 책임은 사용자에게 있습니다.
{: important}

### 레이블 지정된 데이터 삭제

고객 ID와 연관된 데이터를 모두 삭제하려면 **레이블 지정된 데이터 삭제** 메소드를 사용하십시오. `customer_id={id}` 문자열을 요청과 함께 조회 매개변수로 전달해야 합니다. 다음 예에서는 고객 ID `my_ID`의 데이터를 모두 삭제합니다. 

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

**레이블 지정된 데이터 삭제** 메소드는 정보를 추가할 때 사용된 메소드와 관계없이 지정된 고객 ID와 연관된 데이터를 모두 삭제합니다. 고객 ID와 연관된 데이터가 없는 경우에는 이 메소드가 적용되지 않습니다. 

삭제 요청은 일괄적으로 처리되며 완료하는 데 최대 24시간이 걸릴 수 있습니다.
{: tip}

### 지원
{: #gdpr-visrec-support}

계정 담당자에게 직접 문의하거나, [https://ibm.biz/ibmcloudsupport ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/ibmcloudsupport){: new_window}에서 직접 지원 센터에 연락하십시오. 
