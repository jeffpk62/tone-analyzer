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

# Informazioni
{: #about}

> **Aggiornamento del servizio:** *il servizio {{site.data.keyword.toneanalyzershort}} è stato aggiornato tra il 25 e il 28 settembre 2017. Per l'endpoint di utilizzo generico, sono stati modificati i parametri della richiesta e il contenuto della risposta; in aggiunta, l'endpoint non restituisce più i toni sociali o il tono di disgusto e ora accetta l'input in francese. L'input e i limiti della strozzatura sono stati modificati per entrambi gli endpoint, come fatto nella versione dell'interfaccia. Il servizio inoltre ora accetta input parzialmente corretto invece di restituire un errore per la richiesta generale. Per ulteriori informazioni su queste ed altre modifiche, consulta le [Note sulla release](/docs/services/tone-analyzer/release-notes.html).*

Il servizio {{site.data.keyword.toneanalyzerfull}} utilizza l'analisi linguistica per individuare i toni linguistici ed emotivi nel testo scritto. Il servizio può analizzare il tono ai livelli della frase e del documento. Puoi utilizzare il servizio per capire come le tue comunicazioni scritte vengono percepite e quindi migliorare il tono delle tue comunicazioni. Le aziende possono utilizzare il servizio per avere informazioni sul tono delle comunicazioni dei loro clienti e per rispondere ad ogni cliente nel modo appropriato o per comprendere e migliorare le loro conversazioni con i clienti in generale.
{: shortdesc}

Invia input JSON, testo semplice o HTML che contiene il tuo contenuto scritto al servizio. Il servizio accetta fino a 128 KB di testo, che sono circa 1000 frasi. Il servizio restituisci i risultati JSON che riportano il tono del tuo input. Puoi utilizzare questi risultati per migliorare la percezione e l'efficacia delle tue comunicazioni, assicurandoti che la tua scrittura comunichi il tono e lo stile che desideri per i tuoi destinatari previsti. Il seguente diagramma mostra il flusso di base delle chiamate al servizio.

![Invia il contenuto al servizio Tone Analyzer e utilizza i risultati per migliorare le tue comunicazioni.](images/tone-analyzer.png)

## Endpoint Tone Analyzer

Il servizio offre due endpoint:

-   **Endpoint di utilizzo generico** (`GET` o `POST /v3/tone`)

    Utilizza l'endpoint di utilizzo generico {{site.data.keyword.toneanalyzershort}} per analizzare i dati web più brevi, come i messaggi email o i tweet o i documenti più lunghi, come un articolo o i post del blog. Monitora i social media per comprendere quali clienti stanno parlando del marchio e per determinare a chi destinare la messaggistica specifica. L'endpoint accetta input JSON, testo semplice o HTML. Per ulteriori informazioni sul metodo e sui toni che restituisce, consulta [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer/using-tone.html).

    La [general purpose demo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://tone-analyzer-demo.ng.bluemix.net/){: new_window} ti consente di inviare il contenuto al servizio per l'analisi. Il servizio restituisce le analisi al livello della frase del tono del contenuto.
-   **Endpoint di coinvolgimento cliente** (`POST /v3/tone_chat`)

    Utilizza l'endpoint di coinvolgimento cliente {{site.data.keyword.toneanalyzershort}} per monitorare le conversazioni del supporto e del servizio clienti. Inoltra le conversazioni del cliente quando peggiorano o trovi l'opportunità di migliorare gli script del servizio clienti, le strategie di dialogo e i percorsi del cliente. L'endpoint accetta l'input JSON. Per ulteriori informazioni sul metodo e sui toni che restituisce, consulta [Utilizzo dell'endpoint di coinvolgimento cliente](/docs/services/tone-analyzer/using-tone-chat.html).

    La [customer engagement demo ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://customer-engagement-analytics.mybluemix.net/){: new_window} analizza le conversazioni tra i clienti e gli agenti del servizio clienti. Il servizio misura le preoccupazioni e la soddisfazione del cliente, valuta le prestazioni dell'agente e ti lascia valutare come si evolve l'interazione.

Per informazioni sui piani dei prezzi disponibili per il servizio, consulta il servizio [{{site.data.keyword.toneanalyzershort}} nel catalogo {{site.data.keyword.Bluemix_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/catalog/services/tone-analyzer){: new_window}.

## Casi di utilizzo

I seguenti sono alcuni casi di utilizzo interessanti:

-   *Ascolto nei social e monitoraggio dei destinatari:* monitora i social media per comprendere quali clienti stanno parlando del tuo marchio in tempo reale. Ad esempio, potresti determinare che i tuoi clienti in Chicago sono tristi dopo che i Bulls hanno perso o felici durante il festival Taste of Chicago. (Endpoint di utilizzo generico)
-   *Marketing personalizzato:* determina a chi destinare la messaggistica personalizzata e quando. Ad esempio, una compagnia di viaggi potrebbe inviare a clienti felici la messaggistica "regalati", a clienti tristi "scappa" e a clienti arrabbiati "relax". (Endpoint di utilizzo generico)
-   *Servizi di chat:* abilita un agent automatizzato per rilevare i toni del cliente e per creare risposte adeguate. Ad esempio, potresti rispondere alla tristezza con "Mi dispiace che sei turbato da questo problema" o alla soddisfazione con "Sono lieto che sei soddisfatto dei nostri servizi." (Endpoint di coinvolgimento del cliente)
-   *Monitoraggio del coinvolgimento del cliente e del controllo qualità:* monitora il tono generale delle comunicazioni del cliente e dell'agente, rileva le anomalie ed evidenzia le opportunità di formare gli agenti su come comunicare in modo migliore. (Endpoint di coinvolgimento del cliente)

Puoi anche utilizzare i servizi {{site.data.keyword.toneanalyzershort}} con servizi aggiuntivi {{site.data.keyword.ibmwatson_notm}}, come [{{site.data.keyword.conversationfull}}](https://console.bluemix.net/docs/services/conversation/index.html) o [{{site.data.keyword.speechtotextfull}}](https://console.bluemix.net/docs/services/speech-to-text/index.html), per analizzare l'input utente. Ad esempio, l'applicazione [Conversation Food Coach ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://food-coach.mybluemix.net/){: new_window} utilizza il servizio {{site.data.keyword.conversationshort}} per insegnare agli utenti a fare scelte sul cibo in base alle loro risposte su quello che mangiano. Per ulteriori informazioni, consulta questo [Watson blog post ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/watson/blog/2016/10/17/creating-a-compassionate-conversational-agent-using-watson-tone-analyzer-and-watson-conversation-services/){: new_window}.

> **Nota:** il servizio {{site.data.keyword.toneanalyzershort}} calcola algoritmicamente il tono del testo scritto. Non deduce le caratteristiche della personalità dell'autore del testo. Per ottenere un ritratto sulla personalità, consulta il servizio [{{site.data.keyword.personalityinsightsfull}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/services/personality-insights/index.html){: new_window}.

## Supporto lingua
{: #languages}

Il metodo `/v3/tone` può analizzare il contenuto in inglese (`en`) e francese (`fr`); il metodo `/v3/tone_chat`supporta solo l'inglese. Entrambi i metodi possono rispondere con il contenuto localizzato in varie lingue. Per ulteriori informazioni, consulta [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer/using-tone.html) e [Utilizzo dell'endpoint di coinvolgimento cliente](/docs/services/tone-analyzer/using-tone-chat.html).
