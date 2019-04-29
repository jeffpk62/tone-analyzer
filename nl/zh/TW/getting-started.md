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

# 入門指導教學
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} 服務可分析輸入內容的語氣。本指導教學會顯示分析不同範例內容的指令。這些範例示範一般用途及客戶參與端點。
{: shortdesc}

此指導教學使用 {{site.data.keyword.cloud}} Identity and Access Management (IAM) API 金鑰進行鑑別。舊的服務實例可能會繼續使用其現有 Cloud Foundry 服務認證中的 `{username}` 及 `{password}` 來進行鑑別。使用適合服務實例的方式來進行鑑別。如需服務使用 IAM 鑑別的相關資訊，請參閱[版本注意事項](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)。
{: important}

## 開始之前
{: #prerequisites}

- {: hide-dashboard}建立服務的實例：
    1.  {: hide-dashboard} 移至「{{site.data.keyword.cloud_notm}} 型錄」中的 [{{site.data.keyword.toneanalyzershort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} 頁面。
    1.  {: hide-dashboard} 註冊免費的 {{site.data.keyword.cloud_notm}} 帳戶或登入。
    1.  {: hide-dashboard} 按一下**建立**。
-   複製用來向服務實例進行鑑別的認證：
    1.  {: hide-dashboard} 從 [{{site.data.keyword.cloud_notm}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/dashboard/apps){: new_window} 中，按一下 {{site.data.keyword.toneanalyzershort}} 服務實例以移至 {{site.data.keyword.toneanalyzershort}} 服務儀表板頁面。
    1.  在**管理**頁面上，按一下**顯示**以檢視您的認證。
    1.  複製 `API 金鑰`及 `URL` 值。
-   確定您具有 `curl` 指令。
    -   這些範例使用 `curl` 指令來呼叫 HTTP 介面的方法。請從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝您的作業系統適用的版本。請安裝支援 Secure Sockets Layer (SSL) 通訊協定的版本。請一定要在 `PATH` 環境變數中包含已安裝的二進位檔。

當您輸入指令時，請將 `{apikey}` 及 `{url}` 取代為實際 API 金鑰及 URL。請省略指令中的大括弧，而大括弧指出變數值。實際值與下列範例類似：
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## 步驟 1：透過 POST 要求方法來使用一般用途端點
{: #generalPurposePost}

下列指令會呼叫 `POST /v3/tone` 方法，以分析 `tone.json` 檔案的內容。此檔案包含一個人所撰寫的一段純文字。這些範例示範方法的 `sentences` 查詢參數。

1.  下載範例檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a>。
1.  發出下列指令，以分析整體內容及每個個別句子的語氣。
    -   {: hide-dashboard} 將 `{apikey}` 及 `{url}` 取代為您的資訊。
    -   修改 `{path_to_file}` 以指定 `tone.json` 檔案的位置。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  發出下列指令，透過將 `sentences` 參數設為 `false`，只分析整體內容的語氣。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

如需方法輸出的範例，請參閱[範例回應](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone)。

## 步驟 2：透過 GET 要求方法來使用一般用途端點
{: #generalPurposeGet}

此介面也提供 `GET /v3/tone` 方法。`GET` 方法提供與 `POST` 方法相同的功能，並產生相同的結果，但您使用方法的 `text` 查詢參數來指定要分析的內容。此方法僅接受純文字輸入。

1.  下列範例透過 `text` 參數指定 `tone.json` 檔案的文字；如下所示，您必須對該文字進行 URL 編碼。指令會省略 `sentences` 參數，因此它會傳回與先前顯示的第一個 `POST` 範例相同的輸出。（此範例包含換行以提高可讀性；請勿在實際指令中包含換行。）

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## 步驟 3：使用客戶參與端點
{: #customerEngagement}

下列指令會呼叫 `POST /v3/tone_chat` 方法，以分析 `tone-chat.json` 檔案的內容。此檔案包含兩個人（<code>customer</code> 及 <code>agent</code>）之間的簡短訊息交流。

1.  下載範例檔 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部鏈結圖示" title="外部鏈結圖示"></a>。
1.  發出下列指令來分析範例檔案中的交流語氣。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

服務的回應指出針對輸入的每個陳述偵測到的最普遍語氣。若要檢視此要求的回應內容，請參閱[範例回應](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat)。

## 後續步驟
{: #gsns}

-   如需 `/v3/tone` 方法的相關資訊，請參閱[使用一般用途端點](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)。
-   如需 `/v3/tone_chat` 方法的相關資訊，請參閱[使用客戶參與端點](/docs/services/tone-analyzer?topic=tone-analyzer-utco)。
-   如需服務介面方法的相關資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。
