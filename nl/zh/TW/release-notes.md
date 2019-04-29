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

# 版本注意事項
{: #rnrn}

下列各節記載了 {{site.data.keyword.toneanalyzershort}} 服務的每一個版本所包含的新增特性及變更。變更不會岔斷現有的程式碼。
{: shortdesc}

版本注意事項會記載每次更新的*服務版本* 及*介面版本*。請以 `version` 查詢參數指定*介面版本*，才能使用該更新所提供的新增特性及功能。服務會使用 `X-Service-Api-Version` 回應標頭來傳回這兩個版本。
{: note}

## 2019 年 2 月 22 日
{: #February2019}

**服務版本** - `3.5.9`<br/> **介面版本** - `2017-09-21`

-   {{site.data.keyword.cloud}} 法蘭克福位置 (**eu-de**) 中的 {{site.data.keyword.toneanalyzershort}} 服務現在會使用記號型 Identity and Access Management (IAM) 鑑別。所有在這個或任何位置中建立的新服務實例都會使用 IAM 鑑別。
-   也會更新服務的內部變更及改善。

## 2018 年 11 月 18 日
{: #November2018b}

**服務版本** - `3.5.4`<br/> **介面版本** - `2017-09-21`

{{site.data.keyword.cloud_notm}} 倫敦位置 (**eu-gb**) 現在可以使用 {{site.data.keyword.toneanalyzershort}} 服務。與所有位置類似，倫敦會使用記號型 IAM 鑑別。所有在此位置中建立的新服務實例都會使用 IAM 鑑別。

## 2018 年 11 月 7 日
{: #November2018a}

**服務版本** - `3.5.4`<br/> **介面版本** - `2017-09-21`

{{site.data.keyword.cloud_notm}} 東京位置 (**jp-tok**) 現在可以使用 {{site.data.keyword.toneanalyzershort}} 服務。與所有位置類似，東京會使用記號型 IAM 鑑別。所有在此位置中建立的新服務實例都會使用 IAM 鑑別。

## 較舊版本
{: #rnor}

  - [2018 年 10 月 30 日](#30-october-2018)
  - [2018 年 6 月 11 日](#11-june-2018)
  - [2018 年 5 月 25 日](#25-may-2018)
  - [2018 年 3 月 13 日](#13-march-2018)
  - [2017 年 9 月 28](#28-september-2017)
  - [2017 年 9 月 25 日](#25-september-2017)
  - [2017 年 7 月 6 日](#6-july-2017)
  - [2017 年 7 月 1 日](#1-july-2017)
  - [2017 年 5 月 8 日](#8-may-2017)
  - [2017 年 4 月 17 日](#17-april-2017)
  - [2017 年 3 月 15 日](#15-march-2017)
  - [2016 年 12 月 1 日](#1-december-2016)
  - [2016 年 10 月 18 日](#18-october-2016)
  - [2016 年 10 月 3 日](#3-october-2016)
  - [2016 年 5 月 19 日](#19-may-2016)

### 2018 年 10 月 30 日
{: #October2018}

**服務版本** - `3.5.4`<br/> **介面版本** - `2017-09-21`

所有位置的 {{site.data.keyword.toneanalyzershort}} 服務都已移轉至記號型 IAM 鑑別。所有 {{site.data.keyword.cloud_notm}} 服務現在都會使用 IAM 鑑別。每個位置已在下列日期移轉的 {{site.data.keyword.toneanalyzershort}} 服務：

-   達拉斯 (**us-south**)：2018 年 10 月 30 日
-   法蘭克福 (**eu-de**)：進行中
-   華盛頓特區 (**us-east**)：2018 年 6 月 11 日
-   雪梨 (**au-syd**)：2018 年 5 月 25 日

在法蘭克福位置，此服務繼續使用 Cloud Foundry 服務認證進行鑑別。此位置將盡快移轉至 IAM 鑑別。
{: important}

移轉至 IAM 鑑別會以不同的方式影響新的及現有服務實例：

-   *所有您在任何位置建立的新服務實例* 現在都會使用 IAM 鑑別來存取服務。您可以傳遞 Bearer 記號或 API 金鑰：記號支援已鑑別要求，而不在每個呼叫中內嵌服務認證；API 金鑰會使用 HTTP 基本鑑別。當您使用任何 {{site.data.keyword.watson}} SDK 時，可以傳遞 API 金鑰，並讓 SDK 管理記號的生命週期。
-   *在指出的移轉日期之前於位置中建立的現有服務實例* 會繼續使用其先前 Cloud Foundry 服務認證中的 `{username}` 及 `{password}` 來進行鑑別，直到您更新它們以使用 IAM 鑑別為止。因為 {{site.data.keyword.toneanalyzershort}} 服務是無狀態的，所以您可以執行下列步驟，以將現有服務實例轉換成使用 IAM 鑑別：

    1.  刪除並重建服務實例。
    1.  修改應用程式碼以使用 IAM 鑑別。

如需相關資訊，請參閱下列文件：

-   若要瞭解您服務實例所使用的鑑別機制，請在 [{{site.data.keyword.cloud_notm}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/dashboard/apps){: new_window} 上按一下實例來檢視服務認證。
-   如需搭配使用 IAM 記號與 Watson 服務的相關資訊，請參閱[使用 IAM 記號鑑別](/docs/services/watson?topic=watson-iam)。
-   如需搭配使用 IAM API 金鑰與 Watson 服務的相關資訊，請參閱 [IAM 服務 API 金鑰](/docs/services/watson?topic=watson-api-key-bp)。
-   如需使用 IAM 鑑別的範例，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。

### 2018 年 6 月 11 日
{: #June2018}

**服務版本** - `3.5.4`<br/> **介面版本** - `2017-09-21`

對於華盛頓特區 (**us east**) 中所管理的服務實例及應用程式，此服務現在支援新的 API 鑑別處理程序。如需相關資訊，請參閱 [2018 年 10 月 30 日服務更新](#October2018)。

### 2018 年 5 月 25 日
{: #May2018}

**服務版本** - `3.5.4`<br/> **介面版本** - `2017-09-21`

對於雪梨 (**au-syd**) 中所管理的服務實例及應用程式，此服務現在支援新的 API 鑑別處理程序。如需相關資訊，請參閱 [2018 年 10 月 30 日服務更新](#October2018)。

### 2018 年 3 月 13 日
{: #March2018}

**服務版本** - `3.5.3`<br/> **介面版本** - `2017-09-21`

對於客戶參與端點 `/v3/tone_chat`，除了英文之外，此服務也已更新成新增法文 (`fr`) 輸入內容。您可以使用 `Content-Language` 要求標頭來指定語言；預設值是美式英文。

### 2017 年 9 月 28
{: #September2017b}

**服務版本** - `3.4.1`<br/> **介面版本** - `2017-09-21`

個別 {{site.data.keyword.cloud_notm}} 使用者名稱可提交之要求數上限的節流控制限制已增加為每分鐘 1200 個要求。如果使用者超出限制，則服務會傳回 HTTP 回應碼 429 *要求太多*。

### 2017 年 9 月 25 日
{: #September2017a}

**服務版本** - `3.4.1`<br/> **介面版本** - `2017-09-21`

-   一般用途端點（`/v3/tone` 方法）已變更。

    -   除了英文之外，還支援法文 (`fr`) 輸入內容。
    -   不再傳回社交語氣。
    -   不再與情緒語氣一起傳回 `disgust`。
    -   省略其評分小於 `0.5` 的任何語氣。此資格符合 `/v3/tone_chat` 方法的回應。
    - 不再傳回語氣種類（`tone_categories` 欄位）作為其輸出的一部分。其值符合限定臨界值的所有語氣都會傳回作為單一 `tones` 物件的一部分。與之前一樣，預設一律會針對完整文件及每個個別句子傳回語氣。
    - 不再接受 `tones` 查詢參數，無法將輸出限制為指定的語氣。系統會針對每個要求傳回所有限定語氣。在要求中包含參數並不會造成錯誤，但它對回應沒有影響。
    - 不再針對個別句子傳回 `input_from` 及 `input_to` 欄位。除了其分析結果之外，此方法現在只會傳回 ID 及每一個句子的文字。

-   現在，服務會在下列情況下針對部分正確的輸入傳回 HTTP 回應碼 200（而非 400）：

    -   若為 `/v3/tone` 方法，如果您提交超過 128 KB 或 1000 個句子的輸入內容，則服務會傳回 `warning` 欄位作為其回應的一部分。服務會分析文件層次分析的前 1000 個句子。它只會分析句子層次分析的前 100 個句子。如果您超出任一限制，舊版的服務會針對要求傳回回應碼 400。服務現在也會分析少於三個單字的句子。
    -   若為 `/v3/tone_chat` 方法，如果您提交超過 50 個陳述，則服務會在回應的 `utterances_tone` 層次，針對整體內容傳回 `warning` 欄位；它只會分析前 50 個陳述。如果您提交包含超過 500 個字元的單一陳述，則服務會針對該陳述傳回 `error` 欄位，而不分析此陳述。如果您超出任一限制，舊版的服務會傳回回應碼 400。如果輸入的所有陳述都超過 500 個字元，則服務仍會針對要求傳回回應碼 400。

-   服務現在會對它從單一使用者接受的要求數進行節流控制。如果服務每分鐘從個別 {{site.data.keyword.cloud_notm}} 使用者名稱收到超過 600 個要求，則服務會傳回 HTTP 回應碼 429 *要求太多*。

-   下列變更同時適用於一般用途端點及客戶參與端點：

    -   以 `version` 參數指定的介面版本是 `2017-09-21`，才能使用最新版本的服務。
    -   已更新文件來指出服務可以使用各種語言產生本地化輸出。請使用 `Accept-Language` 要求標頭來指定語言。

### 2017 年 7 月 6 日
{: #July2017b}

**服務版本** - `3.3.6`<br/> **介面版本** - `2016-05-19`

服務已針對客戶參與端點的小型問題報告修正程式進行更新。

### 2017 年 7 月 1 日
{: #July2017a}

**服務版本** - `3.3.5`<br/> **介面版本** - `2016-05-19`

{{site.data.keyword.toneanalyzershort}} 服務的客戶參與端點現在已正式發行 (GA)。端點的所有呼叫目前都是以與一般用途端點呼叫相同的費率收費。

### 2017 年 5 月 8 日
{: #May2017}

**服務版本** - `3.3.4`<br/> **介面版本** - `2016-05-19`

IBM 已透過進一步擴充訓練資料集來更新情緒語氣及客戶關懷參與語氣的評分模型。現在，模型對基準性能測試資料集具有更高的精準度。

### 2017 年 4 月 17 日
{: #April2017}

-   現在提供一組客戶參與領域特有的語氣：*frustrated*、*satisfied*、*excited*、*polite*、*impolite*、*sad* 及 *sympathetic*。服務會從客戶與客服人員之間的交談文字中偵測這些語氣。語氣目前是測試版功能。
-   IBM 已發行情緒語氣評分模型的更新，以改善情緒結果。

### 2017 年 3 月 15 日
{: #March2017}

IBM 已更新情緒語氣評分模式。訓練資料集已擴充。因此，現在模型對基準性能測試資料集具有更高的精準度。

### 2016 年 12 月 1 日
{: #December2016}

IBM 已更新文件情緒語氣評分。新模型會考量句子的情緒側寫來彙總文件評分。

### 2016 年 10 月 18 日
{: #October2016b}

IBM 已加強社交語氣。服務現在使用一個稱為 [GloVe ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://nlp.stanford.edu/projects/glove/){: new_window} 的開放程式碼單字內嵌技術，來推斷社交語氣評分。此變更可讓服務在計算社交語氣時涵蓋更大量的單字詞彙。如需如何推斷社交語氣的相關資訊，請參閱 {{site.data.keyword.personalityinsightsshort}} 服務的[服務背後的科學](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html)。

### 2016 年 10 月 3 日
{: #October2016a}

IBM 已加強型句子層次的情緒偵測。服務會使用新的訓練資料、新的特性選擇處理程序，以及單字、表情符號及俚語的擴增辭彙。這些變更會在句子層次產生不同但顯著改善的情緒評分。服務的 API 尚未變更。

### 2016 年 5 月 19 日
{: #May2016}

{{site.data.keyword.toneanalyzershort}} 服務的正式發行 (GA) 版本包含下列新增特性：

-   服務的模型使用改良的上下文敏感度來解譯語氣。模型目前使用的項目不只是詞彙記號。現在，它們會考量標點符號、表情符號、語言參數（例如句子結構）及句子複雜性這類特性。
-   撰寫語氣模型已重新命名為語言語氣。
-   語言和情緒語氣模型現在會處理否定。
-   對於少於三個單字的句子，服務不再傳回回應。
-   服務現在有一個簡化及改良的[示範 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://tone-analyzer-demo.ng.bluemix.net){: new_window}。
