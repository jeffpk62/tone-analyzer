---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-14"

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

# Overview for developers
{: #overviewDevelopers}

You can access the capabilities of the {{site.data.keyword.toneanalyzershort}} service via an HTTP Representational State Transfer (REST) API. Several Software Development Kits (SDKs) are also available to simplify application development in various languages and environments. The following sections provide an overview of application development with the service.
{: shortdesc}

## Programming with the service
{: #programming}

To analyze the tone of an individual's text, you pass the input text to the service via the `GET` or `POST /v3/tone` method. To analyze the exchanges in a conversation, you pass input to the service via the `POST /v3/tone_chat` method. In both cases, the service returns its analysis in JSON format.

For more information, see [Using the general-purpose endpoint](/docs/services/tone-analyzer/using-tone.html) and [Using the customer-engagement endpoint](/docs/services/tone-analyzer/using-tone-chat.html).

## Using Software Development Kits
{: #sdks}

The {{site.data.keyword.toneanalyzershort}} service supports a number of SDKs for simplified application development. The SDKs are available for many popular programming languages and platforms, including Node.js, Java, and Python. For a complete list of SDKs and information about using them, see [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html). All SDKs are available from the [watson-developer-cloud namespace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud){: new_window} on GitHub.

## Learning more about application development
{: #learn}

The {{site.data.keyword.toneanalyzershort}} service supports two typical programming models. With *direct interaction*, the client communicates with the service directly. With *relaying via a proxy*, the client and service exchange all data (requests and results) through a proxy application that resides in {{site.data.keyword.Bluemix_short}}.

For more information about working with {{site.data.keyword.watson}} Developer Cloud services and {{site.data.keyword.Bluemix_notm}}, see the following pages:

-   For an introduction to working with {{site.data.keyword.watson}} services and {{site.data.keyword.Bluemix_notm}}, see [Getting started with {{site.data.keyword.watson}} and {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   For a language-independent introduction to developing {{site.data.keyword.watson}} services applications in {{site.data.keyword.Bluemix_notm}}, see [{{site.data.keyword.Bluemix_notm}} development approaches](/docs/services/watson/getting-started-bluemix.html).
-   For more information about the two programming models available for developing {{site.data.keyword.watson}} applications, see [Programming models for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-develop.html).
    -   With relaying via a proxy, the client relies on a proxy server that resides in {{site.data.keyword.Bluemix_notm}} to communicate with the service. The client passes all requests through the proxy application. Relaying requests via a proxy relies only on service credentials to authenticate with the service; see [Service credentials for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-credentials.html).
    -   With direct interaction, the client uses the proxy application in {{site.data.keyword.Bluemix_notm}} only to obtain an authentication token for the service. It then communicates directly with the service. Direct interaction uses service credentials only to obtain a token; see [Tokens for authentication](/docs/services/watson/getting-started-tokens.html).

    > **Note:** In some regions, new service instances use {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) instead of service credentials for authentication.
    -   For more information about where and how the service uses IAM authentication, see the [Release notes](/docs/services/tone-analyzer/release-notes.html).
    -   For more information about using IAM tokens with {{site.data.keyword.watson}} services, see [Authenticating with IAM tokens](/docs/services/watson/getting-started-iam.html).

-   For more information about controlling the default request logging that is performed for all {{site.data.keyword.watson}} services, see [Controlling request logging for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-logging.html).

    > **Note:** Request logging is disabled for the {{site.data.keyword.toneanalyzershort}} service. The service does not log or retain data from requests and responses, regardless of whether the `X-Watson-Learning-Opt-Out` request header is set.
