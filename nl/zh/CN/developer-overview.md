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

# 开发者概述
{: #overviewDevelopers}

您可以通过 HTTP 具象状态传输 (REST) API 来访问 {{site.data.keyword.toneanalyzershort}} 服务的功能。还可以使用多种软件开发包 (SDK) 来简化各种语言中的应用程序开发。以下各节提供了使用服务进行应用程序开发的概述。
{: shortdesc}

## 使用服务编程
{: #programming}

要分析个人的文本的语气，可通过 `GET` 或 `POST /v3/tone` 方法，将输入文本传递到服务。要分析对话中的交流，可通过 `POST /v3/tone_chat` 方法，将输入传递到服务。在这两种情况下，服务都将以 JSON 格式返回其分析。有关更多信息，请参阅

-   [使用通用端点](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [使用顾客参与端点](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## 使用软件开发包
{: #sdks}

SDK 可用于 {{site.data.keyword.toneanalyzershort}} 服务，以简化应用程序开发。{{site.data.keyword.ibmwatson}} SDK 可用于许多常用的编程语言和平台。

-   有关 GitHub 上的 SDK 和 SDK 链接的完整列表，请参阅[使用 SDK](/docs/services/watson?topic=watson-using-sdks)。
-   有关 {{site.data.keyword.toneanalyzershort}} 服务的 Node、Java、Python、Ruby 和 Go SDK 所有方法的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。

## 了解有关应用程序开发的更多信息
{: #learn}

有关使用 {{site.data.keyword.watson}} 服务和 {{site.data.keyword.cloud}} 的更多信息，请参阅以下页面：

-   有关使用 {{site.data.keyword.watson}} 服务和 {{site.data.keyword.cloud_notm}} 的简介，请参阅 [{{site.data.keyword.watson}} 和 {{site.data.keyword.cloud_notm}} 入门](/docs/services/watson?topic=watson-about)。
-   所有新服务实例都使用 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 进行认证。较早的服务实例可以继续使用现有 Cloud Foundry 服务凭证的 `{username}` 和 `{password}` 进行认证。有关对服务进行认证的更多信息，请参阅发行说明中的 [2018 年 10 月 30 日服务更新](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018)。
-   {{site.data.keyword.toneanalyzershort}} 服务禁用了请求日志记录。无论是否设置 `X-Watson-Learning-Opt-Out` 请求头，该服务都不会记录或保留来自请求和响应的数据。
