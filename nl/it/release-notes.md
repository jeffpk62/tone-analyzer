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

# Note sulla release
{: #rnrn}

Le seguenti sezioni illustrano le nuove funzioni e modifiche che sono state incluse in ogni release del servizio {{site.data.keyword.toneanalyzershort}}. Le modifiche non interrompono il codice esistente.
{: shortdesc}

Le note sulla release documentano la *versione del servizio* e la *versione dell'interfaccia* per ogni aggiornamento. Hai specificato la *versione dell'interfaccia* con il parametro di query `version` per utilizzare le nuove funzioni e funzionalità rese disponibili con questo aggiornamento. Il servizio restituisce entrambe le versioni con l'intestazione della risposta `X-Service-Api-Version`.
{: note}

## 22 febbraio 2019
{: #February2019}

**Versione del servizio** - `3.5.9`<br/> **Versione dell'interfaccia** - `2017-09-21`

-   Il servizio {{site.data.keyword.toneanalyzershort}} nell'ubicazione di Francoforte di {{site.data.keyword.cloud}} (**eu-de**) utilizza ora l'autenticazione IAM (Identity e Access Management) basata sui token. Tutte le nuove istanze del servizio che crei in questa o in qualsiasi altra ubicazione utilizzano l'autenticazione IAM.
-   Il servizio è stato anche aggiornato per le modifiche e i miglioramenti interni.

## 18 novembre 2018
{: #November2018b}

**Versione del servizio** - `3.5.4`<br/> **Versione dell'interfaccia** - `2017-09-21`

Il servizio {{site.data.keyword.toneanalyzershort}} è ora disponibile nell'ubicazione Londra di {{site.data.keyword.cloud_notm}} (**eu-gb**). Come tutte le ubicazioni, Londra utilizza l'autenticazione IAM basata sui token. Tutte le nuove istanze del servizio che crei in questa ubicazione utilizzano l'autenticazione IAM.

## 7 novembre 2018
{: #November2018a}

**Versione del servizio** - `3.5.4`<br/> **Versione dell'interfaccia** - `2017-09-21`

Il servizio {{site.data.keyword.toneanalyzershort}} è ora disponibile nell'ubicazione Tokyo di {{site.data.keyword.cloud_notm}} (**jp-tok**). Come tutte le ubicazioni, Tokyo utilizza l'autenticazione IAM basata sui token. Tutte le nuove istanze del servizio che crei in questa ubicazione utilizzano l'autenticazione IAM.

## Release precedenti
{: #rnor}

  - [30 ottobre 2018](#30-october-2018)
  - [11 giugno 2018](#11-june-2018)
  - [25 maggio 2018](#25-may-2018)
  - [13 marzo 2018](#13-march-2018)
  - [28 settembre 2017](#28-september-2017)
  - [25 settembre 2017](#25-september-2017)
  - [6 luglio 2017](#6-july-2017)
  - [1 luglio 2017](#1-july-2017)
  - [8 maggio 2017](#8-may-2017)
  - [17 aprile 2017](#17-april-2017)
  - [15 marzo 2017](#15-march-2017)
  - [1 dicembre 2016](#1-december-2016)
  - [18 ottobre 2016](#18-october-2016)
  - [3 ottobre 2016](#3-october-2016)
  - [19 maggio 2016](#19-may-2016)

### 30 ottobre 2018
{: #October2018}

**Versione del servizio** - `3.5.4`<br/> **Versione dell'interfaccia** - `2017-09-21`

Il servizio {{site.data.keyword.toneanalyzershort}} ha eseguito la migrazione all'autenticazione IAM basata sui token per tutte le ubicazioni. Tutti i servizi {{site.data.keyword.cloud_notm}} ora utilizzano l'autenticazione IAM. Il servizio {{site.data.keyword.toneanalyzershort}} ha eseguito la migrazione in ciascuna ubicazione nelle seguenti date:

-   Dallas (**us-south**): 30 ottobre 2018
-   Francoforte (**eu-de**): in corso
-   Washington, DC (**us-east**): 11 giugno 2018
-   Sydney (**au-syd**): 25 maggio 2018

Il servizio continua a utilizzare le credenziali del servizio Cloud Foundry per l'autenticazione nell'ubicazione di Francoforte. Questa ubicazione eseguirà la migrazione all'autenticazione IAM il prima possibile.
{: important}

La migrazione all'autenticazione IAM influenza le istanze del servizio nuove e esistenti in modo differente:

-   *Tutte le nuove istanze del servizio che crei in qualsiasi ubicazione* ora utilizzano l'autenticazione IAM per accedere al servizio. Puoi passare un token di connessione (bearer) oppure una chiave API: i token supportano le richieste autenticate senza integrare le credenziali del servizio in ogni chiamata; le chiavi API utilizzano l'autenticazione di base HTTP. Quando utilizzi uno qualsiasi degli SDK {{site.data.keyword.watson}}, puoi passare la chiave API e lasciare che SDK gestisca il ciclo di vita dei token.
-   *Le istanze del servizio esistenti che hai creato in un'ubicazione prima della data di migrazione indicata*  continuano a utilizzare il nome utente (`{username}`) e la password (`{password}`) dalle loro precedenti credenziali del servizio Cloud Foundry per l'autenticazione finché non ne esegui l'aggiornamento  per utilizzare l'autenticazione IAM. Poiché il servizio {{site.data.keyword.toneanalyzershort}} è senza stato, puoi eseguire la seguente procedura per convertire un'istanza del servizio esistente per utilizzare l'autenticazione IAM:

    1.  Elimina e crea nuovamente l'istanza del servizio.
    1.  Modifica il tuo codice dell'applicazione per utilizzare l'autenticazione IAM.

Per ulteriori, vedi la seguente documentazione:

-   Per sapere quale meccanismo di autenticazione utilizza la tua istanza del servizio, visualizza le tue credenziali di servizio facendo clic sull'istanza nel [dashboard {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/dashboard/apps){: new_window}.
-   Per ulteriori informazioni sull'utilizzo dei token IAM con i servizi Watson, vedi [Autenticazione con i token IAM](/docs/services/watson?topic=watson-iam).
-   Per ulteriori informazioni sull'utilizzo delle chiavi API IAM con i servizi Watson, vedi[Chiavi API del servizio IAM](/docs/services/watson?topic=watson-api-key-bp).
-   Per degli esempi che utilizzano l'autenticazione IAM, vedi la [Guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

### 11 giugno 2018
{: #June2018}

**Versione del servizio** - `3.5.4`<br/> **Versione dell'interfaccia** - `2017-09-21`

Per le istanze del servizio e le applicazioni ospitate a Washington, DC (**us east**), il servizio ora supporta un nuovo processo di autenticazione API. Per ulteriori informazioni, vedi l'[aggiornamento del servizio del 30 ottobre 2018](#October2018).

### 25 maggio 2018
{: #May2018}

**Versione del servizio** - `3.5.4`<br/> **Versione dell'interfaccia** - `2017-09-21`

Per le istanze del servizio e le applicazioni ospitate a Sydney (**au-syd**), il servizio ora supporta un nuovo processo di autenticazione API. Per ulteriori informazioni, vedi l'[aggiornamento del servizio del 30 ottobre 2018](#October2018).

### 13 marzo 2018
{: #March2018}

**Versione del servizio** - `3.5.3`<br/> **Versione dell'interfaccia** - `2017-09-21`

Il servizio è stato aggiornato per aggiungere il contenuto di input in francese (`fr`) in aggiunta all'inglese per l'endpoint di coinvolgimento del cliente, `/v3/tone_chat`. Utilizzi l'intestazione della richiesta `Content-Language` per specificare una lingua; il valore predefinito è inglese (US).

### 28 settembre 2017
{: #September2017b}

**Versione del servizio** - `3.4.1`<br/> **Versione dell'interfaccia** - `2017-09-21`

La limitazione relativa al numero massimo di richieste che un singolo nome utente {{site.data.keyword.cloud_notm}} può inviare è aumentato a 1200 richieste al minuto. Il servizio restituisce il codice di risposta HTTP 429 *Too many requests* se un utente supera tale limite.

### 25 settembre 2017
{: #September2017a}

**Versione del servizio** - `3.4.1`<br/> **Versione dell'interfaccia** - `2017-09-21`

-   L'endpoint di utilizzo generico (il metodo `/v3/tone`) è stato modificato.

    -   Supporta il contenuto di input in francese (`fr`) in aggiunta all'inglese.
    -   Non restituisce più i toni sociali.
    -   Non restituisce più `disgust` con i toni emotivi.
    -   Omette tutti i toni il cui punteggio è inferiore a `0.5`. Questa qualifica corrisponde alla risposta del metodo `/v3/tone_chat`.
    - Non restituisce più le categorie del tono (il campo `tone_categories`) come parte del proprio output. Tutti i toni i cui valori soddisfano la soglia di qualifica vengono restituiti come parte di un solo oggetto `tones`. Come precedentemente, per impostazione predefinita i toni vengono sempre restituiti per il documento completo e per ogni singola frase.
    - Non accetta più un parametro di query `tones` per limitare l'output a toni specificati. Tutti i toni qualificati vengono restituiti per ogni richiesta. Includere il parametro con una richiesta non provoca un errore, ma non ha effetto sulla risposta.
    - Non restituisce più i campi `input_from` e `input_to` per le singole frasi. In aggiunta ai risultati dell'analisi, il metodo ora restituisce solo un ID e il testo di ogni frase.

-   Il servizio ora restituisce il codice di risposta HTTP 200 invece del 400 per l'input parzialmente corretto nei seguenti casi:

    -   Per il metodo `/v3/tone`, se invii più di 128 KB o 1000 frasi di contenuto di input, il servizio restituisce un campo `warning` come parte della propria risposta. Il servizio analizza le prime 1000 frasi per l'analisi al livello del documento. Analizza solo le prime 100 frasi per l'analisi al livello della frase. Le versioni precedenti del servizio restituivano il codice di risposta 400 per la richiesta se superavi il limite. Inoltre, il servizio ora analizza le frasi che hanno meno di tre parole.
    -   Per il metodo `/v3/tone_chat`, se invii più di 50 affermazioni, il servizio restituisce un campo `warning` con il contenuto generale al livello della risposta `utterances_tone`; analizza solo le prime 50 affermazioni. Se invii una sola affermazione che contiene più di 500 caratteri, il servizio restituisce un campo `error` per l'affermazione e non esegue l'analisi. Le versioni precedenti del servizio restituivano il codice di risposta 400 se superavi il limite. Se tutte le affermazioni dell'input hanno più di 500 caratteri, il servizio restituisce comunque il codice di risposta 400 per la richiesta.

-   Il servizio ora limita il numero di richieste che accetta da un solo utente. Il servizio restituisce il codice di risposta HTTP 429 *Too many requests* se riceve più di 600 richieste al minuto da un singolo nome utente {{site.data.keyword.cloud_notm}}.

-   Le seguenti modifiche sono state applicate sia agli endpoint di utilizzo generico sia a quelli di coinvolgimento del cliente:

    -   La versione dell'interfaccia specificata con il parametro `version` è `2017-09-21` per utilizzare la versione più recente del servizio.
    -   La documentazione è stata aggiornata per indicare che il servizio può produrre l'output localizzato in varie lingue. Utilizza l'intestazione della richiesta `Accept-Language` per specificare la lingua.

### 6 luglio 2017
{: #July2017b}

**Versione del servizio** - `3.3.6`<br/> **Versione dell'interfaccia** - `2016-05-19`

Il servizio è stato aggiornato per una piccola correzione di un difetto all'endpoint di coinvolgimento del cliente.

### 1 luglio 2017
{: #July2017a}

**Versione del servizio** - `3.3.5`<br/> **Versione dell'interfaccia** - `2016-05-19`

L'endpoint di coinvolgimento del cliente del servizio {{site.data.keyword.toneanalyzershort}} è ora generalmente disponibile (GA). Tutte le chiamate all'endpoint vengono ora addebitate alla stessa tariffa delle chiamate all'endpoint di utilizzo generico.

### 8 maggio 2017
{: #May2017}

**Versione del servizio** - `3.3.4`<br/> **Versione dell'interfaccia** - `2016-05-19`

IBM ha aggiornato i modelli del punteggio del tono emotivo e del tono di coinvolgimento del supporto clienti espandendo ulteriormente il dataset di formazione. I modelli hanno ora una maggiore precisione nel dataset di riferimento.

### 17 aprile 2017
{: #April2017}

-   È ora disponibile una nuova serie di toni specifici per il dominio di coinvolgimento del cliente: *frustrated*, *satisfied*, *excited*, *polite*, *impolite*, *sad* e *sympathetic*. Il servizio rileva questi toni dal testo di una conversazione tra un cliente e un agente. I toni sono al momento una funzionalità beta.
-   IBM ha rilasciato gli aggiornamenti al modello di punteggio del tono emotivo che migliorano i risultati emotivi.

### 15 marzo 2017
{: #March2017}

IBM ha aggiornato il modello di punteggio del tono emotivo. Il dataset di formazione è stato espanso. Di conseguenza, i modelli hanno ora una maggiore precisione nel dataset di riferimento.

### 1 dicembre 2016
{: #December2016}

IBM ha aggiornato i punteggi del tono emotivo del documento. Il nuovo modello prende in considerazione il profilo emotivo delle frasi per aggregare il punteggio del documento.

### 18 ottobre 2016
{: #October2016b}

IBM ha migliorato il tono social. Il servizio ora utilizza una tecnica di integrazione della parola open source denominata [GloVe ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://nlp.stanford.edu/projects/glove/){: new_window} per dedurre i punteggi del tono social. Questa modifica consente al servizio di coprire un vocabolario più ampio di parole quando calcola i toni sociali. Per ulteriori informazioni su come vengono dedotti i toni sociali, consulta [The science behind the service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) per il servizio {{site.data.keyword.personalityinsightsshort}}.

### 3 ottobre 2016
{: #October2016a}

IBM ha migliorato il rilevamento emotivo al livello della frase. Il servizio utilizza i nuovi dati di formazione, un nuovo processo di selezione della funzione e i dizionari estesi di parole, emoticon e gerghi. Queste modifiche producono punteggi emotivi differenti ma significativamente migliorati al livello della frase. L'API del servizio non è stata modificata.

### 19 maggio 2016
{: #May2016}

La release generalmente disponibile (GA) del servizio {{site.data.keyword.toneanalyzershort}} include queste nuove funzioni:

-   I modelli del servizio utilizzano una sensibilità al contesto migliorata per interpretare il tono. I modelli ora non si limitano a utilizzare i token lessicali. Ora prendono in considerazione funzioni come la punteggiatura, le emoticon, i parametri della lingua come la struttura e la complessità della frase.
-   Il modello del tono di scrittura è stato ridenominato con tono linguistico.
-   I modelli del tono linguistico ed emotivo ora gestiscono le negazioni.
-   Il servizio non restituisce più una risposta alla frasi con meno di tre parole.
-   Il servizio ha ora una [demo migliorata e semplificata ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://tone-analyzer-demo.ng.bluemix.net){: new_window}.
