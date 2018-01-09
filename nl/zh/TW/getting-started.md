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

# 入門指導教學

{{site.data.keyword.toneanalyzershort}} 服務可分析輸入內容的語氣。本指導教學會顯示分析不同範例內容的指令。這些範例同時示範一般用途端點及客戶參與端點。
{: shortdesc}

## 開始之前
{: #prerequisites}

- 建立服務的實例：
    - {: download} 如果您看到此項目，則表示您已建立服務實例。現在，請取得您的認證。
    - 從服務中建立專案：
        1.  移至 {{site.data.keyword.watson}} Developer Console [服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/developer/watson/services){: new_window} 頁面。
        1.  選取 {{site.data.keyword.toneanalyzershort}}，按一下**新增服務**，然後註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶或登入。
        1.  鍵入 `tone-tutorial` 作為專案名稱，然後按一下**建立專案**。
- 複製用來向服務實例進行鑑別的認證：
    - {: download} 從您正在查看的服務儀表板中：
        1.  按一下**服務認證**標籤。
        1.  按一下**動作**下的**檢視認證**。
        1.  複製 `username`、`password` 及 `url` 值。
        {: download}
    - 從 Developer Console 的 **tone-tutorial** 專案中，複製**認證**區段中 `"tone_analyzer"` 的 `username`、`password` 及 `url` 值。
- 確定您有 cURL：
    - 這些範例使用 cURL 來呼叫 HTTP 介面的方法。請從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝您的作業系統適用的版本。請安裝支援 Secure Sockets Layer (SSL) 通訊協定的版本。請一定要在 `PATH` 環境變數中包含已安裝的二進位檔。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果您使用{{site.data.keyword.Bluemix_dedicated_notm}}，請從「型錄」的 [{{site.data.keyword.toneanalyzershort}}![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} 頁面建立服務實例。如需如何尋找服務認證的詳細資料，請參閱 [Watson 服務的服務認證 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步驟 1：透過 POST 要求方法來使用一般用途端點
{: #generalPurposePost}

下列指令會呼叫 `POST /v3/tone` 方法，以分析 `tone.json` 檔案的內容。此檔案包含一個人所撰寫的一段純文字。這些範例示範方法的 `sentences` 查詢參數。

1.  下載範例檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a>。
1.  發出下列指令，以分析整體內容及每個個別句子的語氣。
    -   將 `{username}` 及 `{password}` 取代為先前步驟中的服務認證。
    -   修改 `{path_to_file}` 以指定 `tone.json` 檔案的位置。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  發出下列指令，透過將 `sentences` 參數設為 `false`，只分析整體內容的語氣。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

如需方法輸出的範例，請參閱[範例回應](/docs/services/tone-analyzer/using-tone.html#exampleResponse)。

## 步驟 2：透過 GET 要求方法來使用一般用途端點
{: #generalPurposeGet}

此介面也提供 `GET /v3/tone` 方法。`GET` 方法提供與 `POST` 方法相同的功能，並產生相同的結果，但您使用方法的 `text` 查詢參數來指定要分析的內容。此方法僅接受純文字輸入。

1.  下列範例透過 `text` 參數指定 `tone.json` 檔案的文字；如下所示，您必須對該文字進行 URL 編碼。指令會省略 `sentences` 參數，因此它會傳回與先前顯示的第一個 `POST` 範例相同的輸出。（此範例包含換行以提高可讀性；請勿在實際指令中包含換行。）

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## 步驟 3：使用客戶參與端點
{: #customerEngagement}

下列指令會呼叫 `POST /v3/tone_chat` 方法，以分析 `tone-chat.json` 檔案的內容。此檔案包含兩個人（<code>customer</code> 及 <code>agent</code>）之間的簡短訊息交流。

1.  下載範例檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示" class="style-scope doc-content"></a>。
1.  發出下列指令來分析範例檔案中的交流語氣。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

服務的回應指出針對輸入的每個陳述偵測到的最普遍語氣。若要檢視此要求的回應內容，請參閱[範例回應](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse)。

## 後續步驟

-   如需 `/v3/tone` 方法的相關資訊，請參閱[使用一般用途端點](/docs/services/tone-analyzer/using-tone.html)。
-   如需 `/v3/tone_chat` 方法的相關資訊，請參閱[使用客戶參與端點](/docs/services/tone-analyzer/using-tone-chat.html)。
-   如需服務介面方法的詳細資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}。
-   在 [API 瀏覽器 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window} 中與 API 互動。
