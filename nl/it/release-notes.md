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

# Note sulla release

Le seguenti sezioni illustrano le nuove funzioni e modifiche che sono state incluse in ogni release del servizio {{site.data.keyword.toneanalyzershort}}. Le modifiche non interrompono il codice esistente.
{: shortdesc}

> **Nota:** le note sulla release ora illustrano la *versione del servizio* e la *versione dell'interfaccia* di ogni aggiornamento. Hai specificato la *versione dell'interfaccia* con il parametro di query `version` per utilizzare le nuove funzioni e funzionalità rese disponibili con questo aggiornamento. Il servizio restituisce entrambe le versioni con l'intestazione della risposta `X-Service-Api-Version`.

## 28 settembre 2017
{: #September2017b}

**Versione del servizio:** `3.4.1`<br/> **Versione dell'interfaccia:** `2017-09-21`

-   Il limite di strozzatura sul numero massimo di richieste che un solo nome utente {{site.data.keyword.Bluemix_notm}} può inviare, è stato incrementato a 1200 richieste al minuto. Il servizio restituisce il codice di risposta HTTP 429 *Too many requests* se un utente supera tale limite.

## 25 settembre 2017
{: #September2017a}

**Versione del servizio:** `3.4.1`<br/> **Versione dell'interfaccia:** `2017-09-21`

-   L'endpoint di utilizzo generico (il metodo `/v3/tone`) è stato modificato nel seguente modo:

    -   Supporta il contenuto di input in francese (`fr`) in aggiunta all'inglese.
    -   Non restituisce più i toni sociali.
    -   Non restituisce più `disgust` con i toni emotivi.
    -   Omette tutti i toni il cui punteggio è inferiore a `0.5`. Questa qualifica corrisponde alla risposta del metodo `/v3/tone_chat`.
    - Non restituisce più le categorie del tono (il campo `tone_categories`) come parte del proprio output. Tutti i toni i cui valori soddisfano la soglia di qualifica vengono restituiti come parte di un solo oggetto `tones`. Come precedentemente, per impostazione predefinita i toni vengono sempre restituiti per il documento completo e per ogni singola frase.
    - Non accetta più un parametro di query `tones` per limitare l'output a toni specificati. Tutti i toni qualificati vengono restituiti per ogni richiesta. Includere il parametro con una richiesta non provoca un errore, ma non ha effetto sulla risposta.
    - Non restituisce più i campi `input_from` e `input_to` per le singole frasi. In aggiunta ai risultati dell'analisi, il metodo ora restituisce solo un ID e il testo di ogni frase.

-   Il servizio ora restituisce il codice di risposta HTTP 200 invece del 400 per l'input parzialmente corretto nei seguenti casi:

    -   Per il metodo `/v3/tone`, se invii più di 128 KB o 1000 frasi di contenuto di input, il servizio restituisce un campo `warning` come parte della propria risposta. Il servizio analizza le prime 1000 frasi per l'analisi al livello del documento e, come fa al momento, solo le prime 100 frasi per l'analisi al livello della frase. Le versioni precedenti del servizio restituivano il codice di risposta 400 per la richiesta se superavi il limite. Tieni inoltre presente che il servizio ora analizza le frasi che hanno meno di tre parole.
    -   Per il metodo `/v3/tone_chat`, se invii più di 50 affermazioni, il servizio restituisce un campo `warning` con il contenuto generale al livello della risposta `utterances_tone`; analizza solo le prime 50 affermazioni. Se invii una sola affermazione che contiene più di 500 caratteri, il servizio restituisce un campo `error` per l'affermazione e non esegue l'analisi. Le versioni precedenti del servizio restituivano il codice di risposta 400 se superavi il limite. Tiene presente che se tutte le affermazioni dell'input hanno più di 500 caratteri, il servizio restituirà il codice di risposta 400 per la richiesta.

-   Il servizio ora limita il numero di richieste che accetta da un solo utente. Il servizio restituisce il codice di risposta HTTP 429 *Too many requests* se riceve più di 600 richieste al minuto da un singolo nome utente {{site.data.keyword.Bluemix_notm}}.

-   Le seguenti modifiche sono state applicate agli endpoint di utilizzo generico e di coinvolgimento del cliente:

    -   La versione dell'interfaccia specificata con il parametro `version` è `2017-09-21` per utilizzare l'ultima versione del servizio.
    -   La documentazione è stata aggiornata per tenere presente che il servizio può produrre l'output localizzato in varie lingue. Utilizza l'intestazione della richiesta `Accept-Language` per specificare la lingua desiderata.

## 6 luglio 2017
{: #July2017b}

**Versione del servizio:** `3.3.6`<br/> **Versione dell'interfaccia:** `2016-05-19`

Il servizio è stato aggiornato per un piccolo problema all'endpoint di utilizzo generico.

## Release precedenti

-   [1 luglio 2017](#July2017a)
-   [8 maggio 2017](#May2017)
-   [17 aprile 2017](#April2017)
-   [15 marzo 2017](#March2017)
-   [1 dicembre 2016](#December2016)
-   [18 ottobre 2016](#October2016b)
-   [3 ottobre 2016](#October2016a)
-   [19 maggio 2016](#May2016)

### 1 luglio 2017
{: #July2017a}

**Versione del servizio:** `3.3.5`<br/> **Versione dell'interfaccia:** `2016-05-19`

L'endpoint di coinvolgimento del cliente del servizio {{site.data.keyword.toneanalyzershort}} è ora generalmente disponibile (GA). Tutte le chiamate all'endpoint vengono ora addebitate alla stessa tariffa delle chiamate all'endpoint di utilizzo generico.

### 8 maggio 2017
{: #May2017}

**Versione del servizio:** `3.3.4`<br/> **Versione dell'interfaccia:** `2016-05-19`

IBM ha aggiornato i modelli del punteggio del tono emotivo e del tono di coinvolgimento del supporto clienti espandendo ulteriormente il dataset di formazione. I modelli hanno ora una maggiore precisione nel dataset di riferimento.

### 17 aprile 2017
{: #April2017}

-   È ora disponibile una nuova serie di toni del dominio del supporto clienti: *frustrato*, *soddisfatto*, *eccitato*, *educato*, *maleducato*, *triste* e *comprensivo*. Il servizio rileva questi toni dal testo di una conversazione tra un cliente e un agente. I toni sono al momento una funzionalità beta.
-   IBM ha rilasciato gli aggiornamenti al modello di punteggio del tono emotivo che migliorano i risultati emotivi.

### 15 marzo 2017
{: #March2017}

IBM ha aggiornato il modello di punteggio del tono emotivo. Il dataset di formazione è stato espanso. Di conseguenza, i modelli hanno ora una maggiore precisione nel dataset di riferimento.

### 1 dicembre 2016
{: #December2016}

IBM ha aggiornato i punteggi del tono emotivo del documento. Il nuovo modello prende in considerazione il profilo emotivo delle frasi per aggregare il punteggio del documento.

### 18 ottobre 2016
{: #October2016b}

IBM ha migliorato il tono sociale. Il servizio ora utilizza una tecnica di integrazione della parola open source denominata [GloVe ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://nlp.stanford.edu/projects/glove/){: new_window} per dedurre i punteggi del tono sociale. Questa modifica consente al servizio di coprire un grande vocabolario di parole quando calcola i toni sociali. Per ulteriori informazioni su come vengono dedotti i toni sociali, consulta [The science behind the service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) per il servizio {{site.data.keyword.personalityinsightsshort}}.

### 3 ottobre 2016
{: #October2016a}

IBM ha migliorato il rilevamento emotivo al livello della frase. Il servizio utilizza i nuovi dati di formazione, un nuovo processo di selezione della funzione e i dizionari estesi di parole, emoticon e gerghi. Queste modifiche producono punteggi emotivi differenti ma significativamente migliorati al livello della frase. L'API del servizio non è stata modificata.

### 19 maggio 2016
{: #May2016}

La release generalmente disponibile (GA) del servizio {{site.data.keyword.toneanalyzershort}} include queste nuove funzioni:

-   I modelli del servizio utilizzano una sensibilità al contesto migliorata per interpretare il tono. I modelli ora utilizzano più dei soli token lessicali. Ora prendono in considerazione ulteriori funzioni come la punteggiatura, le emoticon, i parametri della lingua come la struttura e la complessità della frase.
-   Il modello del tono di scrittura è stato ridenominato con tono linguistico.
-   I modelli del tono linguistico ed emotivo ora gestiscono le negazioni.
-   Il servizio non restituisce più una risposta alla frasi con meno di tre parole.
-   Il servizio ha ora una [demo migliorata e semplificata ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://tone-analyzer-demo.mybluemix.net){: new_window}.
