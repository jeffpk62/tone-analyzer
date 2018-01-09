---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-09"

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

# 開發人員概觀
{: #overviewDevelopers}

您可以透過 HTTP「具象狀態傳輸 (REST)」API，來存取 {{site.data.keyword.toneanalyzershort}} 服務的功能。也可以使用數個軟體開發套件 (SDK) 來簡化各種語言和環境的應用程式開發。下列各節提供了使用服務開發應用程式的概觀。
{: shortdesc}

## 使用服務進行程式設計
{: #programming}

為了分析一個人的文字語氣，您會透過 `GET` 或 `POST /v3/to` 方法，將輸入文字傳遞至服務。若要分析交談中的交流，您可以透過 `POST /v3/tone_chat` 方法，將輸入傳遞給服務。在這兩種情況下，服務都會以 JSON 格式傳回其分析。

如需相關資訊，請參閱[使用一般用途端點](/docs/services/tone-analyzer/using-tone.html)和[使用客戶參與端點](/docs/services/tone-analyzer/using-tone-chat.html)。

## 使用軟體開發套件
{: #sdks}

{{site.data.keyword.toneanalyzershort}} 服務支援許多 SDK 來進行簡化的應用程式開發。SDK 適用於許多熱門的程式設計語言和平台，包括 Node.js、Java、Python 和 Apple&reg; iOS。如需 SDK 的完整清單及使用它們的相關資訊，請參閱 [{{site.data.keyword.watson}} SDK](/docs/services/watson/getting-started-sdks.html)。在 GitHub 上，可以從 [watson-developer-cloud 名稱空間 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud){: new_window} 取得所有 SDK。

針對行動式開發，請參閱 [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}。所有 SDK 都支援使用您的服務認證或鑑別記號來進行鑑別。

## 進一步瞭解應用程式開發
{: #learn}

{{site.data.keyword.toneanalyzershort}} 服務支援兩個典型的程式設計模型：*直接互動*，在該模型中，用戶端直接與服務通訊；*透過 Proxy 進行通訊*，在此期間，用戶端與服務會透過位於 {{site.data.keyword.Bluemix_short}} 的 Proxy 應用程式來交換所有資料（要求和結果）。

如需使用 {{site.data.keyword.watson}} Developer Cloud 服務及 {{site.data.keyword.Bluemix_notm}} 的相關資訊，請參閱下列項目：

-   如需使用 {{site.data.keyword.watson}} 服務及 {{site.data.keyword.Bluemix_notm}} 的簡介，請參閱[開始使用 {{site.data.keyword.watson}} 及 {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html)。
-   如需在 {{site.data.keyword.Bluemix_notm}} 中開發 {{site.data.keyword.watson}} 服務應用程式且與語言無關的簡介，請參閱 [{{site.data.keyword.Bluemix_notm}} 開發方法](/docs/services/watson/getting-started-bluemix.html)。
-   如需可用來開發 {{site.data.keyword.watson}} 應用程式之兩種程式設計模型的相關資訊，請參閱 [{{site.data.keyword.watson}} 服務的程式設計模型](/docs/services/watson/getting-started-develop.html)：
    -   透過 Proxy 轉遞時，用戶端會依賴位於 {{site.data.keyword.Bluemix_notm}} 中的 Proxy 伺服器，來與服務通訊；它會通過 Proxy 應用程式來傳遞所有要求。透過 Proxy 轉遞要求只依賴服務認證來向服務進行鑑別；請參閱 [{{site.data.keyword.watson}} 服務的服務認證](/docs/services/watson/getting-started-credentials.html)。
    -   透過直接互動，用戶端在 {{site.data.keyword.Bluemix_notm}} 中只會使用 Proxy 應用程式時來取得服務的鑑別記號，之後它會直接與服務進行通訊。直接互動只會使用服務認證來取得記號；請參閱[鑑別用的記號](/docs/services/watson/getting-started-tokens.html)。
-   如需控制針對所有 {{site.data.keyword.watson}} 服務執行之預設要求記載的相關資訊，請參閱[控制 {{site.data.keyword.watson}} 服務的要求記載](/docs/services/watson/getting-started-logging.html)。
