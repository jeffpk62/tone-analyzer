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

# Panoramica per gli sviluppatori
{: #overviewDevelopers}

Puoi accedere alle funzionalità del servizio {{site.data.keyword.toneanalyzershort}} tramite un'API REST (Representational State Transfer) HTTP. Sono disponibili molti SDK (Software Development Kit) per semplificare lo sviluppo delle applicazioni in diversi linguaggi. Le seguenti sezioni forniscono una panoramica sullo sviluppo di applicazioni con il servizio.
{: shortdesc}

## Programmazione con il servizio
{: #programming}

Per analizzare il tono di un testo di un individuo, passa il testo di input al servizio tramite il metodo `GET` o `POST /v3/tone`. Per analizzare gli scambi in una conversazione, passa l'input al servizio tramite il metodo `POST /v3/tone_chat`. In entrambi i casi, il servizio restituisce la sua analisi nel formato JSON. Per ulteriori informazioni, vedi

-   [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [Utilizzo dell'endpoint di coinvolgimento del cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Utilizzo delle SDK (Software Development Kit)
{: #sdks}

Gli SDK sono disponibili per il servizio {{site.data.keyword.toneanalyzershort}} per semplificare lo sviluppo di applicazioni. Gli SDK {{site.data.keyword.ibmwatson}} sono disponibili per molti linguaggi di programmazione e molte piattaforme di comune utilizzo.

-   Per un elenco completo degli SDK e i link agli SDK su GitHub, vedi [Utilizzo di SDK](/docs/services/watson?topic=watson-using-sdks).
-   Per informazioni dettagliate su tutti i metodi degli SDK Node, Java, Python, Ruby e Go per il servizio {{site.data.keyword.toneanalyzershort}}, vedi la [Guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

## Ulteriori informazioni sullo sviluppo dell'applicazione
{: #learn}

Per ulteriori informazioni sull'utilizzo dei servizi {{site.data.keyword.watson}} e {{site.data.keyword.cloud}}, vedi le seguenti pagine:

-   Per un'introduzione all'utilizzo dei servizi {{site.data.keyword.watson}} e {{site.data.keyword.cloud_notm}}, consulta [Introduzione a {{site.data.keyword.watson}} e {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about).
-   Tutte le nuove istanze di servizio utilizzano {{site.data.keyword.cloud_notm}} IAM (Identity and Access Management) per l'autenticazione. Le istanze del servizio meno recenti potrebbero continuare a utilizzare `{username}` e `{password}` dalle loro credenziali del servizio Cloud Foundry esistenti per l'autenticazione. Per ulteriori informazioni sull'autenticazione presso il servizio, vedi l'[aggiornamento del servizio del 30 ottobre 2018](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018) nelle note sulla release.
-   La registrazione della richiesta è disabilitata per il servizio {{site.data.keyword.toneanalyzershort}}. Il servizio non registra o conserva i dati da richieste e risposte, a prescindere dall'impostazione o meno dell'intestazione della richiesta `X-Watson-Learning-Opt-Out`.
