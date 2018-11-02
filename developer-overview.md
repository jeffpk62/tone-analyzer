---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-01"

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

To analyze the tone of an individual's text, you pass the input text to the service via the `GET` or `POST /v3/tone` method. To analyze the exchanges in a conversation, you pass input to the service via the `POST /v3/tone_chat` method. In both cases, the service returns its analysis in JSON format. For more information, see

-   [Using the general-purpose endpoint](/docs/services/tone-analyzer/using-tone.html)
-   [Using the customer-engagement endpoint](/docs/services/tone-analyzer/using-tone-chat.html)

## Using Software Development Kits
{: #sdks}

The {{site.data.keyword.toneanalyzershort}} service supports a number of SDKs for simplified application development. The SDKs are available for many popular programming languages and platforms, including Node.js, Java, Python, and Ruby. All SDKs are available from the [watson-developer-cloud namespace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud){: new_window} on GitHub.

-   For a complete list of SDKs and information about using them, see [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html).
-   For detailed information about the methods of the Node, Java, Python, and Ruby SDKs, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.

## Learning more about application development
{: #learn}

For more information about working with {{site.data.keyword.watson}} Developer Cloud services and {{site.data.keyword.Bluemix_notm}}, see the following pages:

-   For an introduction to working with {{site.data.keyword.watson}} services and {{site.data.keyword.Bluemix_notm}}, see [Getting started with {{site.data.keyword.watson}} and {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   All new service instances use {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) for authentication. Older service instances might continue to use the `{username}` and `{password}` from their existing Cloud Foundry service credentials for authentication. For more information about authenticating to the service, see the [30 October 2018 service update](/docs/services/tone-analyzer/release-notes.html#October2018) in the release notes.
-   Request logging is disabled for the {{site.data.keyword.toneanalyzershort}} service. The service does not log or retain data from requests and responses, regardless of whether the `X-Watson-Learning-Opt-Out` request header is set.
