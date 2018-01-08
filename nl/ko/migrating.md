---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# {{site.data.keyword.alchemyvisionshort}}에서 {{site.data.keyword.visualrecognitionshort}}으로 마이그레이션

2016년 5월 19일에 {{site.data.keyword.alchemyvisionshort}} 서비스는 더 이상 사용되지 않으며, 해당 기능은 {{site.data.keyword.visualrecognitionshort}}(GA)의 일부가 되었습니다. {{site.data.keyword.alchemyvisionshort}} 서비스에서 {{site.data.keyword.visualrecognitionshort}} 서비스로 {{site.data.keyword.Bluemix_notm}}에 배치된 애플리케이션을 마이그레이션하려면 코드를 업데이트하십시오.
{: shortdesc}

{{site.data.keyword.alchemyvisionshort}} 및 {{site.data.keyword.visualrecognitionshort}} 간의 다음 차이점은 애플리케이션 코드에 영향을 줄 수 있습니다. 

- **클래스 및 분류자:** {{site.data.keyword.alchemyvisionshort}}에서는 분석된 이미지가 "태그"로 레이블이 지정됩니다. {{site.data.keyword.visualrecognitionshort}}에서는 "태그"를 "클래스"라고 합니다. 클래스의 그룹을 "분류자"라고 합니다. {{site.data.keyword.alchemyvisionshort}}의 모든 기본 태그를 {{site.data.keyword.visualrecognitionshort}}에서 클래스로서 계속 사용할 수 있습니다. 
- **사용자 정의 분류자:** {{site.data.keyword.visualrecognitionshort}}을 사용하여 사용자 정의 분류자 및 클래스를 학습시키고 작성할 수 있습니다. 
- **일괄처리 입력:** {{site.data.keyword.visualrecognitionshort}}에서는 이제 압축(.zip) 파일의 이미지 파일을 제출하거나 JSON 문자열의 단일 이미지 URL을 제출하여 이미지 또는 이미지 URL의 일괄처리를 분류할 수 있습니다. 
- **언어 지정:** {{site.data.keyword.alchemyvisionshort}}에서 사용자는 조회 매개변수로서 태그 지정 호출의 언어를 지정했습니다. {{site.data.keyword.visualrecognitionshort}}에서 사용자는 `Accept-Language` 헤더에 분류 호출의 언어를 지정합니다. 
- **엔드포인트:** 다음 {{site.data.keyword.alchemyvisionshort}} 기능이 {{site.data.keyword.visualrecognitionshort}}의 GA 릴리스에서 새 엔드포인트에 포함되어 있습니다. 

| 기능 | {{site.data.keyword.alchemyvisionshort}} 엔드포인트(더 이상 사용되지 않음) | {{site.data.keyword.visualrecognitionshort}} 엔드포인트(GA) |
|---------------|--------------------|----------------|
| 기본 제공 분류자로 이미지 태그 지정 | `POST /image/ImageGetRankedImageKeywords`<br/>`GET /url/URLGetRankedImageKeywords` | `POST /v3/classify`<br/>`GET /v3/classify` |
| 얼굴, 연령 범위 및 성별 감지 | `POST /image/ImageGetRankedImageFaceTags`<br/>`GET /url/URLGetRankedImageFaceTags` | `POST /v3/detect_faces`<br/>`GET /v3/detect_faces` |
| HTML 또는 웹 사이트 URL에서 기본 이미지 추출 | `POST /html/HTMLGetImage`<br/>`GET /url/URLGetImage` | 독립형 엔드포인트를 통해서가 아니라 `/v3/classify` 및 `/v3/detect_faces` 메소드에 URL별로 이미지를 제공할 수 있습니다. |
