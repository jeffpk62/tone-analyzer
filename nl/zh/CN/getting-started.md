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
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 入门教程
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} 服务分析输入内容的语气。本教程显示用于分析不同样本内容的命令。这些示例展示通用端点和客户参与端点。
{: shortdesc}

本教程使用 {{site.data.keyword.cloud}} Identity and Access Management (IAM) API 密钥进行认证。较早的服务实例可以继续使用现有 Cloud Foundry 服务凭证的 `{username}` 和 `{password}` 进行认证。使用适合您的服务实例的方法进行认证。有关服务使用 IAM 认证的更多信息，请参阅[发行说明](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)。
{: important}

## 开始之前
{: #prerequisites}

- {: hide-dashboard}创建服务的实例：
    1.  {: hide-dashboard}转至 {{site.data.keyword.cloud_notm}}“目录”中的 [{{site.data.keyword.toneanalyzershort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} 页面。
    1.  {: hide-dashboard}注册免费的 {{site.data.keyword.cloud_notm}} 帐户或登录。
    1.  {: hide-dashboard}单击**创建**。
-   复制凭证以对服务实例进行认证：
    1.  {: hide-dashboard}从 [{{site.data.keyword.cloud_notm}}仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/dashboard/apps){: new_window} 中，单击 {{site.data.keyword.toneanalyzershort}} 服务实例，以转至 {{site.data.keyword.toneanalyzershort}} 服务仪表板页面。
    1.  在**管理**页面上，单击**显示**以查看凭证。
    1.  复制 `API Key` 和 `URL` 值。
-   确保您有 `curl` 命令。
    -   这些示例使用 `curl` 命令来调用 HTTP 接口的方法。从 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 安装适用于您操作系统的版本。请安装支持安全套接字层 (SSL) 协议的版本。确保在 `PATH` 环境变量上包括已安装的二进制文件。

输入命令时，将 `{apikey}` 和 `{url}` 替换为实际 API 密钥和 URL。从命令中省略指示变量值的花括号。实际值与以下示例类似：
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## 步骤 1：通过 POST 请求方法使用通用端点
{: #generalPurposePost}

以下命令会调用 `POST /v3/tone` 方法来分析文件 `tone.json` 的内容。该文件包含由一个人编写的单个纯文本段。这些示例演示方法的 `sentences` 查询参数。

1.  下载样本文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a>。
1.  发出以下命令来分析整体内容的语气和每个单独句子的语气。
    -   {: hide-dashboard}将 `{apikey}` 和 `{url}` 替换为您的信息。
    -   修改 `{path_to_file}` 以指定 `tone.json` 文件的位置。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  发出以下命令，通过将 `sentences` 参数设置为 `false` 来分析整体内容的语气。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

有关方法的输出示例，请参阅[示例响应](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone)。

## 步骤 2：通过 GET 请求方法使用通用端点
{: #generalPurposeGet}

该接口还提供 `GET /v3/tone` 方法。`GET` 方法提供了相同的功能，并且生成与 `POST` 方法相同的结果，但您使用方法的 `text` 查询参数来指定要分析的内容。此方法仅接受纯文本输入。

1.  以下示例通过 `text` 参数指定文件 `tone.json` 的文本；如图所示，您必须对文本进行 URL 编码。该命令省略 `sentences` 参数，因此它返回与先前显示的第一个 `POST` 示例相同的输出。（此示例包含换行符以便于阅读；在实际命令中不要包含换行符。）

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## 步骤 3：使用客户参与端点
{: #customerEngagement}

以下命令会调用 `POST /v3/tone_chat` 方法来分析文件 `tone-chat.json` 的内容。该文件包含两个人员 <code>customer</code> 和 <code>agent</code> 之间的简短信息交流。

1.  下载样本文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tonechat.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a>。
1.  发出以下命令以分析样本文件中交流的语气。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

服务的响应指示对于输入的每个话语检测到的最普遍的语气。要查看此请求的响应内容，请参阅[示例响应](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat)。

## 后续步骤
{: #gsns}

-   有关 `/v3/tone` 方法的更多信息，请参阅[使用通用端点](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)。
-   有关 `/v3/tone_chat` 方法的更多信息，请参阅[使用客户参与端点](/docs/services/tone-analyzer?topic=tone-analyzer-utco)。
-   有关服务接口的方法的更多信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。
