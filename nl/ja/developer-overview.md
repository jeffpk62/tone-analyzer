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

# 開発者向けの概要
{: #overviewDevelopers}

HTTP Representational State Transfer (REST) API を使用して、{{site.data.keyword.toneanalyzershort}} サービスの機能を利用することができます。 さまざまな言語でアプリケーションを簡単に開発できるように、いくつかのソフトウェア開発キット (SDK) も提供されています。 以下のセクションでは、このサービスを使用するアプリケーションの開発の概要を説明します。
{: shortdesc}

## サービスを使用するプログラミング
{: #programming}

1 人のテキストのトーンを分析するには、`GET` または `POST /v3/tone` メソッドを使用して入力テキストをサービスに渡します。 会話の中のやり取りを分析するには、`POST /v3/tone_chat` メソッドを使用して入力をサービスに渡します。 どちらの場合も、サービスは分析結果を JSON 形式で返します。 詳しくは、以下を参照してください。

-   [汎用エンドポイントの使用](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [カスタマー・エンゲージメント・エンドポイントの使用](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## ソフトウェア開発キットの使用
{: #sdks}

アプリケーション開発を簡素化するために、{{site.data.keyword.toneanalyzershort}} サービスの SDK を使用できます。多くの一般的なプログラミング言語およびプラットフォーム用の {{site.data.keyword.ibmwatson}} SDK があります。

-   すべての SDK のリストと GitHub 上の SDK へのリンクについては、[SDK の使用](/docs/services/watson?topic=watson-using-sdks)を参照してください。
-   {{site.data.keyword.toneanalyzershort}} サービスの Node 、Java、Python、Ruby、および Go SDK のすべてのメソッドについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/tone-analyzer){: new_window} を参照してください。

## アプリケーション開発の詳細
{: #learn}

{{site.data.keyword.watson}} サービスと {{site.data.keyword.cloud}} を使用する方法について詳しくは、以下のページを参照してください。

-   {{site.data.keyword.watson}} サービスと {{site.data.keyword.cloud_notm}} の使用を始める方法については、[{{site.data.keyword.watson}} と {{site.data.keyword.cloud_notm}} の始め方](/docs/services/watson?topic=watson-about)を参照してください。
-   すべての新しいサービス・インスタンスは、認証に {{site.data.keyword.cloud_notm}} ID およびアクセス管理 (IAM) を使用します。古いサービス・インスタンスでは、既存の Cloud Foundry サービスの資格情報の `{username}` と `{password}` を認証に使い続けることができる場合があります。サービスの認証について詳しくは、リリース・ノートの「[2018 年 10 月 30 日のサービスの更新](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018)」を参照してください。
-   {{site.data.keyword.toneanalyzershort}} サービスの要求ロギングは使用不可になっています。このサービスは、`X-Watson-Learning-Opt-Out` 要求ヘッダーが設定されているかどうかに関係なく、要求と応答からのデータをログに記録することも、保存することもありません。
