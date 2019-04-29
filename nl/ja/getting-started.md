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

# 入門チュートリアル
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} サービスは、入力コンテンツのトーンを分析します。 このチュートリアルでは、さまざまなサンプル・コンテンツを分析するためのコマンドを示します。 例は、汎用エンドポイントとカスタマー・エンゲージメント・エンドポイントの両方を示しています。
{: shortdesc}

チュートリアルでは認証に {{site.data.keyword.cloud}} ID およびアクセス管理 (IAM) API 鍵を使用します。古いサービス・インスタンスでは、既存の Cloud Foundry サービスの資格情報の `{username}` と `{password}` を認証に使い続けることができる場合があります。お使いのサービス・インスタンスに適した方法を用いて認証を行ってください。サービスの IAM 認証の使用について詳しくは、[リリース・ノート](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)を参照してください。
{: important}

## 始めに
{: #prerequisites}

- {: hide-dashboard}  サービスのインスタンスを作成します。
    1.  {: hide-dashboard} {{site.data.keyword.cloud_notm}} カタログの [{{site.data.keyword.toneanalyzershort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} ページに移動します。
    1.  {: hide-dashboard} 無料の {{site.data.keyword.cloud_notm}} アカウントを登録するか、ログインします。
    1.  {: hide-dashboard} **「作成」**をクリックします。
-   サービス・インスタンスに認証されるための資格情報をコピーします。
    1.  {: hide-dashboard}  [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/dashboard/apps){: new_window} から、{{site.data.keyword.toneanalyzershort}} サービス・インスタンスをクリックして {{site.data.keyword.toneanalyzershort}} サービス・ダッシュボード・ページに移動します。
    1.  **「管理」**ページで、 **「表示」**をクリックして資格情報を表示します。
    1.  `「API キー」`の値と`「URL」`の値をコピーします。
-   `curl` コマンドを使用できることを確認します。
    -   例では `curl` コマンドを使用して HTTP インターフェースのメソッドを呼び出しています。オペレーティング・システムに適したバージョンを [curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} からインストールしてください。 Secure Sockets Layer (SSL) プロトコルをサポートするバージョンをインストールします。 必ず、インストールしたバイナリー・ファイルを `PATH` 環境変数に含めてください。

コマンドを入力するときには、`{apikey}` と `{url}` を、実際の API 鍵および URL に置き換えてください。変数値を表す中括弧はコマンドから削除してください。実際の値を入れると次の例のようになります。
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## 手順 1: POST 要求メソッドで汎用エンドポイントを使用する
{: #generalPurposePost}

以下のコマンドは、`POST /v3/tone` メソッドを呼び出してファイル `tone.json` のコンテンツを分析します。 このファイルには、ある人が記述したプレーン・テキストの段落が 1 つ含まれています。 例では、このメソッドの `sentences` 照会パラメーターについて説明します。

1.  サンプル・ファイル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> をダウンロードします。
1.  以下のコマンドを発行して、コンテンツ全体のトーンとセンテンスごとのトーンを分析します。
    -   {: hide-dashboard} `{apikey}` および `{url}` は、ご使用の情報に置き換えてください。
    -   `{path_to_file}` を、`tone.json` ファイルの場所を指すように変更します。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  `sentences` パラメーターを `false` に設定して以下のコマンドを発行することで、コンテンツ全体のトーンのみを分析します。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

メソッドの出力例については、[応答の例](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone)を参照してください。

## 手順 2: GET 要求メソッドで汎用エンドポイントを使用する
{: #generalPurposeGet}

インターフェースには、`GET /v3/tone` メソッドも用意されています。 `GET` メソッドの機能は `POST` メソッドと同じで、生成される結果も同じです。ただし、GET メソッドでは、分析するコンテンツを `text` 照会パラメーターを使用して指定します。 GET メソッドはプレーン・テキストの入力のみを受け入れます。

1.  以下の例では、`text` パラメーターでファイル `tone.json` のテキストを指定しています。この例が示すように、テキストを URL にエンコードする必要があります。 このコマンドでは `sentences` パラメーターを省略しているので、最初に説明した `POST` の例と同じ出力が返されます (この例では読みやすいように改行していますが、実際のコマンドでは改行を入れないでください)。

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## 手順 3: カスタマー・エンゲージメント・エンドポイントを使用する
{: #customerEngagement}

以下のコマンドは、`POST /v3/tone_chat` メソッドを呼び出してファイル `tone-chat.json` のコンテンツを分析します。 このファイルには、<code>customer</code> と <code>agent</code> という 2 人の間で行われた短いメッセージのやり取りが含まれています。

1.  サンプル・ファイル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン"></a> をダウンロードします。
1.  以下のコマンドを発行して、サンプル・ファイルに含まれているやり取りのトーンを分析します。

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

サービスの応答は、入力の発話ごとに最も多く検出されたトーンを示します。 この要求の応答の内容を確認するには、[応答の例](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat)を参照してください。

## 次の手順
{: #gsns}

-   `/v3/tone` メソッドについて詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)を参照してください。
-   `/v3/tone_chat` メソッドについて詳しくは、[カスタマー・エンゲージメント・エンドポイントの使用](/docs/services/tone-analyzer?topic=tone-analyzer-utco)を参照してください。
-   サービスのインターフェースのメソッドについて詳しくは、[API リファレンス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/tone-analyzer){: new_window} を参照してください。
