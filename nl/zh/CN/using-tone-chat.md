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

# 使用客户参与端点
{: #utco}

{{site.data.keyword.toneanalyzershort}} 客户参与端点分析客户服务和支持对话的语气。它可以帮助您更好地了解与客户的交互，并改善常规通信或特定客户的通信。有关接口的更多信息（包括可用于调用服务的 Node.js、Java 和 Python SDK），请参阅 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。
{: shortdesc}

针对 {{site.data.keyword.toneanalyzershort}} 服务禁用了请求日志记录。无论是否设置了 `X-Watson-Learning-Opt-Out` 请求头，服务都不会记录或保留来自请求和响应的数据。
{: note}

## 请求语气分析
{: #request-tone-chat}

要使用客户参与端点来分析语气，请使用以下参数调用 `POST /v3/tone_chat` 方法。

<table>
  <caption>表 1. <code>POST /v3/tone_chat</code> 方法的参数</caption>
  <tr>
    <th style="text-align:left; width:20%">参数</th>
    <th style="text-align:center; width:12%">类型</th>
    <th style="text-align:center; width:20%">数据类型</th>
    <th style="text-align:left">描述</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>必需</em></td>
    <td style="text-align:center">正文</td>
    <td style="text-align:center">JSON 对象</td>
    <td>
包含要分析的内容的 JSON <code>ToneChatInput</code> 对象。有关更多信息，请参阅[指定 JSON 输入](#JSONrequest)。</td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必需</em></td>
    <td style="text-align:center">查询</td>
    <td style="text-align:center">字符串</td>
    <td>
      想要用作 <code>YYYY-MM-DD</code> 格式的日期的 API 版本；例如，指定 <code>2017-09-21</code> 以表示 2017 年 9 月 21 日（最新版本）。有关所有可用版本的更多信息，请参阅[发行说明](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)。</td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>可选</em></td>
    <td style="text-align:center">头</td>
    <td style="text-align:center">字符串</td>
    <td>
      输入内容的语言。<ul style="margin:0px 0px 0px 20px; padding:0px">
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
      请求的响应语言。<ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code>（阿拉伯语）</li>
        <li style="margin:0px; padding:0px">
          <code>de</code>（德语）</li>
        <li style="margin:0px; padding:0px">
          <code>en</code>（英语，缺省值）
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code>（西班牙语）</li>
        <li style="margin:0px; padding:0px">
          <code>fr</code>（法语）</li>
        <li style="margin:0px; padding:0px">
          <code>it</code>（意大利语）</li>
        <li style="margin:0px; padding:0px">
          <code>ja</code>（日语）</li>
        <li style="margin:0px; padding:0px">
          <code>ko</code>（韩语）</li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code>（巴西葡萄牙语）</li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code>（简体中文）</li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code>（繁体中文）</li>
      </ul>
对于双字符自变量，区域变体将被视为其父语言；例如，<code>en-US</code> 将解释为 <code>en</code>。您可以对输入和响应使用不同的语言。</td>
  </tr>
</table>

如果提交的话语超过 50 个，那么对于整体内容，此服务将在响应的 `utterances_tone` 级别返回 `warning` 字段，且仅分析前 50 个话语。如果提交包含超过 500 个字符的单一话语，那么该服务将针对该话语返回 `error` 字段，并且不会分析该话语。在这两种情况下，请求仍会成功，HTTP 响应代码为 200。

如果输入的所有话语超过 500 个字符，那么该服务会返回响应代码 400。
{: note}

### 示例请求
{: #exampleRequest}

以下示例 `curl` 命令使用输入文件 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tonechat.json<img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 和版本 `2017-09-21` 来调用客户参与端点：

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## 指定 JSON 输入
{: #JSONrequest}

您使用以下格式向方法传递 JSON `TOoneChatInput` 对象。`utterances` 字段提供 `utterance` 对象的数组。`text` 字段是必填字符串，用于提供用户在要分析的对话中所贡献的话语。`user` 是可选字符串，用于标识贡献话语的用户。

```javascript
{
  "utterances": [
    {
      "text": "",
      "user": ""
    },
    . . .
  ]
}
```
{: codeblock}

以下示例显示 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tonechat.json <img src="../../icons/launch-glyph.svg" alt="外部链接图标" title="外部链接图标"></a> 文件的内容。该文件包含 <code>customer</code> 与 <code>agent</code> 之间的简短交流。

```javascript
{
  "utterances": [
    {
      "text": "Hello, I'm having a problem with your product.",
      "user": "customer"
    },
    {
      "text": "OK, let me know what's going on, please.",
      "user": "agent"
    },
    {
      "text": "Well, nothing is working :(",
      "user": "customer"
    },
    {
      "text": "Sorry to hear that.",
      "user": "agent"
    }
  ]
}
```
{: codeblock}

## JSON 响应内容
{: #JSONresponse-tone-chat}

该服务返回包含单个字段 `utterances_tone` 的 JSON `UtteranceAnalyses` 对象。此字段包含 `UtteranceAnalysis` 对象的数组，其中每个对象都提供有关输入内容话语的以下信息：

-   `utterance_id`（整数）提供话语的唯一标识。第一个话语的 ID 为 0，后续每个话语的 ID 加一。
-   `utterance_text`（字符串）提供话语的文本。
-   `tones` 是 `ToneChatScore` 对象的数组，用于为主语气提供结果。此类语气的得分至少为 0.5。如果话语没有任何语气具有满足此阈值的得分，那么该数组为空。

每个 `ToneChatScore` 对象都提供有关符合条件语气的以下信息：

-   `score`（双精度）是一个语气的得分，范围在 0.5 到 1 之间。大于 0.75 的得分表示在话语中感知到该语气的可能性大。
-   `tone_id`（字符串）是语气的唯一非本地化标识；有关语气的描述，请参阅[客户参与语气](#tones-tone-chat)。
-   `tone_name`（字符串）是用户可见的已本地化的语气名称。

以下示例显示了 `UtteranceAnalyses` 对象的结构：

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": {integer},
      "utterance_text": "{string}",
      "tones": [
        {
          "score": {double},
          "tone_id": "{string",
          "tone_name": "{string}"
        }
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### 示例响应
{: #exampleResponse-tone-chat}

对于[示例请求](#exampleRequest)，将返回以下输出。（对于[入门教程](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted#customerEngagement)中的示例，将返回相同的输出。）所有报告的语气的得分至少为 0.5。得分至少为 0.75 的语气很可能由参与者在对话中感知到。

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.686361,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": [
        {
          "score": 0.92724,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997795,
          "tone_id": "sad",
          "tone_name": "sad"
        }
      ]
    },
    {
      "utterance_id": 3,
      "utterance_text": "Sorry to hear that.",
      "tones": [
        {
          "score": 0.730982,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.672499,
          "tone_id": "sympathetic",
          "tone_name": "Sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## 客户参与语气
{: #tones-tone-chat}

该服务可返回以下七个语气的分数。

<table style="width:90%">
  <caption>表 2. 客户参与语气</caption>
  <tr>
    <th style="text-align:left; width:20%">语气/标识</th>
    <th style="text-align:left">描述</th>
  </tr>
  <tr>
    <td>兴奋<br/><code>excited</code></td>
    <td>
展现个人热情和兴趣</td>
  </tr>
  <tr>
    <td>沮丧<br/><code>frustrated</code></td>
    <td>
定义为感到恼火和烦躁</td>
  </tr>
  <tr>
    <td>粗鲁<br/><code>impolite</code></td>
    <td>
      无礼粗暴
    </td>
  </tr>
  <tr>
    <td>有礼<br/><code>polite</code></td>
    <td>
定义为理性的以目标为导向的行为</td>
  </tr>
  <tr>
    <td>悲伤<br/><code>sad</code></td>
    <td>
      视为一种不高兴的消极情绪
    </td>
  </tr>
  <tr>
    <td>满意<br/><code>satisfied</code></td>
    <td>
      感知服务质量的情感反应
    </td>
  </tr>
  <tr>
    <td>同情<br/><code>sympathetic</code></td>
    <td>
涉及情绪共鸣的一种情感理解方式</td>
  </tr>
</table>
