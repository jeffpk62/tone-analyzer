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

# Visão geral para desenvolvedores
{: #overviewDevelopers}

É possível acessar os recursos do serviço do {{site.data.keyword.toneanalyzershort}} por meio de uma API de Representational State Transfer (REST) de HTTP. Diversos kit de desenvolvimento de software (SDKs) também estão disponíveis para simplificar o desenvolvimento de aplicativos em vários idiomas. As seções a seguir fornecem uma visão geral de desenvolvimento de aplicativos com o serviço.
{: shortdesc}

## Programando com o serviço
{: #programming}

Para analisar o tom do texto de um indivíduo, você passa o texto de entrada para o serviço por meio do método `GET` ou `POST /v3/tone`. Para analisar as trocas em uma conversa, você passa a entrada para o serviço por meio do método `POST /v3/tone_chat`. Em ambos os casos, o serviço retorna sua análise no formato JSON. Para obter mais informações, veja

-   [Usando o terminal de uso geral](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Usando kits de desenvolvimento de software
{: #sdks}

Os SDKs estão disponíveis para o serviço {{site.data.keyword.toneanalyzershort}} para simplificar o desenvolvimento de aplicativos. Os SDKs do {{site.data.keyword.ibmwatson}} estão disponíveis para muitas linguagens de programação e plataformas populares.

-   Para obter uma lista completa de SDKs e links para os SDKs no GitHub, veja [Usando SDKs](/docs/services/watson?topic=watson-using-sdks).
-   Para obter informações detalhadas sobre todos os métodos dos SDKs do Node, do Java, do Python, do Ruby
e do Go para o serviço {{site.data.keyword.toneanalyzershort}}, veja a [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

## Aprendendo mais sobre o desenvolvimento de aplicativo
{: #learn}

Para obter mais informações sobre como trabalhar com os serviços {{site.data.keyword.watson}} e {{site.data.keyword.cloud}}, veja as páginas a seguir:

-   Para obter uma introdução ao trabalho com serviços do {{site.data.keyword.watson}} e o {{site.data.keyword.cloud_notm}}, consulte [Introdução ao {{site.data.keyword.watson}} e ao {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about).
-   Todas as novas instâncias de serviço usam o {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para autenticação. As instâncias de serviço mais antigas podem continuar a usar o `{username}` e a `{password}` de suas credenciais de serviço existentes do Cloud Foundry para autenticação. Para obter mais informações sobre a autenticação no serviço, veja a [Atualização de serviço
de 30 de outubro de 2018](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018) nas notas sobre a liberação.
-   A criação de log da solicitação está desativada para o serviço {{site.data.keyword.toneanalyzershort}}. O serviço não registra nem retém dados de solicitações
e respostas, independentemente de o cabeçalho da solicitação `X-Watson-Learning-Opt-Out` estar configurado.
