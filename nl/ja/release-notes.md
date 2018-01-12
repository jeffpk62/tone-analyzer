---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

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

# リリース・ノート

ここでは、{{site.data.keyword.toneanalyzershort}} サービスの各リリースで導入された新機能と変更点について説明します。既存のコードを壊す変更が行われたことはありません。
{: shortdesc}

> **注:** 更新ごとに*サービス・バージョン*と*インターフェース・バージョン*がリリース・ノートに記載されるようになりました。ある更新で提供された新機能と機能を使用するためには、`version` 照会パラメーターに*インターフェース・バージョン*を指定してください。サービスは、`X-Service-Api-Version` 応答ヘッダーを使用して両方のバージョンを返します。

## 2017 年 9 月 28 日
{: #September2017b}

**サービス・バージョン:** `3.4.1`<br/> **インターフェース・バージョン:** `2017-09-21`

-   1 人の {{site.data.keyword.Bluemix_notm}} ユーザー名で送信できる要求の最大数を絞る限度が、毎分 1200 個の要求に増えました。ユーザーがこの限度を超えると、サービスは、HTTP 応答コード 429 *「Too many requests (要求が多すぎます)」*を返します。

## 2017 年 9 月 25 日
{: #September2017a}

**サービス・バージョン:** `3.4.1`<br/> **インターフェース・バージョン:** `2017-09-21`

-   汎用エンドポイント (`/v3/tone` メソッド) が以下のように変更されました。

    -   英語に加えてフランス語 (`fr`) の入力コンテンツがサポートされます。
    -   社交性のトーンが返されなくなりました。
    -   感情のトーンで `disgust` が返されなくなりました。
    -   スコアが `0.5` 未満のトーンは省略されます。この条件は、`/v3/tone_chat` メソッドの応答と対応しています。
    - トーン・カテゴリー (`tone_categories` フィールド) が出力に含めて返されなくなりました。条件のしきい値を満たす値のすべてのトーンが、単一の `tones` オブジェクトに含められて返されます。これまでと同様に、デフォルトでは、常にドキュメント全体のトーンとセンテンスごとのトーンが返されます。
    - 指定したトーンに出力を制限する `tone` 照会パラメーターは受け入れられなくなりました。どの要求に対しても、該当するすべてのトーンが返されます。パラメーターを要求に含めてもエラーにはなりませんが、応答には影響しません。
    - 各センテンスの `input_from` フィールドと `input_to` フィールドは返されなくなりました。分析結果の他にメソッドから返されるのは、各センテンスの ID とテキストのみになりました。

-   以下の例のように入力が部分的に正しい場合に、サービスは、HTTP 応答コード 400 の代わりに 200 を返すようになりました。

    -   `/v3/tone` メソッドでは、128 KB を超える入力コンテンツ、またはセンテンス数が 1000 を超える入力コンテンツを送信した場合に、サービスは、`warning` フィールドを応答に含めて返すようになりました。サービスは、ドキュメント・レベルの分析として最初の 1000 個のセンテンスを分析し、現在と同様に、センテンス・レベルの分析として最初の 100 個のセンテンスのみを分析します。これより前のバージョンのサービスは、どちらの限度を超えた場合も、応答コード 400 を要求に返していました。また、3 ワード未満のセンテンスをサービスが分析するようになったことにも注意してください。
    -   `/v3/tone_chat` メソッドでは、50 個を超える発話を送信した場合に、サービスは、`utterances_tone` レベルの応答でコンテンツ全体に対して `warning` フィールドを返し、50 個の発話のみを分析します。送信された発話の 1 つが 500 文字を超える場合、サービスはその発話に対して `error` フィールドを返し、その発話を分析しません。これより前のバージョンのサービスは、どちらの限度を超えた場合も、応答コード 400 を返していました。入力した発話がすべて 500 文字を超えている場合は、サービスは、以前と同様に応答コード 400 を要求に対して返すことに注意してください。

-   サービスは、1 人のユーザーから受け入れる要求数を絞るようになりました。1 人の {{site.data.keyword.Bluemix_notm}} ユーザー名から受け取る要求の数が 600 個/分を超えると、サービスは、HTTP 応答コード 429 *「Too many requests (要求が多すぎます)」*を返します。

-   汎用エンドポイントとカスタマー・エンゲージメント・エンドポイントの両方に、以下の変更が適用されます。

    -   最新バージョンのサービスを使用する場合、`version` パラメーターで指定するインターフェース・バージョンは `2017-09-21` です。
    -   資料が更新され、さまざまな言語でローカライズされた出力をサービスで生成できるようになったことが記載されました。目的の言語を指定するには、`Accept-Language` 要求ヘッダーを使用します。

## 2017 年 7 月 6 日
{: #July2017b}

**サービス・バージョン:** `3.3.6`<br/> **インターフェース・バージョン:** `2016-05-19`

カスタマー・エンゲージメント・エンドポイントの軽度の欠陥を修正するための更新がサービスに行われました。

## さらに前のリリース

-   [2017 年 7 月 1 日](#July2017a)
-   [2017 年 5 月 8 日](#May2017)
-   [2017 年 4 月 17 日](#April2017)
-   [2017 年 3 月 15 日](#March2017)
-   [2016 年 12 月 1 日](#December2016)
-   [2016 年 10 月 18 日](#October2016b)
-   [2016 年 10 月 3 日](#October2016a)
-   [2016 年 5 月 19 日](#May2016)

### 2017 年 7 月 1 日
{: #July2017a}

**サービス・バージョン:** `3.3.5`<br/> **インターフェース・バージョン:** `2016-05-19`

{{site.data.keyword.toneanalyzershort}} サービスのカスタマー・エンゲージメント・エンドポイントが一般出荷 (GA) されました。このエンドポイントの呼び出しはすべて、汎用エンドポイントの呼び出しと同じ価格で課金されるようになりました。

### 2017 年 5 月 8 日
{: #May2017}

**サービス・バージョン:** `3.3.4`<br/> **インターフェース・バージョン:** `2016-05-19`

IBM は、トレーニング・データ・セットをさらに拡張し、感情のトーンとカスタマー・ケア・エンゲージメントのトーンのスコア・モデルを更新しました。 ベンチマーク・データ・セットでは、これらのモデルの精度が向上しました。

### 2017 年 4 月 17 日
{: #April2017}

-   カスタマー・エンゲージメントの分野に固有の新しいトーン (*不満* (frustrated)、*満足* (satisfied)、*興奮* (excited)、*礼儀正しさ* (polite)、*不作法* (impolite)、*悲しみ* (sad)、*共感* (sympathetic)) が一式導入されました。サービスは、顧客と担当員の間の会話のテキストから、これらのトーンを検出します。これらのトーンは現在、ベータ機能になっています。
-   IBM は、感情の結果を向上させる感情のトーン・スコア・モデルに対する更新をリリースしました。

### 2017 年 3 月 15 日
{: #March2017}

IBM は、感情のトーンのスコア・モデルを更新しました。トレーニング・データ・セットが拡張されました。その結果、ベンチマーク・データ・セットに対するモデルの精度が向上しました。

### 2016 年 12 月 1 日
{: #December2016}

IBM は、ドキュメントの感情のトーン・スコアを更新しました。新しいモデルは、センテンスの感情プロファイルを加味してドキュメントのスコアを集計します。

### 2016 年 10 月 18 日
{: #October2016b}

IBM は、社交性のトーンを拡張しました。サービスは、[GloVe ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://nlp.stanford.edu/projects/glove/){: new_window} と呼ばれるオープン・ソースの単語埋め込み技法を使用して、社交性のトーン・スコアを推測するようになりました。この変更により、サービスは、社交性のトーンを計算する際に、より広範な語彙をカバーできるようになりました。社交性のトーンの推測方法について詳しくは、{{site.data.keyword.personalityinsightsshort}} サービスの[サービスを支える科学](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html)を参照してください。

### 2016 年 10 月 3 日
{: #October2016a}

IBM は、センテンス・レベルの感情の検出を拡張しました。サービスで使用するトレーニング・データ・セット、機能選択プロセスを刷新し、単語、絵文字、スラングの辞書を強化しました。これらの変更により、センテンス・レベルの感情のスコアが変わりましたが、大幅に改善されました。サービスの API は変更されていません。

### 2016 年 5 月 19 日
{: #May2016}

一般出荷可能 (GA) リリースの {{site.data.keyword.toneanalyzershort}} サービスには、以下の新機能があります。

-   サービスのモデルでトーンを解釈するために使用するコンテキスト感度が向上しました。字句トークン以外のものがモデルで使用されるようになりました。句読点、顔文字、センテンスの構造などの言語パラメーター、センテンスの複雑さなどの追加の特性が考慮されるようになりました。
-   記述トーンというモデルの名前が言語トーンに変更されました。
-   言語トーンと感情トーンのモデルが否定の言葉に対応するようになりました。
-   3 語未満のセンテンスにはサービスは応答を返さなくなりました。
-   サービスの[デモ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://tone-analyzer-demo.mybluemix.net){: new_window} がシンプルに改善されました。