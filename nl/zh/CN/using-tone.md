---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-21"

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

# 使用通用端点

{{site.data.keyword.toneanalyzershort}} 通用端点分析书面通信的语气，包括简短的电子邮件到较长的文档。它可以帮助您了解通信的情绪语气和语言语气。有关接口的详细信息（包括可用于调用服务的 Node.js、Java 和 Python SDK），请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}。
{: shortdesc}

## 请求语气分析
{: #request}

要使用通用端点来分析语气，可调用服务的 `tone` 方法的以下两个版本之一：

-   `POST /v3/tone` 方法通过请求的必需主体，接受 JSON、纯文本或 HTML 格式的输入内容。对于较长的文本或您不想在 URL 上公开的文本，使用这个版本的方法。
-   `GET /v3/tone` 方法通过其必需的 `text` 查询参数接受输入内容。对于可轻松在 URL 中容纳下的简单文本，使用这个版本的方法。

这些方法接受以下参数。

<table>
  <caption>表 1. <code>/v3/tone</code> 方法的参数</caption>
  <tr>
    <th style="text-align:left; width:20%">参数</th>
    <th style="text-align:center; width:12%">类型</th>
    <th style="text-align:center; width:20%">数据类型</th>
    <th style="text-align:left">描述</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>对于 <code>POST</code> 而言是必需的</em></td>
    <td style="text-align:center">正文</td>
    <td style="text-align:center">JSON 对象 | 字符串</td>
    <td>
包含要分析的内容的 JSON、纯文本或 HTML 输入。对于 JSON 输入，请提供类型为 <code>ToneInput</code> 的对象；请参阅<a href="#JSONinput">指定 JSON 输入</a>。<em><code>GET</code> 请求不支持。</em></td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>对于 <code>GET</code> 而言是必需的</em></td>
    <td style="text-align:center">查询</td>
    <td style="text-align:center">字符串</td>
    <td>
包含要分析的内容的纯文本输入。您必需对输入进行 URL 编码。
<em><code>POST</code> 请求不支持。</em></td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>对于 <code>POST</code> 而言是必需的</em></td>
    <td style="text-align:center">头</td>
    <td style="text-align:center">字符串</td>
    <td>
      请求的内容类型：
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          纯文本为 <code>text/plain</code>
        </li>
        <li style="margin:0px; padding:0px">
            HTML 格式的文本为 <code>text/html</code>（服务将除去 HTML 标记，仅分析文本内容）
</li>
        <li style="margin:0px; padding:0px">
          JSON 格式的文本为 <code>application/json</code>
        </li>
      </ul>
    <em>对于 <code>GET</code> 请求而言会省略。</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必需</em></td>
    <td style="text-align:center">查询</td>
    <td style="text-align:center">字符串</td>
    <td>
所请求的响应格式版本，格式为 <code>YYYY-MM-DD</code> 的日期；例如，指定 <code>2017-09-21</code> 表示 2017 年 9 月 21 日。</td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>可选</em></td>
    <td style="text-align:center">头</td>
    <td style="text-align:center">字符串</td>
    <td>
      输入内容的语言：
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code>（英语，缺省值）
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code>（法语）</li>
      </ul>
区域变体将被视为其父语言；例如，<code>en-US</code> 将解释为 <code>en</code>。输入内容必须与指定的语言匹配。请勿提交包含这两种语言的内容。您可以对输入和响应使用不同的语言。</td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>可选</em></td>
    <td style="text-align:center">头</td>
    <td style="text-align:center">字符串</td>
    <td>
      想要的响应语言：
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
ar（阿拉伯语）</li>
        <li style="margin:0px; padding:0px">
de（德语）</li>
        <li style="margin:0px; padding:0px">
en（英语，缺省值）</li>
        <li style="margin:0px; padding:0px">
es（西班牙语）</li>
        <li style="margin:0px; padding:0px">
fr（法语）</li>
        <li style="margin:0px; padding:0px">
it（意大利语）</li>
        <li style="margin:0px; padding:0px">
ja（日语）</li>
        <li style="margin:0px; padding:0px">
ko（韩语）</li>
        <li style="margin:0px; padding:0px">
pt-br（巴西葡萄牙语）</li>
        <li style="margin:0px; padding:0px">
zh-cn（简体中文）</li>
        <li style="margin:0px; padding:0px">
zh-tw（繁体中文）</li>
      </ul>
对于双字符自变量，区域变体将被视为其父语言；例如，<code>en-US</code> 将解释为 <code>en</code>。您可以对输入和响应使用不同的语言。</td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>可选</em></td>
    <td style="text-align:center">查询</td>
    <td style="text-align:center">布尔</td>
    <td>
指示服务除了完整文档的分析之外，是否返回每个单独句子的分析。如果为 <code>true</code>（缺省值），那么服务将返回每个句子的结果。</td>
  </tr>
</table>

提交的总输入内容不超过 128 KB，且不超过 1000 个单独的句子。对于文档级别的分析，该服务分析前 1000 个句子，而对于句子级别的分析，则仅分析前 100 个句子。如果超过任一限制，那么它将返回 `warning` 字段作为其响应的一部分；请求仍将成功，HTTP 响应代码为 200。

### 示例请求
{: #exampleRequests}

以下示例 cURL 命令使用 HTTP `POST` 请求方法，搭配输入文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 和 `2017-09-21` 的版本来调用通用端点。该示例请求不仅对完整文档进行分析，还对单个句子进行分析。

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

以下示例命令等同于先前的示例，但使用 HTTP `GET` 请求方法：

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

要获取其他示例，请参阅[入门教程](/docs/services/tone-analyzer/getting-started.html)。

### 指定字符集
{: #charset}

缺省情况下，此服务将以下字符集用于输入内容：

-   *对于纯文本和 HTML 内容，*该服务按照 HTTP V1.1 规格，使用国际标准组织 (ISO)-8859-1 字符集（实际上是 ASCII 字符集）。
-   *对于 JSON 内容，*该服务按照国际工程任务组 (IETF) 8.1 节[请求注释 (RFC) 7159 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}，始终使用 Unicode 转换格式 (UTF)-8 字符集。

提交纯文本或 HTML 内容时，请包含带有 `Content-Type` 头的 `charset` 参数，以指示输入文本的字符编码。以下示例为纯文本输入指定了 UTF-8 字符编码：

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

通过使用 `charset` 参数，可以避免与非 ASCII 或不可打印字符相关联的潜在问题。如果在未指定字符集的情况下传递 UTF-8 数据，那么特殊字符可能会导致不正确的结果，或导致 HTTP 4*nn* 或 5*nn* 错误。

为防止使用 cURL 时出现类似错误，请始终通过 `curl` 命令的 `--data-binary` 选项传递内容，以保留内容的任何 UTF-8 编码。如果使用 `--data` 选项将内容作为 ASCII 传递，那么该命令可以处理输入，但可能会导致以 UTF-8 编码的数据出现问题。

## 指定 JSON 输入
{: #JSONinput}

要使用 `POST` 请求方法分析 JSON 输入，请使用以下简单格式向方法传递 JSON `ToneInput` 对象：

```javascript
{
  "text": ""
}
```
{: codeblock}

以下示例显示了 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标" class="style-scope doc-content"></a> 文件的内容，该文件与[入门教程](/docs/services/tone-analyzer/getting-started.html)中的示例一起使用。该文件包含由一个人编写的单个文本段。（以下文本包含换行符以便于阅读；在实际输入中不要包含换行符。）

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## JSON 响应内容
{: #JSONresponse}

该服务返回始终包含 `document_tone` 字段的 JSON `ToneAnalysis` 对象。此字段包含用于提供完整输入文档分析的 `DocumentAnalysis` 对象。它包含单个字段 `tones`，用于提供文档每个符合条件语气的分析结果。

如果省略请求的 `sentences` 参数或该参数设置为 `true`，那么响应还包含 `sentences_tone` 字段。此字段包含 `SentenceAnalysis` 对象数组，其中每个对象都为输入内容中的不同句子提供以下信息：

-   `sentence_id`（整数）提供句子的唯一标识。第一个句子的 ID 为 0，后续每个句子的 ID 加一。
-   `text`（字符串）提供句子的文本。
-   `tones` 提供句子的符合条件语气的分析结果。

以下示例显示了 `ToneAnalysis` 对象的高级结构：

```javascript
{
  "document_tone": {
    "tones": [
      . . .
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": {integer},
      "text": "{string}",
      "tones": [
        . . .
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### 语气和分数结果

针对文档级别和句子级别分析返回的 `tones` 字段包含 `ToneScore` 对象数组，用于提供主语气的结果，其分数至少为 0.5。如果没有任何语气具有满足此阈值的得分，那么该数组为空。每个 `ToneScore` 对象都提供有关符合条件语气的以下信息：

-   `score`（双精度）是一个语气的得分，范围在 0.5 到 1 之间。大于 0.75 的得分表示在内容中感知到该语气的可能性大。
-   `tone_id`（字符串）是语气的唯一非本地化标识；有关语气的描述，请参阅[通用语气](#tones)。
-   `tone_name`（字符串）是用户可见的已本地化的语气名称。

以下示例显示了 `ToneScore` 对象的结构：

```javascript
{
  "tones": [
    {
      "score": {double},
      "tone_id": "{string}",
      "tone_name": "{string}"
    },
    . . .
  ]
}
```
{: codeblock}

### 示例响应
{: #exampleResponse}

对于[示例请求](#exampleRequests)，将返回以下输出。（对于[入门教程](/docs/services/tone-analyzer/getting-started.html)中的第一个示例，将返回相同的输出。）响应包含完整文档和每个单独句子的结果。所有报告语气的得分都至少为 0.5；得分至少为 0.75 的那些语气是很可能在内容中感知到语气。

```javascript
{
  "document_tone": {
    "tones": [
      {
        "score": 0.6165,
        "tone_id": "sadness",
        "tone_name": "Sadness"
      },
      {
        "score": 0.829888,
        "tone_id": "analytical",
        "tone_name": "Analytical"
      }
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": 0,
      "text": "Team, I know that times are tough!",
      "tones": [
        {
          "score": 0.801827,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 1,
      "text": "Product sales have been disappointing for the past three quarters.",
      "tones": [
        {
          "score": 0.771241,
          "tone_id": "sadness",
          "tone_name": "Sadness"
        },
        {
          "score": 0.687768,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 2,
      "text": "We have a competitive product, but we need to do a better job of selling it!",
      "tones": [
        {
          "score": 0.506763,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    }
  ]
}
```
{: codeblock}

## 通用语气
{: #tones}

下表描述了服务可以返回的通用语气。省略分数小于 0.5 的语气，这表示在内容中不太可能感知到该情绪。大于 0.75 的分数表示很有可能会感知到该语气。

<table>
  <caption>表 2. 通用语气</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">语气/标识</th>
    <th style="text-align:left">描述</th>
  </tr>
  <tr>
    <td>愤怒<br/><code>anger</code></td>
    <td>
愤怒是因为不公、冲突、羞辱、过失或背叛而产生的。如果愤怒处于活动状态，那么个人会口头上或身体上对目标进行攻击。愤怒是被动的，人会生闷气并感到情绪紧张、充满敌意。（情绪语气。）
    </td>
  </tr>
  <tr>
    <td>恐惧<br/><code>fear</code></td>
    <td>
      恐惧是对即将发生的危险的回应。它是一种生存机制，作为对某些负面刺激的反应而触发。恐惧可能是轻微谨慎到极度恐怖。（情绪语气。）
    </td>
  </tr>
  <tr>
    <td>愉悦<br/><code>joy</code></td>
    <td>
愉悦（或幸福）有享受、满足和快乐的色彩。愉悦带来一种幸福、内心平和、爱、安全和知足的感觉。（情绪语气。）
    </td>
  </tr>
  <tr>
    <td>悲伤<br/><code>sadness</code></td>
    <td>
悲伤表明了一种失去和处于不利地位的感觉。当一个人沉默寡言、没有精神、孤僻离群的时候，可以推断出他们感到悲伤。（情绪语气。）
    </td>
  </tr>
  <tr>
    <td>善于分析<br/><code>analytical</code></td>
    <td>
善于分析的语气表明一个人对事物具有推理和分析的态度。
善于分析的人可能被认为聪明、理智、有条理、冷静或客观。（语言语气。）
    </td>
  </tr>
  <tr>
    <td>确信<br/><code>confident</code></td>
    <td>
确信语气表明一个人的确定程度。确信的人可能会被认为是自信、镇定、充满希望或自我。（语言语气。）
    </td>
  </tr>
  <tr>
    <td>不确定<br/><code>tentative</code></td>
    <td>
不确定语气表明一个人的顾虑程度。不确定的人可能被认为是犹疑不定、犹豫不决或不够果敢。（语言语气。）
    </td>
  </tr>
</table>
