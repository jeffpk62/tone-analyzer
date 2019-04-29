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

# 開發人員概觀
{: #overviewDevelopers}

您可以透過 HTTP「具象狀態傳輸 (REST)」API，來存取 {{site.data.keyword.toneanalyzershort}} 服務的功能。也可以使用數個「軟體開發套件 (SDK)」來簡化各種語言的應用程式開發。下列各節提供了使用服務開發應用程式的概觀。
{: shortdesc}

## 使用服務進行程式設計
{: #programming}

為了分析一個人的文字語氣，您會透過 `GET` 或 `POST /v3/to` 方法，將輸入文字傳遞至服務。若要分析交談中的交流，您可以透過 `POST /v3/tone_chat` 方法，將輸入傳遞給服務。在這兩種情況下，服務都會以 JSON 格式傳回其分析。如需相關資訊，請參閱

-   [使用一般用途端點](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [使用客戶參與端點](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## 使用軟體開發套件
{: #sdks}

SDK 適用於 {{site.data.keyword.toneanalyzershort}} 服務，以簡化應用程式開發。{{site.data.keyword.ibmwatson}} SDK 適用於許多熱門的程式設計語言及平台。

-   如需完整的 SDK 清單以及 GitHub 上 SDK 的鏈結，請參閱[使用 SDK](/docs/services/watson?topic=watson-using-sdks)。
-   如需 {{site.data.keyword.toneanalyzershort}} 服務之所有 Node、Java、Python、Ruby 及 Go SDK 方法的詳細資訊，請參閱 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/tone-analyzer){: new_window}。

## 進一步瞭解應用程式開發
{: #learn}

如需使用 {{site.data.keyword.watson}} 服務及 {{site.data.keyword.cloud}} 的相關資訊，請參閱下列頁面：

-   如需使用 {{site.data.keyword.watson}} 服務及 {{site.data.keyword.cloud_notm}} 的簡介，請參閱[開始使用 {{site.data.keyword.watson}} 及 {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about)。
-   所有新的服務實例都會使用 {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) 來進行鑑別。舊的服務實例可能會繼續使用其現有 Cloud Foundry 服務認證中的 `{username}` 及 `{password}` 來進行鑑別。如需服務鑑別的相關資訊，請參閱版本注意事項中的 [2018 年 10 月 30 日服務更新](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018)。
-   已停用 {{site.data.keyword.toneanalyzershort}} 服務的要求記載。不論是否設定 `X-Watson-Learning-Opt-Out` 要求標頭，服務都不會記載或保留要求及回應中的資料。
