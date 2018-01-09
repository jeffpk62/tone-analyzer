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

# Sobre

> **Atualização de serviço:** *o serviço do {{site.data.keyword.toneanalyzershort}} foi atualizado em 25 e 28 de setembro de 2017. Para o terminal de propósito geral, tanto os parâmetros de solicitação quanto o conteúdo de resposta mudaram; além disso, o terminal não retorna mais os tons sociais ou o tom de desagrado e agora aceita entrada em francês. Limites de entrada e reguladores com mudança para ambos os terminais, assim como a versão da interface. O serviço agora também aceita entrada parcialmente correta em vez de retornar um erro para a solicitação geral. Para obter mais informações sobre essas e outras mudanças, consulte as [Notas sobre a liberação](/docs/services/tone-analyzer/release-notes.html).*

O serviço do {{site.data.keyword.toneanalyzerfull}} usa análise linguística para detectar tons emocionais e de linguagem no texto por escrito. O serviço pode analisar o tom tanto no nível do documento quanto no da sentença. É possível usar o serviço para entender como suas comunicações por escrito são percebidas e, em seguida, melhorar o tom de suas comunicações. Os negócios podem usar o serviço para aprender o tom das comunicações de seus clientes e responder a cada cliente de forma apropriada ou para entender e melhorar suas conversas com os clientes em geral.
{: shortdesc}

Você envia entrada em JSON, texto sem formatação ou HTML que contém seu conteúdo por escrito para o serviço. O serviço aceita até 128 KB de texto, que é cerca de 1000 sentenças. O serviço retorna resultados em JSON que relatam o tom de sua entrada. É possível usar esses resultados para melhorar a percepção e a eficácia de suas comunicações, assegurando que sua composição transmita o tom e o estilo desejados para seu público alvo. O diagrama a seguir mostra o fluxo básico de chamadas para o serviço.

![Envie conteúdo ao serviço do Tone Analyzer e use os resultados para melhorar suas comunicações.](images/tone-analyzer.png)

## Terminais do Tone Analyzer

O serviço oferece dois terminais:

-   **Terminal de propósito geral** (`GET` ou `POST /v3/tone`)

    Use o terminal de propósito geral do {{site.data.keyword.toneanalyzershort}} para analisar dados da web mais curtos, como mensagens de e-mail ou tweets, ou documentos mais longos, como artigos ou postagens de blog. Monitore mídia social para entender o que os clientes estão falando sobre uma marca e para determinar a quem direcionar mensagens específicas. O terminal aceita entrada em JSON, texto sem formatação ou HTML. Para obter mais informações sobre o método e os tons que ele retorna, consulte [Usando o terminal de propósito geral](/docs/services/tone-analyzer/using-tone.html).

    A [demo de propósito geral ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://tone-analyzer-demo.ng.bluemix.net/){: new_window} permite enviar conteúdo ao serviço para análise. O serviço retorna análise geral e no nível da sentença sobre o tom do conteúdo.
-   **Terminal de engajamento do cliente** (`POST /v3/tone_chat`)

    Use o terminal de engajamento do cliente do {{site.data.keyword.toneanalyzershort}} para monitorar as conversas de atendimento ao cliente e de suporte. Escale conversas com clientes quando elas derem errado ou encontre oportunidades para melhorar scripts de atendimento ao cliente, estratégias de diálogo e jornadas dos clientes. O terminal aceita entrada em JSON. Para obter mais informações sobre o método e os tons que ele retorna, consulte [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer/using-tone-chat.html).

    A [demo de engajamento do cliente ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://customer-engagement-analytics.mybluemix.net/){: new_window} analisa conversas entre clientes e agentes de atendimento ao cliente. O serviço mede a satisfação e as preocupações do cliente, avalia o desempenho do agente e permite medir como a interação evolui.

Para obter informações sobre os planos de precificação disponíveis para o serviço, consulte o [Catálogo do serviço do {{site.data.keyword.toneanalyzershort}} no {{site.data.keyword.Bluemix_short}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/catalog/services/tone-analyzer){: new_window}.

## Casos de uso

Seguem alguns casos de uso interessantes do serviço:

-   *Atendimento social e monitoramento de público:* monitore mídia social para entender o que os clientes estão falando sobre sua marca em tempo real. Por exemplo, você pode determinar que seus clientes em Chicago estão tristes após o Bulls ter perdido ou felizes durante o festival Taste of Chicago. (Terminal de propósito geral)
-   *Marketing personalizado:* determine a quem e quando direcionar mensagens personalizadas. Por exemplo, uma empresa de viagens pode se direcionar a consumidores felizes com mensagens do tipo "presenteie-se", a consumidores tristes com mensagens do tipo "fuja" e a consumidores bravos com mensagens do tipo "relaxe". (Terminal de propósito geral)
-   *Robôs de bate-papo:* permita que um agente automatizado detecte tons dos clientes e monte respostas adequadas. Por exemplo, você pode responder à tristeza com "Sinto muito que você esteja chateado com esse problema" ou à satisfação com "Estou feliz que esteja satisfeito com nosso serviço". (Terminal de engajamento do cliente)
-   *Monitoramento de engajamento do cliente e garantia de qualidade:* monitore o tom geral das comunicações entre agentes e clientes, detecte anomalias e destaque oportunidades para treinar agentes sobre como se comunicar melhor. (Terminal de engajamento do cliente)

Também é possível usar o serviço do {{site.data.keyword.toneanalyzershort}} com serviços adicionais do {{site.data.keyword.ibmwatson_notm}}, como o [{{site.data.keyword.conversationfull}}](https://console.bluemix.net/docs/services/conversation/index.html) ou o [{{site.data.keyword.speechtotextfull}}](https://console.bluemix.net/docs/services/speech-to-text/index.html), para analisar entrada do usuário. Por exemplo, o aplicativo [Conversation Food Coach ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://food-coach.mybluemix.net/){: new_window} usa o serviço do {{site.data.keyword.conversationshort}} para treinar usuários para que façam escolhas alimentares saudáveis com base em suas respostas sobre os alimentos que eles comem. Para obter mais informações, consulte esta [Postagem do blog do Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/watson/blog/2016/10/17/creating-a-compassionate-conversational-agent-using-watson-tone-analyzer-and-watson-conversation-services/){: new_window}.

> **Nota:** o serviço do {{site.data.keyword.toneanalyzershort}} calcula algoritmicamente o tom do texto por escrito. Ele não deduz as características de personalidade do autor do texto. Para obter um retrato da personalidade, consulte o [Serviço do {{site.data.keyword.personalityinsightsfull}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/personality-insights/index.html){: new_window}.

## Suporte ao idioma
{: #languages}

O método `/v3/tone` pode analisar o conteúdo em inglês (`en`) e em francês (`fr`); o método `/v3/tone_chat` suporta apenas o inglês. Ambos os métodos podem responder com conteúdo localizado em vários idiomas. Para obter mais informações, consulte [Usando o terminal de propósito geral](/docs/services/tone-analyzer/using-tone.html) e [Usando o terminal de engajamento do cliente](/docs/services/tone-analyzer/using-tone-chat.html).
