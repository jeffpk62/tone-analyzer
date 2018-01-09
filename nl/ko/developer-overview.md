---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-09"

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

# 개발자를 위한 개요
{: #overviewDevelopers}

{{site.data.keyword.toneanalyzershort}} 서비스의 기능은 HTTP REST(Representational State Transfer) API를 통해 액세스할 수 있습니다. 다양한 언어 및 환경에서의 애플리케이션 개발을 단순화하기 위해 몇 가지 SDK(Software Development Kit) 또한 사용 가능합니다. 다음 절은 서비스를 사용한 애플리케이션 개발에 대한 개요를 제공합니다.
{: shortdesc}

## 서비스를 사용한 프로그래밍
{: #programming}

개별 텍스트의 어조를 분석하려는 경우에는 `GET` 또는 `POST /v3/tone` 메소드를 통해 서비스에 입력 텍스트를 전달합니다. 대화 내용을 분석하려는 경우에는 `POST /v3/tone_chat` 메소드를 통해 서비스에 입력을 전달합니다. 두 경우 모두 서비스는 분석을 JSON 형식으로 리턴합니다. 

자세한 정보는 [일반 목적 엔드포인트 사용](/docs/services/tone-analyzer/using-tone.html) 및 [고객 참여 엔드포인트 사용](/docs/services/tone-analyzer/using-tone-chat.html)을 참조하십시오. 

## Software Development Kit 사용
{: #sdks}

{{site.data.keyword.toneanalyzershort}} 서비스는 단순화된 애플리케이션 개발을 위한 몇 가지 SDK를 지원합니다. 이러한 SDK는 Node.js, Java, Python 및 Apple&reg; iOS를 포함한 다양한 인기 프로그래밍 언어 및 플랫폼에 대해 사용 가능합니다. SDK의 전체 목록 및 이를 사용하는 데 대한 정보는 [{{site.data.keyword.watson}} SDK](/docs/services/watson/getting-started-sdks.html)를 참조하십시오. 모든 SDK는 GitHub의 [watson-developer-cloud 네임스페이스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud){: new_window}에 있습니다. 

모바일 개발의 경우에는 [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}를 참조하십시오. 모든 SDK는 서비스 신임 정보 또는 인증 토큰을 사용한 인증을 지원합니다. 

## 애플리케이션 개발에 대해 자세히 알아보기
{: #learn}

{{site.data.keyword.toneanalyzershort}} 서비스는 두 가지 일반적인 프로그래밍 모델(클라이언트가 서비스와 직접 통신하는 *직접 상호작용*, 그리고 클라이언트와 서비스가 모든 데이터(요청 및 결과)를 {{site.data.keyword.Bluemix_short}}에 있는 프록시 애플리케이션을 통해 교환하는 *프록시를 통한 전달*)을 지원합니다. 

{{site.data.keyword.watson}} Developer Cloud 서비스 및 {{site.data.keyword.Bluemix_notm}} 관련 작업에 대한 자세한 정보는 다음 항목을 참조하십시오. 

-   {{site.data.keyword.watson}} 서비스 및 {{site.data.keyword.Bluemix_notm}} 관련 작업에 대한 소개는 [{{site.data.keyword.watson}} 및 {{site.data.keyword.Bluemix_notm}} 시작하기](/docs/services/watson/index.html)를 참조하십시오. 
-   {{site.data.keyword.Bluemix_notm}}에서 {{site.data.keyword.watson}} 서비스 애플리케이션을 개발하는 데 대한, 언어와 무관한 일반적 소개는 [{{site.data.keyword.Bluemix_notm}} 개발 접근법](/docs/services/watson/getting-started-bluemix.html)을 참조하십시오. 
-   {{site.data.keyword.watson}} 애플리케이션을 개발하는 데 사용할 수 있는 두 가지 프로그래밍 모델에 대한 정보는 [{{site.data.keyword.watson}} 서비스의 프로그래밍 모델](/docs/services/watson/getting-started-develop.html)을 참조하십시오. 
    -   프록시를 통한 전달을 사용하는 경우, 클라이언트는 서비스와 통신하기 위해 {{site.data.keyword.Bluemix_notm}}에 있는 프록시 서버에 의존하며 모든 요청을 프록시 애플리케이션을 통해 전달합니다. 프록시를 통한 요청 전달은 서비스를 인증하기 위해 서비스 신임 정보에 의존합니다. [{{site.data.keyword.watson}} 서비스의 서비스 신임 정보](/docs/services/watson/getting-started-credentials.html)를 참조하십시오. 
    -   직접 상호작용을 사용하는 경우, 클라이언트는 {{site.data.keyword.Bluemix_notm}}의 프록시 애플리케이션을 서비스의 인증 토큰을 획득하는 데만 사용하며, 그 후에는 서비스와 직접 통신합니다. 직접 상호작용은 토큰을 획득하는 데만 서비스 신임 정보를 사용합니다. [인증을 위한 토큰](/docs/services/watson/getting-started-tokens.html)을 참조하십시오. 
-   모든 {{site.data.keyword.watson}} 서비스에 대해 수행되는 기본 요청 로깅을 제어하는 데 대한 정보는 [{{site.data.keyword.watson}} 서비스의 요청 로깅 제어](/docs/services/watson/getting-started-logging.html)를 참조하십시오. 
