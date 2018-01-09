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

# 製品情報

> **サービスの更新:** *{{site.data.keyword.toneanalyzershort}} サービスは、2017 年 9 月 25 と 28 日に更新されました。汎用エンドポイントについては、要求パラメーターと応答コンテンツの両方が変更されています。さらに、このエンドポイントは社交性のトーンや嫌悪トーンを返さなくなり、フランス語入力を受け入れるようになりました。両方のエンドポイントについて、入力とスロットルの制限が変更され、インターフェース・バージョンも変更されました。また、サービスは、入力が部分的に正しい場合に、要求全体に対してエラーを返すのではなく、正しい入力部分を受け入れるようになりました。これらの変更やその他の変更について詳しくは、[リリース・ノート](/docs/services/tone-analyzer/release-notes.html)を参照してください。*

{{site.data.keyword.toneanalyzerfull}} サービスは、言語分析を使用して、記述されたテキストから感情トーンと言語トーンを検出します。このサービスは、ドキュメントとセンテンスの両方のレベルでトーンを分析できます。このサービスを使用して、コミュニケーションのために記述した内容がどのように受け取られるかを理解し、記述内容のトーンを改善することができます。企業はこのサービスを使用してお客様の記述内容のトーンを理解し、お客様に応じて適切に対応することができます。また、お客様との会話全般を理解して改善することができます。
{: shortdesc}

記述されたコンテンツを含む JSON、プレーン・テキスト、または HTML の入力をサービスに送信します。サービスは最大 128 KB のテキスト (約 1000 センテンス) を受け入れます。サービスは、入力のトーンを報告する JSON 結果を返します。それらの結果を使用して、コミュニケーションの受け取られ方と効果を改善し、意図するトーンとスタイルが対象者に伝わる記述にすることができます。以下の図は、サービスに対する基本的な呼び出しのフローを示しています。

![コンテンツを Tone Analyzer サービスに送信し、結果を使用してコミュニケーションを改善します。](images/tone-analyzer.png)

## Tone Analyzer のエンドポイント

サービスには、以下の 2 つのエンドポイントが用意されています。

-   **汎用エンドポイント** (`GET` または `POST /v3/tone`)

    {{site.data.keyword.toneanalyzershort}} 汎用エンドポイントは、E メール・メッセージやツイートなどの短い Web データ、また、記事やブログ投稿などの長いドキュメントを分析するために使用します。ソーシャル・メディアをモニターして、あるブランドについてのお客様達の発言を理解し、特定のメッセージを送るターゲットを決定できます。このエンドポイントは、JSON、プレーン・テキスト、または HTML の入力を取ります。メソッドと返されるトーンについて詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer/using-tone.html)を参照してください。

    [汎用のデモ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://tone-analyzer-demo.ng.bluemix.net/){: new_window} では、コンテンツを分析のためにサービスに送信します。サービスは、そのコンテンツについて全体的に分析したトーンとセンテンス・レベルで分析したトーンを返します。
-   **カスタマー・エンゲージメント・エンドポイント** (`POST /v3/tone_chat`)

    {{site.data.keyword.toneanalyzershort}} カスタマー・エンゲージメント・エンドポイントは、カスタマー・サービスとサポートの会話をモニターするために使用します。お客様の機嫌が悪くなったときにお客様との会話をエスカレーションしたり、カスタマー・サービス・スクリプト、ダイアログ戦略、カスタマー・ジャーニーを改善する機会を見つけたりします。このエンドポイントは JSON 入力を取ります。メソッドと返されるトーンについて詳しくは、[カスタマー・エンゲージメント・エンドポイントの使用](/docs/services/tone-analyzer/using-tone-chat.html)を参照してください。

    [カスタマー・エンゲージメントのデモ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://customer-engagement-analytics.mybluemix.net/){: new_window} では、お客様とカスタマー・サービス担当員の間の会話を分析します。サービスを使用して、お客様の満足度と不安を測定し、担当員の対応を評価し、対話の展開を正しく読み取れるようにします。

このサービスで提供されている価格プランについて詳しくは、[{{site.data.keyword.Bluemix_short}} カタログの {{site.data.keyword.toneanalyzershort}} サービス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.ng.bluemix.net/catalog/services/tone-analyzer){: new_window} を参照してください。

## ユース・ケース

このサービスの興味深いユース・ケースをいくつか紹介します。

-   *ソーシャル・リスニングとオーディエンス・モニタリング:* ソーシャル・メディアをモニターして、あるブランドについてのお客様達の発言をリアルタイムで知ることができます。例えば、シカゴのお客様が、Bulls が試合に負けた後は悲しみ、Taste of Chicago フェスティバルの期間中は喜んでいることがわかる可能性があります (汎用エンドポイント)。
-   *パーソナライズ・マーケティング:* パーソナライズ・メッセージングのターゲットにする人と時期を決定できます。例えば、旅行会社であれば、満足している消費者には「自分へのご褒美を贈りましょう」というメッセージ、悲しんでいる消費者には「気晴らしをしましょう」というメッセージ、怒っている消費者には「リラックスしましょう」というメッセージを送ることができます (汎用エンドポイント)。
-   *チャットボット:* 自動エージェントがお客様のトーンを検出して適切な応答を生成できるようにします。例えば、悲しみに対しては「この問題についてはご気分を害してしまい申し訳ありません」、満足に対しては「当社のサービスにご満足いただき、光栄です」と応答することができます (カスタマー・エンゲージメント・エンドポイント)。
-   *カスタマー・エンゲージメントのモニタリングと品質保証:* 担当員とお客様のコミュニケーションの全体的なトーンをモニターし、異常を検出し、より良くコミュニケーションする方法を担当員に示す好機を強調表示します (カスタマー・エンゲージメント・エンドポイント)。

また、{{site.data.keyword.toneanalyzershort}} サービスを追加の {{site.data.keyword.ibmwatson_notm}} サービス ([{{site.data.keyword.conversationfull}}](https://console.bluemix.net/docs/services/conversation/index.html) や [{{site.data.keyword.speechtotextfull}}](https://console.bluemix.net/docs/services/speech-to-text/index.html) など) と一緒に使用して、ユーザー入力を分析することもできます。例えば、[Conversation Food Coach ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://food-coach.mybluemix.net/){: new_window} アプリケーションは、{{site.data.keyword.conversationshort}} サービスを使用して、食事内容に関するユーザーの応答を基に健康的な食べ物を選ぶように指導できます。詳しくは、こちらの[Watson ブログ投稿 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/watson/blog/2016/10/17/creating-a-compassionate-conversational-agent-using-watson-tone-analyzer-and-watson-conversation-services/){: new_window} を参照してください。

> **注:** {{site.data.keyword.toneanalyzershort}} サービスは、記述されたテキストのトーンをアルゴリズムを使用して計算します。テキストの作成者のパーソナリティー特性は推測しません。パーソナリティーのポートレイトを取得する方法については、[{{site.data.keyword.personalityinsightsfull}} サービス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/docs/services/personality-insights/index.html){: new_window} を参照してください。

## 言語サポート
{: #languages}

`/v3/tone` メソッドは、英語 (`en`) とフランス語 (`fr`) のコンテンツを分析できます。`/v3/tone_chat` メソッドは英語のみをサポートします。どちらのメソッドも、さまざまな言語でローカライズされたコンテンツを使用して応答できます。詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer/using-tone.html)と[カスタマー・エンゲージメント・エンドポイントの使用](/docs/services/tone-analyzer/using-tone-chat.html)を参照してください。
