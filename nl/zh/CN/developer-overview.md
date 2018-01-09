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

# 开发者概述
{: #overviewDevelopers}

您可以通过 HTTP 具象状态传输 (REST) API 来访问 {{site.data.keyword.toneanalyzershort}} 服务的功能。还可以使用多种软件开发包 (SDK) 来简化在各种语言和环境中的应用程序开发。以下各节提供了使用服务进行应用程序开发的概述。
{: shortdesc}

## 使用服务编程
{: #programming}

要分析个别文本的语气，可通过 `GET` 或 `POST /v3/tone` 方法，将输入文本传递到服务。要分析对话中的交流，可通过 `POST /v3/tone_chat` 方法，将输入传递到服务。在这两种情况下，服务都将以 JSON 格式返回其分析。

有关更多信息，请参阅[使用通用端点](/docs/services/tone-analyzer/using-tone.html)和[使用客户参与端点](/docs/services/tone-analyzer/using-tone-chat.html)。

## 使用软件开发包
{: #sdks}

{{site.data.keyword.toneanalyzershort}} 服务支持许多 SDK 以简化应用程序开发。SDK 提供许多常用的编程语言和平台，包括 Node.js、Java、Python 和 Apple&reg; iOS。有关 SDK 的完整列表以及如何使用它们的信息，请参阅 [{{site.data.keyword.watson}} SDK](/docs/services/watson/getting-started-sdks.html)。所有 SDK 都可从 GitHub 上的 [watson-developer-cloud namespace ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud){: new_window} 获取。

对于移动开发，请参阅 [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}。所有 SDK 都支持通过使用服务凭证或认证令牌进行认证。

## 了解有关应用程序开发的更多信息
{: #learn}

{{site.data.keyword.toneanalyzershort}} 服务支持两种典型编程模型：*直接交互*，在该模型中，客户机直接与服务进行通信；*通过代理进行中继*，在该模型中，客户机和服务通过驻留在 {{site.data.keyword.Bluemix_short}} 中的代理应用程序来交换所有数据（请求和结果）。

有关使用 {{site.data.keyword.watson}} Developer Cloud 服务和 {{site.data.keyword.Bluemix_notm}} 的更多信息，请参阅以下内容：

-   有关使用 {{site.data.keyword.watson}} 服务和 {{site.data.keyword.Bluemix_notm}} 的简介，请参阅 [{{site.data.keyword.watson}} 和 {{site.data.keyword.Bluemix_notm}} 入门](/docs/services/watson/index.html)。
-   有关在 {{site.data.keyword.Bluemix_notm}} 中开发 {{site.data.keyword.watson}} 服务应用程序的语言无关简介，请参阅 [{{site.data.keyword.Bluemix_notm}} 开发方法](/docs/services/watson/getting-started-bluemix.html)。
-   有关可用于开发 {{site.data.keyword.watson}} 应用程序的两种编程模型的信息，请参阅 [{{site.data.keyword.watson}} 服务的编程模型](/docs/services/watson/getting-started-develop.html)：
    -   通过代理中继，客户机依赖于驻留在 {{site.data.keyword.Bluemix_notm}} 中的代理服务器与服务进行通信；它通过代理应用程序传递所有请求。通过代理中继请求仅依靠服务凭证向服务进行认证；请参阅 [{{site.data.keyword.watson}} 服务的服务凭证](/docs/services/watson/getting-started-credentials.html)。
    -   通过直接交互，客户机仅在 {{site.data.keyword.Bluemix_notm}} 中使用代理应用程序，来获取服务的认证令牌，然后直接与服务进行通信。直接交互仅使用服务凭证来获取令牌；请参阅[用于认证的令牌](/docs/services/watson/getting-started-tokens.html)。
-   有关控制对所有 {{site.data.keyword.watson}} 服务执行的缺省请求日志记录的信息，请参阅[控制 {{site.data.keyword.watson}} 服务的请求日志记录](/docs/services/watson/getting-started-logging.html)。
