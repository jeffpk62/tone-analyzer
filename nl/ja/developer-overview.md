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

# 開発者向けの概要
{: #overviewDevelopers}

HTTP Representational State Transfer (REST) API を使用して、{{site.data.keyword.toneanalyzershort}} サービスの機能を利用することができます。さまざまな言語や環境でアプリケーションを簡単に開発できるように、いくつかのソフトウェア開発キット (SDK) も提供されています。
以下のセクションでは、このサービスを使用するアプリケーションの開発の概要を説明します。
{: shortdesc}

## サービスを使用するプログラミング
{: #programming}

1 人のテキストのトーンを分析するには、`GET` または `POST /v3/tone` メソッドを使用して入力テキストをサービスに渡します。会話の中のやり取りを分析するには、`POST /v3/tone_chat` メソッドを使用して入力をサービスに渡します。どちらの場合も、サービスは分析結果を JSON 形式で返します。

詳しくは、[汎用エンドポイントの使用](/docs/services/tone-analyzer/using-tone.html)と[カスタマー・エンゲージメント・エンドポイントの使用](/docs/services/tone-analyzer/using-tone-chat.html)を参照してください。

## ソフトウェア開発キットの使用
{: #sdks}

{{site.data.keyword.toneanalyzershort}} サービスは、アプリケーションの開発を簡単にするために、いくつかの SDK に対応しています。それらの SDK は、Node.js、Java、Python、Apple&reg; iOS など、多数の一般的なプログラミング言語やプラットフォームで使用可能です。すべての SDK のリストとその使用方法については、[{{site.data.keyword.watson}} SDK](/docs/services/watson/getting-started-sdks.html) を参照してください。どの SDK も、GitHub の [watson-developer-cloud 名前空間 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud){: new_window} から入手可能です。

モバイルの開発については、[{{site.data.keyword.watson}} Developer Cloud Swift SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/swift-sdk){: new_window} を参照してください。すべての SDK が、サービス資格情報を使用する認証にも、認証トークンを使用する認証にも対応しています。

## アプリケーション開発の詳細
{: #learn}

{{site.data.keyword.toneanalyzershort}} サービスは、*直接対話*と*プロキシー中継*という 2 つの典型的なプログラミング・モデルをサポートします。直接対話では、クライアントがサービスと直接通信するのに対し、プロキシー中継では、{{site.data.keyword.Bluemix_short}} 内に存在するプロキシー・アプリケーションを経由してクライアントとサービスがすべてのデータ (要求と結果) を交換します。


{{site.data.keyword.watson}} Developer Cloud サービスと {{site.data.keyword.Bluemix_notm}} を使用する方法について詳しくは、以下を参照してください。

-   {{site.data.keyword.watson}} サービスと {{site.data.keyword.Bluemix_notm}} の使用を始める方法については、[{{site.data.keyword.watson}} と {{site.data.keyword.Bluemix_notm}} の始め方](/docs/services/watson/index.html)を参照してください。
-   {{site.data.keyword.Bluemix_notm}} で {{site.data.keyword.watson}} サービス・アプリケーションの開発を始めるための、言語に依らない方法については、[{{site.data.keyword.Bluemix_notm}} 開発方法](/docs/services/watson/getting-started-bluemix.html)を参照してください。
-   {{site.data.keyword.watson}} アプリケーションを開発するために使用可能な 2 つのプログラミング・モデルについて詳しくは、[{{site.data.keyword.watson}} サービスのプログラミング・モデル](/docs/services/watson/getting-started-develop.html)を参照してください。
    -   プロキシー中継を使用する場合、クライアントは、{{site.data.keyword.Bluemix_notm}} 内に存在するプロキシー・サーバーに依存してサービスとの通信を行います。すべての要求をプロキシー・アプリケーションを経由して渡します。プロキシーを経由して要求を中継する場合、サービスでの認証には、サービス資格情報だけが使用されます。[{{site.data.keyword.watson}} サービスのためのサービス資格情報](/docs/services/watson/getting-started-credentials.html)を参照してください。
    -   直接対話を使用する場合は、クライアントは、サービスの認証トークンを取得するときに限り、{{site.data.keyword.Bluemix_notm}} 内のプロキシー・アプリケーションを使用し、トークンを取得した後はサービスと直接通信します。直接対話では、サービス資格情報はトークン取得のためにのみ使用します。[認証のためのトークン](/docs/services/watson/getting-started-tokens.html)を参照してください。
-   すべての {{site.data.keyword.watson}} サービスについて実行されるデフォルトの要求ロギングを制御する方法については、[{{site.data.keyword.watson}} サービスの要求ロギングの制御](/docs/services/watson/getting-started-logging.html)を参照してください。
