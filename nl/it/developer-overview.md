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

# Panoramica per gli sviluppatori
{: #overviewDevelopers}

Puoi accedere alle funzionalità del servizio {{site.data.keyword.toneanalyzershort}} tramite un'API REST (Representational State Transfer) HTTP. Sono disponibili molte SDK (Software Development Kit) per semplificare lo sviluppo dell'applicazione per varie lingue e ambienti. Le seguenti sezioni forniscono una panoramica sullo sviluppo dell'applicazione con il servizio.
{: shortdesc}

## Programmazione con il servizio
{: #programming}

Per analizzare il tono di un testo di un individuo, passa il testo di input al servizio tramite il metodo `GET` o `POST /v3/tone`. Per analizzare gli scambi in una conversazione, passa l'input al servizio tramite il metodo `POST /v3/tone_chat`. In entrambi i casi, il servizio restituisce la sua analisi nel formato JSON.

Per ulteriori informazioni, consulta [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer/using-tone.html) e [Utilizzo dell'endpoint di coinvolgimento cliente](/docs/services/tone-analyzer/using-tone-chat.html).

## Utilizzo delle SDK (Software Development Kit)
{: #sdks}

Il servizio {{site.data.keyword.toneanalyzershort}} supporta alcune SDK per lo sviluppo dell'applicazione semplificato. Le SDK sono disponibili per molti linguaggi di programmazione, inclusi Node.js, Java, Python e Apple&reg; iOS. Per un elenco completo di SDK e di informazioni su come utilizzarle, consulta [SDK {{site.data.keyword.watson}}](/docs/services/watson/getting-started-sdks.html). Tutte le SDK sono disponibili da [watson-developer-cloud namespace ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud){: new_window} in GitHub.

Per lo sviluppo mobile, consulta [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}. Tutte le SDK supportano l'autenticazione utilizzando le credenziali del servizio o un token di autenticazione.

## Ulteriori informazioni sullo sviluppo dell'applicazione
{: #learn}

Il servizio {{site.data.keyword.toneanalyzershort}} supporta due modelli di programmazione tipici: *Interazione diretta*, in cui il client comunica direttamente con il servizio; e *inoltro tramite un proxy*, in cui il client e il servizio si scambiano tutti i dati (richieste e risultati) tramite un'applicazione proxy che risiede in {{site.data.keyword.Bluemix_short}}.

Per ulteriori informazioni sull'utilizzo dei servizi {{site.data.keyword.watson}} Developer Cloud e {{site.data.keyword.Bluemix_notm}}, consulta quanto segue:

-   Per un'introduzione all'utilizzo dei servizi {{site.data.keyword.watson}} e {{site.data.keyword.Bluemix_notm}}, consulta [Introduzione a {{site.data.keyword.watson}} e {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   Per un'introduzione indipendente dal linguaggio per lo sviluppo delle applicazioni dei servizi {{site.data.keyword.watson}} in {{site.data.keyword.Bluemix_notm}}, consulta [Strategie di sviluppo {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/getting-started-bluemix.html).
-   Per informazioni sui due modelli di programmazione disponibili per lo sviluppo delle applicazioni {{site.data.keyword.watson}}, consulta [Modelli di programmazione per i servizi {{site.data.keyword.watson}}](/docs/services/watson/getting-started-develop.html):
    -   Con l'inoltro tramite un proxy, il client si basa su un server proxy che risiede in {{site.data.keyword.Bluemix_notm}} per comunicare con il servizio; passa tutte le richieste tramite l'applicazione proxy. L'inoltro delle richieste tramite un proxy si basa solo sulle credenziali del servizio per l'autenticazione con il servizio; consulta [Credenziali del servizio per i servizi {{site.data.keyword.watson}}](/docs/services/watson/getting-started-credentials.html).
    -   Con l'interazione diretta, il client utilizza l'applicazione proxy in {{site.data.keyword.Bluemix_notm}} solo per ottenere un token di autenticazione per il servizio, dopodiché comunica direttamente con il servizio. L'interazione diretta utilizza le credenziali del servizio solo per ottenere un token; consulta [Token per l'autenticazione](/docs/services/watson/getting-started-tokens.html).
-   Per informazioni sul controllo della registrazione della richiesta predefinita eseguita per tutti i servizi {{site.data.keyword.watson}}, consulta [Controllo della registrazione della richiesta per i servizi {{site.data.keyword.watson}}](/docs/services/watson/getting-started-logging.html).
