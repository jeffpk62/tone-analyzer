---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-28"

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

# カスタマー・エンゲージメント・エンドポイントの使用

{{site.data.keyword.toneanalyzershort}} カスタマー・エンゲージメント・エンドポイントは、カスタマー・サービスおよびカスタマー・サポートの会話のトーンを分析します。顧客とのやり取りをより正確に理解し、コミュニケーション全体、また、特定の顧客とのコミュニケーションを向上させるのに役立ちます。サービスの呼び出しに使用できる Node.js SDK、Java SDK、Python SDK などのインターフェースについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window} を参照してください。
{: shortdesc}

## トーン分析の要求
{: #request}

カスタマー・エンゲージメント・エンドポイントを使用してトーンを分析するには、以下のパラメーターを指定して `POST /v3/tone_chat` メソッドを呼び出します。

<table>
  <caption>表 1. <code>POST /v3/tone_chat</code> メソッドのパラメーター</caption>
  <tr>
    <th style="text-align:left; width:20%">パラメーター</th>
    <th style="text-align:center; width:12%">タイプ</th>
    <th style="text-align:center; width:20%">データ・タイプ</th>
    <th style="text-align:left">説明</th>
  </tr>
  <tr>
    <td><code>本文</code><br/><em>必須</em></td>
    <td style="text-align:center">本文</td>
    <td style="text-align:center">JSON オブジェクト</td>
    <td>
分析するコンテンツを含む JSON <code>ToneChatInput</code> オブジェクト。<a href="#JSONrequest">JSON 入力の指定</a>を参照してください。</td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必須</em></td>
    <td style="text-align:center">照会</td>
    <td style="text-align:center">ストリング</td>
    <td>
<code>YYYY-MM-DD</code> 形式の日付として要求するインターフェースのバージョン。例えば、2017 年 9 月 21 日の場合は、<code>2017-09-21</code> と指定します。</td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>オプション</em></td>
    <td style="text-align:center">ヘッダー</td>
    <td style="text-align:center">ストリング</td>
    <td>
      目的の応答言語:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (アラビア語)
        </li>
        <li style="margin:0px; padding:0px">
          de (ドイツ語)
        </li>
        <li style="margin:0px; padding:0px">
          en (英語 (デフォルト))
        </li>
        <li style="margin:0px; padding:0px">
          es (スペイン語)
        </li>
        <li style="margin:0px; padding:0px">
          fr (フランス語)
        </li>
        <li style="margin:0px; padding:0px">
          it (イタリア語)
        </li>
        <li style="margin:0px; padding:0px">
          ja (日本語)
        </li>
        <li style="margin:0px; padding:0px">
          ko (韓国語)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (ブラジル・ポルトガル語)
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (中国語 (簡体字))
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (中国語 (繁体字))
        </li>
      </ul>
    </td>
  </tr>
</table>

50 を超える発話が送信された場合、サービスは応答の `utterances_tone` レベルでコンテンツ全体に対して `warning` フィールドを返し、最初の 50 の発話のみを分析します。送信された発話の 1 つが 500 文字を超える場合、サービスはその発話に対して `error` フィールドを返し、その発話を分析しません。ただし、どちらの場合も HTTP 応答コード 200 で要求は成功します。

> **注:** 入力の発話のすべてが 500 文字を超える場合は、サービスは応答コード 400 を返します。

### 要求の例
{: #exampleRequest}

以下の cURL コマンド例は、入力ファイル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> とバージョン `2017-09-21` を指定して、カスタマー・エンゲージメント・エンドポイントを呼び出します。

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## JSON 入力の指定
{: #JSONrequest}

以下の形式で、メソッドに JSON `ToneChatInput` オブジェクトを渡します。`utterances` フィールドには、`utterance` オブジェクトの配列を指定します。`text` は、分析対象の会話でユーザーが発言した発話を指定する必須ストリングです。`user` は、その発話を発言したユーザーを示すオプションのストリングです。

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

以下の例は、<a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルの内容を示しています。このファイルには、<code>customer</code> と <code>agent</code> の間の短いやり取りが含まれます。

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

## JSON 応答コンテンツ
{: #JSONresponse}

サービスが返す JSON オブジェクト `UtteranceAnalyses` には、単一のフィールド `utterances_tone` が含まれます。このフィールドには `UtteranceAnalysis` オブジェクトで構成された配列が含まれ、各オブジェクトには入力コンテンツの 1 つの発話についての以下の情報が入っています。

-   `utterance_id` (整数) は、発話の固有 ID を示します。最初の発話の ID は 0 で、その後の発話の ID は 1 つずつ増えていきます。
-   `utterance_text` (ストリング) は、発話のテキストを示します。
-   `tones` は、支配的なトーン (スコアが 0.5 以上のトーン) の結果を示す `ToneChatScore` オブジェクトの配列です。このしきい値を満たすスコアのトーンが発話に存在しない場合、配列は空になります。

各 `ToneChatScore` オブジェクトには、該当するトーンに関する以下の情報が示されます。

-   `score` (倍精度浮動小数点数) は、0.5 から 1 までの範囲のトーンのスコアです。0.75 より大きいスコアは、発話でそのトーンが受け取られる可能性が高いことを示します。
-   `tone_id` (ストリング) は、トーンの (ローカライズされない) 固有 ID です。各トーンの説明については、[カスタマー・エンゲージメントのトーン](#tones)を参照してください。
-   `tone_name` (ストリング) は、ユーザーに表示されるトーンのローカライズ名です。

次の例は、`UtterancesAnalyses` オブジェクトの構造を示しています。

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

### 応答の例
{: #exampleResponse}

前の[要求の例](#exampleRequest)に対して、次の出力が返されます。([入門チュートリアル](/docs/services/tone-analyzer/getting-started.html#customerEngagement)の例でも同じ出力が返されます)。報告されるトーンはすべてスコアが 0.5 以上のものです。スコアが 0.75 以上のトーンは、会話の参加者がそのトーンを受け取る可能性が高いものです。

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.718352,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": []
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997149,
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
          "score": 0.689109,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.663203,
          "tone_id": "sympathetic",
          "tone_name": "Sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## カスタマー・エンゲージメントのトーン
{: #tones}

サービスは、以下の 7 つのトーンのスコアを返すことができます。

<table style="width:90%">
  <caption>表 2. カスタマー・エンゲージメントのトーン</caption>
  <tr>
    <th style="text-align:left; width:20%">トーン / ID</th>
    <th style="text-align:left">説明</th>
  </tr>
  <tr>
    <td>興奮<br/><code>excited</code></td>
    <td>
人の熱烈な興味や関心を表します</td>
  </tr>
  <tr>
    <td>不満<br/><code>frustrated</code></td>
    <td>
不快やいらだちの感情として定義されます</td>
  </tr>
  <tr>
    <td>不作法<br/><code>impolite</code></td>
    <td>
失礼また無礼であることです</td>
  </tr>
  <tr>
    <td>礼儀正しさ<br/><code>polite</code></td>
    <td>
理性的で目的のはっきりした振る舞いとして定義されます</td>
  </tr>
  <tr>
    <td>悲しみ<br/><code>sad</code></td>
    <td>
好ましくない消極的な感情と見なされます</td>
  </tr>
  <tr>
    <td>満足<br/><code>satisfied</code></td>
    <td>
受け取られたサービス品質に対する感情反応です</td>
  </tr>
  <tr>
    <td>共感<br/><code>sympathetic</code></td>
    <td>
感情的共鳴を伴う感情モードの理解です</td>
  </tr>
</table>
