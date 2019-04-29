---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-07"

subcollection: tone-analyzer

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

# 개발자를 위한 개요
{: #overviewDevelopers}

{{site.data.keyword.toneanalyzershort}} 서비스의 기능은 HTTP REST(Representational State Transfer) API를 통해 액세스할 수 있습니다. 다양한 언어로 된 애플리케이션 개발을 단순화하기 위해 몇 가지 SDK(Software Development Kit) 또한 사용 가능합니다. 다음 절은 서비스를 사용한 애플리케이션 개발에 대한 개요를 제공합니다.
{: shortdesc}

## 서비스를 사용한 프로그래밍
{: #programming}

개별 텍스트의 어조를 분석하려는 경우에는 `GET` 또는 `POST /v3/tone` 메소드를 통해 서비스에 입력 텍스트를 전달합니다. 대화 내용을 분석하려는 경우에는 `POST /v3/tone_chat` 메소드를 통해 서비스에 입력을 전달합니다. 두 경우 모두 서비스는 분석을 JSON 형식으로 리턴합니다. 자세한 정보는 다음을 참조하십시오. 

-   [범용 엔드포인트 사용](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [고객 참여 엔드포인트 사용](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Software Development Kit 사용
{: #sdks}

{{site.data.keyword.toneanalyzershort}} 서비스에서 애플리케이션 개발을 단순화하는 데 SDK를 사용할 수 있습니다. 다수의 인기 있는 프로그래밍 언어 및 플랫폼에서 {{site.data.keyword.ibmwatson}} SDK를 사용할 수 있습니다. 

-   GitHub에서 SDK의 전체 목록 및 링크를 사용하는 데 대한 정보는 [ SDK](/docs/services/watson?topic=watson-using-sdks)를 참조하십시오. 
-   {{site.data.keyword.toneanalyzershort}} 서비스에 맞는 Node, Java, Python, Ruby 및 Go SDK의 모든 메소드에 대한 자세한 정보는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/tone-analyzer){: new_window}를 참조하십시오.

## 애플리케이션 개발에 대해 자세히 알아보기
{: #learn}

{{site.data.keyword.watson}} 서비스 및 {{site.data.keyword.cloud}} 관련 작업에 대한 자세한 정보는 다음 항목을 참조하십시오. 

-   {{site.data.keyword.watson}} 서비스 및 {{site.data.keyword.cloud_notm}} 관련 작업에 대한 소개는 [{{site.data.keyword.watson}} 및 {{site.data.keyword.cloud_notm}} 시작하기](/docs/services/watson?topic=watson-about)를 참조하십시오. 
-   모든 새 서비스 인스턴스는 인증을 위해 {{site.data.keyword.cloud_notm}} Identity and Access Management(IAM)를 사용합니다. 이전 서비스 인스턴스는 인증을 위해 기존 Cloud Foundry 서비스 인증 정보에서 `{username}` 및 `{password}`를 계속 사용할 수 있습니다. 서비스 인증에 대한 자세한 정보는 릴리스 정보의 [2018년 10월 30일 서비스 업데이트](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018)를 참조하십시오. 
-   {{site.data.keyword.toneanalyzershort}} 서비스에서 요청 로깅이 사용 안함으로 설정됩니다. 서비스는 `X-Watson-Learning-Opt-Out` 요청 헤더의 설정 여부와 관계 없이 요청 및 응답에서 데이터를 로깅하거나 보유하지 않습니다. 
