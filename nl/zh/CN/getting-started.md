---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 入门教程
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} 服务分析输入内容的语气。本教程显示用于分析不同样本内容的命令。以下示例演示通用和客户参与端点：
{: shortdesc}

## 开始之前
{: #prerequisites}

- 创建服务的实例：
    - {: download} 如果您看到此信息，表明您已创建服务实例。现在，获取凭证。
    - 从服务创建项目：
        1.  转至 {{site.data.keyword.watson}} 开发者控制台[服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/developer/watson/services){: new_window} 页面。
        1.  选择 {{site.data.keyword.toneanalyzershort}}，单击**添加服务**，然后注册免费 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
        1.  输入 `tone-tutorial` 作为项目名称，然后单击**创建项目**。
- 复制凭证以对服务实例进行认证：
    - {: download} 从服务仪表板（您正在看的项目）：
        1.  单击**服务凭证**选项卡。
        1.  单击**操作**下的**查看凭证**。
        1.  复制 `username`、`password` 和 `url` 值。
        {: download}
    - 从开发者控制台中的 **tone-tutorial** 项目，复制**凭证**部分中 `"tone_analyzer"` 的 `username`、`password` 和 `url` 值。
- 确保您具有以下 cURL：
    - 这些示例使用 cURL 来调用 HTTP 接口的方法。从 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 安装适用于您操作系统的版本。请安装支持安全套接字层 (SSL) 协议的版本。确保在 `PATH` 环境变量上包括已安装的二进制文件。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果使用 {{site.data.keyword.Bluemix_dedicated_notm}}，请从目录中的 [{{site.data.keyword.toneanalyzershort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} 页面创建服务实例。有关如何查找服务凭证的详细信息，请参阅 [Watson 服务的服务凭证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步骤 1：通过 POST 请求方法使用通用端点
{: #generalPurposePost}

以下命令会调用 `POST /v3/tone` 方法来分析文件 `tone.json` 的内容。该文件包含由一个人编写的单个纯文本段。这些示例演示方法的 `sentences` 查询参数。

1.  下载样本文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a>。
1.  发出以下命令来分析整体内容的语气和每个单独句子的语气。
    -   将 `{username}` 和 `{password}` 替换为先前步骤中的服务凭证。
    -   修改 `{path_to_file}` 以指定 `tone.json` 文件的位置。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  发出以下命令，通过将 `sentences` 参数设置为 `false` 来分析整体内容的语气。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

有关方法的输出示例，请参阅[示例响应](/docs/services/tone-analyzer/using-tone.html#exampleResponse)。

## 步骤 2：通过 GET 请求方法使用通用端点
{: #generalPurposeGet}

该接口还提供 `GET /v3/tone` 方法。`GET` 方法提供了相同的功能，并且生成与 `POST` 方法相同的结果，但您使用方法的 `text` 查询参数来指定要分析的内容。此方法仅接受纯文本输入。

1.  以下示例通过 `text` 参数指定文件 `tone.json` 的文本；如图所示，您必须对文本进行 URL 编码。该命令省略 `sentences` 参数，因此它返回与先前显示的第一个 `POST` 示例相同的输出。（此示例包含换行符以便于阅读；在实际命令中不要包含换行符。）

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## 步骤 3：使用客户参与端点
{: #customerEngagement}

以下命令会调用 `POST /v3/tone_chat` 方法来分析文件 `tone-chat.json` 的内容。该文件包含两个人员 <code>customer</code> 和 <code>agent</code> 之间的简短信息交流。

1.  下载样本文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tonechat.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a>。
1.  发出以下命令以分析样本文件中交流的语气。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

服务的响应指示对于输入的每个话语检测到的最普遍的语气。要查看此请求的响应内容，请参阅[示例响应](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse)。

## 后续步骤

-   有关 `/v3/tone` 方法的更多信息，请参阅[使用通用端点](/docs/services/tone-analyzer/using-tone.html)。
-   有关 `/v3/tone_chat` 方法的更多信息，请参阅[使用客户参与端点](/docs/services/tone-analyzer/using-tone-chat.html)。
-   有关服务接口的方法的详细信息，请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}。
-   与 [API 资源管理器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window} 中的 API 进行交互。
