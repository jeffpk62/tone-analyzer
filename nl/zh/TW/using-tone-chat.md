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

# 使用客戶參與端點

{{site.data.keyword.toneanalyzershort}} 客戶參與端點會分析客戶服務及支援交談的語氣。它能幫助您更充分地瞭解與客戶的互動，並改善您一般或特定客戶的溝通。如需介面的詳細資訊，包括可用於呼叫服務的 Node.js、Java 及 Python SDK，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}。
{: shortdesc}

## 要求語氣分析
{: #request}

若要分析客戶參與端點的語氣，您可以使用下列參數來呼叫 `POST /v3/tone_chat` 方法。

<table>
  <caption>表 1. <code>POST /v3/tone_chat</code> 方法的參數</caption>
  <tr>
    <th style="text-align:left; width:20%">參數</th>
    <th style="text-align:center; width:12%">類型</th>
    <th style="text-align:center; width:20%">資料類型</th>
    <th style="text-align:left">說明</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>必要</em></td>
    <td style="text-align:center">內文</td>
    <td style="text-align:center">JSON 物件</td>
    <td>
      包含要分析之內容的 JSON <code>ToneChatInput</code> 物件。請參閱<a href="#JSONrequest">指定 JSON 輸入</a>。</td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必要</em></td>
    <td style="text-align:center">查詢</td>
    <td style="text-align:center">字串</td>
    <td>
      所要求的介面版本，日期格式為
      <code>YYYY-MM-DD</code>；例如，指定 <code>2017-09-21</code>
      代表 2017 年 9 月 21 日。
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>選用</em></td>
    <td style="text-align:center">標頭</td>
    <td style="text-align:center">字串</td>
    <td>
      回應的想要語言：
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar（阿拉伯文）
        </li>
        <li style="margin:0px; padding:0px">
          de（德文）
        </li>
        <li style="margin:0px; padding:0px">
          en（英文，預設值）
        </li>
        <li style="margin:0px; padding:0px">
          es（西班牙文）
        </li>
        <li style="margin:0px; padding:0px">
          fr（法文）
        </li>
        <li style="margin:0px; padding:0px">
          it（義大利文）
        </li>
        <li style="margin:0px; padding:0px">
          ja（日文）
        </li>
        <li style="margin:0px; padding:0px">
          ko（韓文）
        </li>
        <li style="margin:0px; padding:0px">
          pt-br（巴西葡萄牙文）
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn（簡體中文）
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw（繁體中文）
        </li>
      </ul>
    </td>
  </tr>
</table>

如果您提交超過 50 個以上的陳述，服務會在其回應的 `utterances_tone` 層次，針對整體內容傳回 `warning` 欄位；它只會分析前 50 個陳述。如果您提交包含超過 500 個字元的單一陳述，則服務會傳回該陳述的 `error` 欄位，且不分析陳述。在這兩種情況下，要求仍然成功，並顯示 HTTP 回應碼 200。

> **附註：**如果輸入的所有陳述超過 500 個字元，則服務會傳回回應碼 400。

### 範例要求
{: #exampleRequest}

下列範例 cURL 指令會使用輸入檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 和版本 `2017-09-21` 呼叫客戶參與端點：

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## 指定 JSON 輸入
{: #JSONrequest}

您會使用下列格式，來傳遞 JSON `ToneChatInput` 物件給方法。`utterances` 欄位提供 `utterance` 物件的陣列，其中 `text` 是一個必要字串，它提供使用者提供給要分析之交談的陳述，而 `user` 是選用字串，用來識別提供陳述的使用者。

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

下列範例顯示 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a> 檔案的內容。檔案包含 <code>customer</code> 與 <code>agent</code> 之間的短暫交流。

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

## JSON 回應內容
{: #JSONresponse}

服務會傳回包含單一欄位 `utterances_tone` 的 JSON `UtteranceAnalyses` 物件。這個欄位包含 `UtteranceAnalysis` 物件的陣列，其中每個都提供輸入內容之陳述的下列資訊：

-   `utterance_id`（整數）提供陳述的唯一 ID。第一個陳述的 ID 為 0，且每一個後續的陳述 ID 都加 1。
-   `utterance_text`（字串）提供陳述的文字。
-   `tones` 是提供主要語氣結果的 `ToneChatScore` 物件陣列，這些語氣的評分至少為 0.5。如果陳述沒有評分符合此臨界值的語氣，則陣列為空陣列。

每一個 `ToneChatScore` 物件提供合格語氣的下列相關資訊：

-   `score`（倍精準數）是介於 0.5 到 1 範圍內的語氣評分。大於 0.75 的評分表示很有可能察覺到陳述中的語氣。
-   `tone_id`（字串）是語氣的唯一、未本地化 ID；如需語氣的說明，請參閱[客戶參與語氣](#tones)。
-   `tone_name`（字串）是使用者可見的語氣本地化名稱。

下列範例顯示 `UtterancesAnalyses` 物件的結構：

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

### 範例回應
{: #exampleResponse}

對於[範例要求](#exampleRequest)，會傳回下列輸出。（對於[入門指導教學](/docs/services/tone-analyzer/getting-started.html#customerEngagement)中的範例，會傳回相同的輸出。）所有報告的語氣評分至少為 0.5，且評分至少為 0.75 的語氣很可能已被交談的參與者察覺。

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

## 客戶參與語氣
{: #tones}

服務可以傳回下列七種語氣的評分。

<table style="width:90%">
  <caption>表 2. 客戶參與語氣</caption>
  <tr>
    <th style="text-align:left; width:20%">語氣 / ID</th>
    <th style="text-align:left">說明</th>
  </tr>
  <tr>
    <td>興奮<br/><code>excited</code></td>
    <td>
      顯示個人熱忱與興趣
    </td>
  </tr>
  <tr>
    <td>挫敗<br/><code>frustrated</code></td>
    <td>
      定義為感覺煩惱且急躁
    </td>
  </tr>
  <tr>
    <td>沒有禮貌<br/><code>impolite</code></td>
    <td>
      失禮且粗魯
    </td>
  </tr>
  <tr>
    <td>有禮貌<br/><code>polite</code></td>
    <td>
      定義為理智、目標導向的行為
    </td>
  </tr>
  <tr>
    <td>悲傷<br/><code>sad</code></td>
    <td>
      視為不愉快的被動情緒
    </td>
  </tr>
  <tr>
    <td>滿意<br/><code>satisfied</code></td>
    <td>
      對察覺到的服務品質的情緒回應
    </td>
  </tr>
  <tr>
    <td>同情<br/><code>sympathetic</code></td>
    <td>
      牽涉到情緒回響的情緒理解模式
    </td>
  </tr>
</table>
