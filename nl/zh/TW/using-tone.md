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

# 使用一般用途端點
{: #utgpe}

{{site.data.keyword.toneanalyzershort}} 一般用途端點會分析書面通訊的語氣，從簡短的電子郵件訊息到更長的文件。它可以幫助您瞭解通訊的情緒和語言語氣。如需介面的相關資訊，包括可用於呼叫服務的 Node.js、Java 及 Python SDK，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。
{: shortdesc}

已停用 {{site.data.keyword.toneanalyzershort}} 服務的要求記載。不論是否設定 `X-Watson-Learning-Opt-Out` 要求標頭，服務都不會記載或保留要求及回應中的資料。
{: note}

## 要求語氣分析
{: #request-tone}

為了使用一般用途端點來分析語氣，您可以呼叫服務的兩個 `tone` 方法版本之一：

-   `POST /v3/tone` 方法透過要求的必要內文，接受 JSON、純文字或 HTML 格式的輸入內容。請將此版本的方法用於較長的文字，或用於您不想在 URL 上公開的文字。
-   `GET /v3/tone` 方法透過其必要的 `text` 查詢參數接受輸入內容。請將此版本的方法用於可輕鬆容納於 URL 的簡單文字。

這些方法接受下列參數。

<table>
  <caption>表 1. <code>/v3/tone</code> 方法的參數</caption>
  <tr>
    <th style="text-align:left; width:20%">參數</th>
    <th style="text-align:center; width:12%">類型</th>
    <th style="text-align:center; width:20%">資料類型</th>
    <th style="text-align:left">說明</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em><code>POST</code> 需要</em></td>
    <td style="text-align:center">內文</td>
    <td style="text-align:center">JSON 物件 | 字串</td>
    <td>
      包含要分析之內容的 JSON、純文字或 HTML 輸入。對於 JSON 輸入，請提供類型為 <code>ToneInput</code> 的物件。如需相關資訊，請參閱[指定 JSON 輸入](#JSONinput)。<em>不支援 <code>GET</code> 要求。</em></td>
  </tr>
  <tr>
    <td><code>text</code><br/><em><code>GET</code> 需要</em></td>
    <td style="text-align:center">查詢</td>
    <td style="text-align:center">字串</td>
    <td>
      包含要分析之內容的純文字輸入。您必須將輸入以
      URL 編碼。<em>不支援 <code>POST</code> 要求。</em></td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em><code>POST</code> 需要</em></td>
    <td style="text-align:center">標頭</td>
    <td style="text-align:center">字串</td>
    <td>
      要求的內容類型。
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> 適用於純文字
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> 適用於 HTML 格式的文字（服務會移除
            HTML 標籤，並只分析文字內容）
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> 適用於 JSON 格式的文字
        </li>
      </ul>
    <em>針對 <code>GET</code> 要求省略。</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必要</em></td>
    <td style="text-align:center">查詢</td>
    <td style="text-align:center">字串</td>
    <td>
      您要使用的 API 版本，日期格式為 <code>YYYY-MM-DD</code>；例如，指定 <code>2017-09-21</code> 代表 2017 年 9 月 21 日（最新版本）。如需所有可用版本的相關資訊，請參閱[版本注意事項](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)。
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>選用</em></td>
    <td style="text-align:center">標頭</td>
    <td style="text-align:center">字串</td>
    <td>
      輸入內容的語言。
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code>（英文，預設值）
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code>（法文）</li>
      </ul>
      地區變式會被視為其母項語言；例如 <code>en-US</code> 會解譯為 <code>en</code>。輸入內容必須符合指定的語言。請勿提交包含兩種語言的內容。
您可以對輸入及回應使用不同的語言。</td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>選用</em></td>
    <td style="text-align:center">標頭</td>
    <td style="text-align:center">字串</td>
    <td>
      針對回應所要求的語言。
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code>（阿拉伯文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>de</code>（德文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code>（英文，預設值）
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code>（西班牙文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code>（法文）</li>
        <li style="margin:0px; padding:0px">
          <code>it</code>（義大利文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code>（日文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code>（韓文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code>（巴西葡萄牙文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code>（簡體中文）
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code>（繁體中文）
        </li>
      </ul>
      若為兩個字元的引數，地區變式會被視為其母項語言；例如 <code>en-US</code> 會解譯為 <code>en</code>。您可以對輸入及回應使用不同的語言。</td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>選用</em></td>
    <td style="text-align:center">查詢</td>
    <td style="text-align:center">布林</td>
    <td>
      指出服務是否要在完整文件的分析之外，額外傳回每個個別句子的分析。若為 <code>true</code>（預設值），服務會傳回每個句子的結果。
    </td>
  </tr>
</table>

提交時請不要超過總計 128 KB 的輸入內容，而且不要超過 1000 個個別句子。服務會分析文件層次的前 1000 個句子，且僅會分析句子層次的前 100 個句子。它會在您超過任一限制時，在回應當中傳回 `warning` 欄位；要求仍會成功，HTTP 回應碼為 200。

### 範例要求
{: #exampleRequests}

下列範例 `curl` 指令使用 HTTP `POST` 要求方法，以輸入檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 及版本 `2017-09-21` 呼叫一般用途端點。此範例要求完整文件及個別句子的分析。

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

下列範例指令與前一個範例相等，但使用 HTTP `GET` 要求方法：

```bash
curl -X GET -u "apikey:{apikey}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

如需其他範例，請參閱[入門指導教學](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted)。

### 指定字集
{: #charset}

依預設，服務會對輸入內容使用下列字集：

-   *對於純文字和 HTML 內容*，服務根據 HTTP 1.1 版規格，使用國際標準組織 (ISO)-8859-1 字集（實際上是 ASCII 字集）。
-   *對於 JSON 內容*，服務根據國際工程工作小組 (IETF) [徵求意見稿 (RFC) 7159 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window} 8.1 節，實際上一律使用 Unicode 轉換格式 (UTF)-8 字集。

提交純文字或 HTML 內容時，請用 `Content-Type` 標頭來包含 `charset` 參數，以指出輸入文字的字元編碼。下列範例指定純文字輸入的 UTF-8 字元編碼：

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

使用 `charset` 參數，您可以避免與非 ASCII 或不可列印字元相關聯的潛在問題。如果您傳遞 UTF-8 資料，但未指定字集，則特殊字元可能導致不正確的結果，或可能會導致 HTTP 400 或 500 層次錯誤。

為了防止在使用 `curl` 時發生類似的錯誤，請一律透過 `curl` 指令的 `--data-binary` 選項傳遞內容，以保留內容的任何 UTF-8 編碼。如果您使用 `--data` 選項將內容傳遞為 ASCII，則指令可以處理輸入，這可能會導致以 UTF-8 編碼的資料發生問題。

## 指定 JSON 輸入
{: #JSONinput}

若要使用 `POST` 要求方法來分析 JSON 輸入，您可以採用下列簡單格式來傳遞 JSON `ToneInput` 物件給方法：

```javascript
{
  "text": ""
}
```
{: codeblock}

下列範例顯示 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a> 檔案的內容，該檔案會與[入門指導教學](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted)中的範例搭配使用。檔案包含由一個人所撰寫的單一文字段落。（下列文字包含換行以方便閱讀；實際輸入時請勿包含換行。）

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## JSON 回應內容
{: #JSONresponse-tone}

服務會傳回一律包含 `document_tone` 欄位的 JSON `ToneAnalysis` 物件。這個欄位包含提供完整輸入文件分析的 `DocumentAnalysis` 物件。它包含單一欄位 `tones`，可為文件的每一個合格語氣提供分析的結果。

如果要求的 `sentences` 參數已省略，或是設為 `true`，則回應也會包含 `sentences_tone` 欄位。這個欄位包含 `SentenceAnalysis` 物件的陣列，其中每個都提供輸入內容之不同句子的下列資訊：

-   `sentence_id`（整數）提供句子的唯一 ID。第一個句子的 ID 為 0，且每一個後續的句子 ID 都加 1。
-   `text`（字串）提供句子的文字。
-   `tones` 會針對句子的每一個合格語氣提供分析的結果。

下列範例顯示 `ToneAnalysis` 物件的高階結構：

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

### 語氣及評分結果
{: #uttsr}

針對文件及句子層次分析所傳回的 `tones` 欄位，包含 `ToneScore` 物件的陣列，這些物件提供主要語氣的結果。這類語氣的評分至少為 0.5。如果沒有評分符合此臨界值的語氣，則陣列為空陣列。每一個 `ToneScore` 物件提供合格語氣的下列相關資訊：

-   `score`（倍精準數）是介於 0.5 到 1 範圍內的語氣評分。大於 0.75 的評分表示很有可能察覺到內容中的語氣。
-   `tone_id`（字串）是語氣的唯一、未本地化 ID；如需語氣的說明，請參閱[一般用途語氣](#tones-tone)。
-   `tone_name`（字串）是使用者可見的語氣本地化名稱。

下列範例顯示 `ToneScore` 物件的結構：

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

### 範例回應
{: #exampleResponse-tone}

對於[範例要求](#exampleRequests)，會傳回下列輸出。（對於[入門指導教學](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted)中的第一個範例，會傳回相同的輸出。）回應包括完整文件和每個個別句子的結果。所有報告的語氣評分至少為 0.5。評分至少為 0.75 的語氣可能已在內容中察覺。

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

## 一般用途語氣
{: #tones-tone}

下表說明服務可傳回的一般用途語氣。評分少於 0.5 的語氣會被省略，這表示不太可能在內容中察覺情緒。大於 0.75 的評分表示很有可能察覺到語氣。

<table>
  <caption>表 2. 一般用途語氣</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">語氣 / ID</th>
    <th style="text-align:left">說明</th>
  </tr>
  <tr>
    <td>憤怒<br/><code>anger</code></td>
    <td>
      憤怒因不公、衝突、羞辱、疏忽或背叛而致。如果憤怒是主動的，則該人會以口頭方式或實體方式攻擊目標。如果憤怒是被動的，則該人會生悶氣，並感到緊張和敵意。（情緒性的語氣。）</td>
  </tr>
  <tr>
    <td>恐懼<br/><code>fear</code></td>
    <td>
      恐懼是對於即將發生之危險的回應。它是一種生存機制，會因為對部分負面刺激的反應而觸發。恐懼可能是適度的小心或是極端的恐懼。（情緒性的語氣。）</td>
  </tr>
  <tr>
    <td>高興<br/><code>joy</code></td>
    <td>
      高興（或快樂）具有享受、滿足和愉悅。高興會帶來健康感、內心平靜、愛、安全和滿足。（情緒性的語氣。）</td>
  </tr>
  <tr>
    <td>悲傷<br/><code>sadness</code></td>
    <td>
      悲傷表示失去和不利的感覺。當一個人安靜、無精打采且退縮時，可以推斷他們感覺悲傷。（情緒性的語氣。）</td>
  </tr>
  <tr>
    <td>分析<br/><code>analytical</code></td>
    <td>
      分析語氣表示一個人對事物的推理和分析態度。分析性的人可能認為是智慧、理性、系統化、無情緒或是冷漠。（語言語氣。）</td>
  </tr>
  <tr>
    <td>自信<br/><code>confident</code></td>
    <td>
      自信的語氣表示一個人的確定程度。自信的人可能被認為是有把握、鎮定、有希望或自我中心。（語言語氣。）</td>
  </tr>
  <tr>
    <td>猶豫<br/><code>tentative</code></td>
    <td>
猶豫的語氣表示一個人的壓抑程度。猶豫的人可能被認為是可疑、令人懷疑或有爭議。（語言語氣。）</td>
  </tr>
</table>
