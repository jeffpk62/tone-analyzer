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

# 入門チュートリアル

{{site.data.keyword.toneanalyzershort}} サービスは、入力コンテンツのトーンを分析します。このチュートリアルでは、さまざまなサンプル・コンテンツを分析するためのコマンドを示します。複数の例を使用して、汎用エンドポイントとカスタマー・エンゲージメント・エンドポイントの両方について説明します。
{: shortdesc}

## 始めに
{: #prerequisites}

- サービスのインスタンスを作成します。
    - {: download} これが表示されたら、サービス・インスタンスは作成されています。次に資格情報を取得します。
    - サービスからプロジェクトを作成します。
        1.  {{site.data.keyword.watson}} Developer Console の[サービス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/developer/watson/services){: new_window} のページに移動します。
        1.  {{site.data.keyword.toneanalyzershort}} を選択し、**「サービスの追加」**をクリックして、無料の {{site.data.keyword.Bluemix_notm}} アカウントを申請するか、またはログインします。
        1.  プロジェクト名として `tone-tutorial` と入力し、**「プロジェクトの作成 (Create Project)」**をクリックします。
- サービス・インスタンスに認証されるための資格情報をコピーします。
    - {: download} (表示されている) サービス・ダッシュボードから次を行います。
        1.  **「サービス資格情報」**タブをクリックします。
        1.  **「アクション」**の下にある**「資格情報の表示」**をクリックします。
        1.  `username`、`password`、`url` の値をコピーします。
        {: download}
    - Developer Console の **tone-tutorial** プロジェクトから、`"tone_analyzer"` のための `username`、`password`、`url` の値を **「資格情報」**セクションからコピーします。
- cURL があることを確認します。
    - 例では、cURL を使用して HTTP インターフェースのメソッドを呼び出します。オペレーティング・システムに適したバージョンを [curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} からインストールしてください。Secure Sockets Layer (SSL) プロトコルをサポートするバージョンをインストールします。必ず、インストールしたバイナリー・ファイルを `PATH` 環境変数に含めてください。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}} を使用する場合、カタログの [{{site.data.keyword.toneanalyzershort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} ページからサービス・インスタンスを作成します。サービス資格情報を見つける方法について詳しくは、[Watson サービスのサービス資格情報![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window} を参照してください。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 手順 1: POST 要求メソッドで汎用エンドポイントを使用する
{: #generalPurposePost}

以下のコマンドは、`POST /v3/tone` メソッドを呼び出してファイル `tone.json` のコンテンツを分析します。このファイルには、ある人が記述したプレーン・テキストの段落が 1 つ含まれています。例では、このメソッドの `sentences` 照会パラメーターについて説明します。

1.  サンプル・ファイル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> をダウンロードします。
1.  以下のコマンドを発行して、コンテンツ全体のトーンとセンテンスごとのトーンを分析します。
    -   `{username}` と `{password}` を前の手順で取得したサービス資格情報に置き換えます。
    -   `{path_to_file}` を、`tone.json` ファイルの場所を指すように変更します。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  `sentences` パラメーターを `false` に設定して以下のコマンドを発行することで、コンテンツ全体のトーンのみを分析します。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

メソッドの出力例については、[応答の例](/docs/services/tone-analyzer/using-tone.html#exampleResponse)を参照してください。

## 手順 2: GET 要求メソッドで汎用エンドポイントを使用する
{: #generalPurposeGet}

インターフェースには、`GET /v3/tone` メソッドも用意されています。`GET` メソッドの機能は `POST` メソッドと同じで、生成される結果も同じです。ただし、GET メソッドでは、分析するコンテンツを `text` 照会パラメーターを使用して指定します。GET メソッドはプレーン・テキストの入力のみを受け入れます。

1.  以下の例では、`text` パラメーターでファイル `tone.json` のテキストを指定しています。この例が示すように、テキストを URL にエンコードする必要があります。このコマンドでは `sentences` パラメーターを省略しているので、最初に説明した `POST` の例と同じ出力が返されます (この例では読みやすいように改行していますが、実際のコマンドでは改行を入れないでください)。

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## 手順 3: カスタマー・エンゲージメント・エンドポイントを使用する
{: #customerEngagement}

以下のコマンドは、`POST /v3/tone_chat` メソッドを呼び出してファイル `tone-chat.json` のコンテンツを分析します。このファイルには、<code>customer</code> と <code>agent</code> という 2 人の間で行われた短いメッセージのやり取りが含まれています。

1.  サンプル・ファイル <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> をダウンロードします。
1.  以下のコマンドを発行して、サンプル・ファイルに含まれているやり取りのトーンを分析します。

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

サービスの応答は、入力の発話ごとに最も多く検出されたトーンを示します。この要求の応答の内容を確認するには、[応答の例](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse)を参照してください。

## 次の手順

-   `/v3/tone` メソッドについて詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer/using-tone.html)を参照してください。
-   `/v3/tone_chat` メソッドについて詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer/using-tone-chat.html) を参照してください。
-   サービスのインターフェースのメソッドについて詳しくは、[API リファレンス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window} を参照してください。
-   [API Explorer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window} の API と対話します。
