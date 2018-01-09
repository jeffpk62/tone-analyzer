---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

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

# La scienza dietro il servizio 

Il servizio {{site.data.keyword.toneanalyzerfull}} si basa sulla teoria di psicolinguistica, un campo di ricerca che esplora la relazione tra i comportamenti linguistici e le teorie psicologiche. Il servizio utilizza le analisi linguistiche e la correlazione tra le funzioni linguistiche del testo di scrittura e i toni linguistici ed emotivi per sviluppare punteggi per ognuna di queste dimensioni del tono.
{: shortdesc}

Le ricerche di psicolinguistica sono state effettuate per comprendere se le parole che utilizziamo nella nostra vita di tutti i giorni rispecchiano chi siamo, come ci sentiamo e cosa pensiamo. Dopo diverse decadi di ricerche in questo campo, viene ora accettato in psicologia, nel marketing ed in altri campi che la lingua rispecchia più di quanto vogliamo dire. La frequenza con cui utilizziamo alcuni tipi di parole può fornire indizi sulla personalità, sullo stile di pensiero, sulle connessioni sociali e sugli stati emotivi.

Ad esempio, le persone esibiscono vari toni nella loro comunicazioni giornaliere: felice o triste, aperto o moderato, analitico o informale ([Gou et al., 2014](/docs/services/tone-analyzer/references.html#bib-gou) e [Jian et al., 2014](/docs/services/tone-analyzer/references.html#bib-jian)). Questi toni possono influenzare la percezione dell'identità online di una persona e l'efficacia delle loro comunicazioni in diversi contesti.

Inoltre, nella comunicazioni email di business, le persone probabilmente percepiscono emozioni negative con grande intensità rispetto ad emozioni positive ([Byron, 2008](/docs/services/tone-analyzer/references.html#bib-byron)). E nei social media, le persone presentano diverse identità online che influenzano l'impressione che gli altri hanno di loro ([DiMicco & Millen, 2007](/docs/services/tone-analyzer/references.html#bib-dimicco)).

Molte persone leggono in modo naturale un messaggio e giudicano i toni comunicati dal mittente. Ma può un computer rilevare i toni divulgati da un messaggio in modo automatico e accurato? Questa è una delle molte domande complesse a cui i ricercatori nei campi delle scienze cognitive e di intelligenza artificiale stanno cercando delle risposte. Prima con il servizio {{site.data.keyword.personalityinsightsshort}} e ora con il servizio {{site.data.keyword.toneanalyzershort}}, IBM ha iniziato a rispondere a questa domanda.

## Panoramica sulle ricerche correlate.

La ricerca ha mostrato una correlazione forte e statisticamente significativa tra la scelta delle parole e la personalità, le emozioni, le attitudini, i bisogni intrinsechi, i valori e i processi mentali. Molte ricerche hanno scoperto che le persone cambiano il modo di come spesso utilizzano alcune categorie di parole quando scrivono nei blog, nella saggistica e nei tweet e che questi mezzi di comunicazione possono aiutare a prevedere aspetti differenti della personalità:

-   [Fast and Funder (2008)](/docs/services/tone-analyzer/references.html#bib-fast)
-   [Gill et al. (2009)](/docs/services/tone-analyzer/references.html#bib-gill)
-   [Golbeck et al. (2011)](/docs/services/tone-analyzer/references.html#bib-golbeck)
-   [Hirsh and Peterson (2009)](/docs/services/tone-analyzer/references.html#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer/references.html#bib-yarkoni)

Molti di questi lavori precedenti si basavano sul trovare categorie di parole psicologicamente significative dall'utilizzo delle parole nella scrittura. Questa ricerca serve come base per il lavoro di IBM nel servizio {{site.data.keyword.toneanalyzershort}}. Basandosi sulle scoperte scientifiche dalla ricerca psicolinguistica, IBM sta lavorando per dedurre le caratteristiche della personalità delle persone, i loro stili di scrittura e pensiero, le loro emozioni e i valori e bisogni intrinsechi dalle parole che scrivono. IBM utilizza i propri modelli di apprendimento automatico per valutare queste caratteristiche stimando varie funzioni della scrittura di una persona.

## Il modello di utilizzo generico
{: #analysis}

L'endpoint di utilizzo generico analizza il contenuto scritto di una serie di toni applicabili ad un'ampia gamma di utilizzi. Il servizio {{site.data.keyword.toneanalyzershort}} calcola una scorecard che include i seguenti toni:

-   **Tono emotivo** viene derivato dal lavoro di IBM sulle analisi emotive, che sono un framework completo che deduce le emozioni da un testo scritto. Per derivare i punteggi emotivi dal testo, IBM utilizza un framework completo basato sulla generalizzazione impilata; la generalizzazione impilata utilizza un modello di livello superiore per combinare i modelli di livello inferiore per archiviare una maggiore accuratezza predittiva. Le funzioni come n-grams (unigrams, bigrams e trigrams), la punteggiatura, le emoticon, le parolacce, i saluti (come "salve," "ciao," e "grazie") e la polarità dei sentimenti vengono forniti agli algoritmi di apprendimento automatico per classificare le categorie emotive.
-   **Tono linguistico** viene calcolato dalle analisi linguistiche basate sulle funzioni di apprendimento.

### Misurazione della qualità del servizio

IBM ha misurato la qualità del servizio {{site.data.keyword.toneanalyzershort}} insieme alle dimensioni del tono menzionate nella sezione precedente:

-   Per le categorie *Tono emotivo* è stato fatto riferimento ai dataset delle emozioni standard come ISEAR e SEMEVAL. I risultati mostrano che le prestazioni medie del modello completo (il punteggio F1 di media macro è circa il 41 e 60 percento, rispettivamente, per i due dataset) sono statisticamente migliori dell'accuratezza riportata dai modelli all'avanguardia (i cui punteggi di media macro sono circa il 37 e il 63 percento, rispettivamente).
-   *Tono linguistico* è stato valutato con un studio approfondito di più di duecentomila frasi raccolte da origini come forum di dibattito, discorsi e social media. Di queste frasi, IBM ha selezionato a caso 1330 frasi per il tono analitico e 1000 frasi ognuna delle quali per i toni esitante e confidente. IBM ha quindi inviato queste frasi al servizio {{site.data.keyword.toneanalyzershort}} e ha anche chiesto a degli esseri umani di analizzarle.

    Per l'analisi umana, IBM ha utilizzato una piattaforma di crowd-sourcing denominata [CrowdFlower ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.crowdflower.com/){: new_window} per annotare le frasi selezionate con diverse etichette. Solo ai valutatori con valutazioni di approvazione sopra l'85 percento è stato permesso di partecipare alle attività di annotazione. Cinque annotatori hanno etichettato ogni frase e IBM ha utilizzato i cinque risultati annotati più diffusi per determinare le etichette finali.
    -   Per il *tono analitico*, sono state etichettate 915 di 1330 frasi come analitiche, 411 come non analitiche e 4 come non comprensibili. Confrontando l'etichetta prevista con queste etichette sul campo, IBM ha trovato che il proprio rilevamento del tono analitico ha ricevuto un punteggio F1 di 0.7518.
    -   Per il *tono incerto*, sono state etichettate 292 di 1000 frasi come incerto, 706 come non incerto e 2 come non comprensibile. Confrontando l'etichetta prevista con le etichette sul campo, IBM ha trovato che il proprio rilevamento del tono incerto ha ricevuto un punteggio F1 di 0.6369. 
    -   Per il *tono confidente*, sono state etichettate 623 di 1000 frasi come confidente, 374 come non confidente e 3 come non comprensibile. Confrontando l'etichetta prevista con le etichette sul campo, IBM ha trovato che il proprio rilevamento del tono confidente ha ricevuto un punteggio F1 di 0.7288. 

Nel complesso, la differenza tra le etichette previste e sul campo sono è statisticamente significativa. Questo indica che il servizio funziona bene.

## Il modello di coinvolgimento del cliente

L'endpoint di coinvolgimento del cliente identifica i toni dal dominio di supporto clienti. Per selezionare i toni da valutare con il modello di coinvolgimento del cliente, IBM ha prima condotto uno studio per identificare quali dimensioni del tono vengono percepite come importanti nel dominio:

1.  IBM ha selezionato una serie di 53 toni dalle dimensioni del tono utilizzate nel marketing, le dimensioni utilizzate per descrivere gli stili di scrittura e le scale di personalità ed emozioni psicologiche.
1.  IBM ha chiesto ai dipendenti di CrowdFlower di valutare la misura con cui i 53 attributi del tono descrivono un'affermazione specifica in 1000 conversazioni del supporto clienti. Per semplificare l'attività di valutazione nel contesto di crowd-sourcing, IBM ha diviso i 53 toni in quattro sottoinsiemi. Gli annotatori umani devono valutare solo un sottoinsieme dei toni; IBM quindi determina le valutazioni per tutti i toni dalle aggregazioni di questi risultati.
1.  IBM ha eseguito l'analisi dei fattori su una matrice di correlazione 53 a 53 e ha trovato almeno sette fattori significativi (dimensioni). IBM ha determinato i nomi dei fattori per rappresentare i concetti più importanti rispecchiati da ognuna delle dimensioni.

Questi passi identificano sette importanti dimensioni del tono per il dominio di supporto clienti; frustrazione, soddisfazione, eccitazione, educazione, maleducazione, tristezza e simpatia.

### Raccolta dati 

IBM ha utilizzato i forum di supporto clienti di Twitter come origine dei dati conversazionali per le proprie analisi del tono nel dominio di supporto clienti. Molte aziende utilizzano Twitter come un canale per fornire supporto ai propri clienti. Gli agenti sono assunti e formati per monitorare i tweet che fanno menzione dell'azienda, per indirizzare le richieste di aiuto e per fornire un supporto rapido per risolvere i bisogni dei clienti.

Per raccogliere più conversazioni possibili, IBM ha selezionato 62 marchi con account di supporto clienti dedicati su Twitter. IBM ha scelto questi marchi per coprire una grande varietà di settori, ubicazioni geografiche e scale organizzative. Nel complesso, IBM ha raccolto 2.6 milioni di richieste utente tra il 1 giugno e il 1 agosto 2016.

### Annotazione dati

IBM ha passato al setaccio il dataset raccolto per conservare solo quelle conversazioni che hanno ricevuto almeno una risposta e che hanno coinvolto solo un cliente e un agente. IBM ha anche rimosso dal dataset tutte le conversazioni non in inglese e quelle che contenevano richieste o domande con immagini. Per conservare la privacy delle aziende e degli utenti, IBM ha sostituito tutti i *@mentions* in ogni conversazione con *@customer*, *@[industry]_company* (ad esempio, *@ecommerce_company* o *@telecommunication_company*), *@competitor_company*, o *@other_users*.

Questo processo di selezione ha identificato approssimativamente 96 mila affermazioni conversazionali per le annotazioni dei dipendenti di CrowdFlower. Per promuovere una maggiore comprensione del contesto di annotazione, IBM ha chiesto ai dipendenti di commentare a un livello di conversazione, etichettando tutte le affermazioni coinvolte in una conversazione. Poiché la natura soggettiva di alcuni dei toni proposti potrebbe portare a percezioni inconsistenti, IBM ha chiesto agli annotatori di indicare quando fortemente ritengono che le affermazioni dimostrino i toni su una scala Likert a quattro punti compresa tra "Molto fortemente e "Per niente". Una scala Likert è preferibile a una scala sì/no binaria semplice perché permette un'elevata tolleranza di differenti percezioni e genera etichette meno scarse.

Cinque diversi annotatori etichettano ogni conversazione. IBM ha utilizzato solo annotatori ubicati negli Stati Uniti con un livello accettabile di prestazioni da precedenti attività di commento. IBM ha inoltre richiesto agli annotatori di rispondere a cinque domande di formazione prima che potessero procedere con le attività di commento reali. Le domande di formazione garantiscono che gli annotatori abbiano un'idea del significato di ogni tono nel contesto del servizio clienti. IBM ha anche incorporato le domande di convalida nelle attività reali per una ulteriore convalida della qualità delle etichette degli annotatori.

IBM ha utilizzato la media dei punteggi di cinque annotatori per l'etichetta finale di ogni affermazione. IBM ha quindi utilizzato un punteggio di 1 come soglia per la conversione delle etichette in valori binari. IBM ha scelto 1 come soglia in base alle osservazioni sulle distribuzioni dell'etichetta e alle prestazioni dei modelli con diverse soglie. I risultati finali hanno prodotto la seguente distribuzione delle affermazioni: 9536 frustrati, 10.806 soddisfatti, 6107 eccitati, 63.853 educati, 1688 maleducati, 24.954 tristi e 10.475 simpatici.

### Ulteriori informazioni sui modelli del tono

In base a queste conversazioni del supporto clienti, IBM ha formato un modello di apprendimento automatico basato su SVM (Support Vector Machine) per prevedere il tono per le nuove affermazioni del supporto clienti. Per il modello di apprendimento automatico, IBM ha sfruttato diverse categorie di funzioni, incluse le funzioni n-gram, le funzioni lessicali da vari dizionari, l'esistenza di riferimenti ad altre persone nella conversazione, alcune funzioni specifiche del dialogo come se viene detto grazie o scusa e molte funzioni di livello superiore come l'esistenza di punti di domanda o esclamativi consecutivi.

IBM ha scoperto che circa il 30 percento degli esempi ha più di un tono associato. IBM ha quindi deciso di trovare un'attività di classificazione a più livelli rispetto a una a più classi. Per ogni tono, IBM ha formato il modello indipendentemente dall'utilizzo del paradigma One-vs-Rest (OVR). Il paradigma ha utilizzato le affermazioni di ogni classe come esempi positivi e tutte le altre affermazioni come esempi negativi. IBM ha identificato i toni previsti con almeno la probabilità di 0,5 per i toni finali. Per molti toni, i dati di formazione erano pesantemente sbilanciati; IBM ha quindi identificato il valore di utilizzo ottimale della funzione del valore di ogni tono durante la formazione.

IBM ha utilizzato precisione, richiamo e punteggio F per valutare l'accuratezza del proprio modello di classificazione. Il modello ha dimostrato elevata accuratezza quando confrontato con un dataset di riferimento.
