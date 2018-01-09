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

# Visão geral para desenvolvedores
{: #overviewDevelopers}

É possível acessar os recursos do serviço do {{site.data.keyword.toneanalyzershort}} por meio de uma API de Representational State Transfer (REST) de HTTP. Vários Kits de Desenvolvimento de Software (SDKs) também estão disponíveis para simplificar o desenvolvimento de aplicativos em várias linguagens e ambientes. As seções a seguir fornecem uma visão geral de desenvolvimento de aplicativos com o serviço.
{: shortdesc}

## Programando com o serviço
{: #programming}

Para analisar o tom do texto de um indivíduo, você passa o texto de entrada para o serviço por meio do método `GET` ou `POST /v3/tone`. Para analisar as trocas em uma conversa, você passa a entrada para o serviço por meio do método `POST /v3/tone_chat`. Em ambos os casos, o serviço retorna sua análise no formato JSON.

Para obter mais informações, consulte [Usando o terminal de propósito geral](/docs/services/tone-analyzer/using-tone.html) e [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer/using-tone-chat.html).

## Usando Kits de Desenvolvimento de Software
{: #sdks}

O serviço do {{site.data.keyword.toneanalyzershort}} suporta vários SDKs para desenvolvimento de aplicativo simplificado. Os SDKs estão disponíveis para muitas linguagens de programação e plataformas populares, incluindo Node.js, Java, Python e Apple&reg; iOS. Para obter uma lista completa de SDKs e informações sobre como usá-los, consulte [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html). Todos os SDKs estão disponíveis no [watson-developer-cloud namespace ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud){: new_window} no GitHub.

Para desenvolvimento para dispositivo móvel, consulte o [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}. Todos os SDKs suportam a autenticação usando suas credenciais de serviço ou um token de autenticação.

## Aprendendo mais sobre o desenvolvimento de aplicativos
{: #learn}

O serviço do {{site.data.keyword.toneanalyzershort}} suporta dois modelos de programação típicos: *interação direta*, em que o cliente se comunica com o serviço diretamente; e *retransmissão por meio de um proxy*, em que o cliente e o serviço trocam todos os dados (solicitações e resultados) por meio de um aplicativo proxy que reside no {{site.data.keyword.Bluemix_short}}.

Para obter mais informações sobre como trabalhar com os serviços do {{site.data.keyword.watson}} Developer Cloud e com o {{site.data.keyword.Bluemix_notm}}, consulte o seguinte:

-   Para obter uma introdução sobre como trabalhar com os serviços do {{site.data.keyword.watson}} e o {{site.data.keyword.Bluemix_notm}}, consulte [Introdução ao {{site.data.keyword.watson}} e ao {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   Para obter uma introdução independente de linguagem para o desenvolvimento de serviços do {{site.data.keyword.watson}} no {{site.data.keyword.Bluemix_notm}}, consulte [Abordagens de desenvolvimento do {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/getting-started-bluemix.html).
-   Para obter informações sobre os dois modelos de programação disponíveis para desenvolver aplicativos do {{site.data.keyword.watson}}, consulte [Programando modelos para serviços do {{site.data.keyword.watson}}](/docs/services/watson/getting-started-develop.html):
    -   Com retransmissão por meio de um proxy, o cliente depende de um servidor proxy que reside no {{site.data.keyword.Bluemix_notm}} para se comunicar com o serviço; ele passa todas as solicitações por meio do aplicativo proxy. A retransmissão de solicitações por meio de um proxy depende apenas de credenciais de serviço para autenticação com o serviço; consulte [Credenciais de serviço para serviços do {{site.data.keyword.watson}}](/docs/services/watson/getting-started-credentials.html).
    -   Com a interação direta, o cliente usa o aplicativo proxy no {{site.data.keyword.Bluemix_notm}} apenas para obter um token de autenticação para o serviço, após o qual se comunicará diretamente com o serviço. A interação direta usa credenciais de serviço apenas para obter um token; consulte [Tokens para autenticação](/docs/services/watson/getting-started-tokens.html).
-   Para obter informações sobre como controlar a solicitação padrão de criação de log que é executada para todos os serviços do {{site.data.keyword.watson}}, consulte [Controlando solicitação de criação de log para serviços do {{site.data.keyword.watson}}](/docs/services/watson/getting-started-logging.html).
