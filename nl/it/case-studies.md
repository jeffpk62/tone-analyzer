---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-07"

subcollection: tone-analyzer

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Casi di studio
{: #caseStudies}

Leggi questi casi di studio per prendere ispirazione su cosa puoi fare con il servizio {{site.data.keyword.toneanalyzerfull}}. Gli studi descrivono la correlazione tra i toni riportati e i risultati previsti. La correlazione può essere positiva o negativa e ha un intervallo compreso tra -1.0 te 1.0.
{: shortdesc}

## Previsione della soddisfazione del cliente nei forum supportati
{: #supportForums}

IBM ha analizzato i forum di supporto clienti per un'azienda software che si concentra su diversi settori. L'azienda contribuisce attivamente ai forum di supporto clienti. Gli utenti possono assegnare *apprezzamento* alle risposte che ritengono utili.

### Obiettivi
{: #supportForumsGoals}

Prevedere la soddisfazione del cliente dal tono della domanda e della risposta. IBM presuppone che una risposta con apprezzamento significa che l'utente era soddisfatto.

### Azioni
{: #supportForumsActions}

-   Effettuata una ricerca per indicizzazione dei 1000 thread più recenti da diversi forum, assicurandosi di includere lo stesso numero di risposte con o senza apprezzamento.
-   Analizzate sia le domande che le risposte.
-   Applicati diversi classificatori all'avanguardia, come naive Bayes, SVM (Support Vector Machine) e random forest, per prevedere se una risposta avrebbe ricevuto l'apprezzamento.

### Risultati
{: #supportForumsResults}

Il servizio può prevedere l'apprezzamento con un'accuratezza del 66 percento. IBM ha rilevato le seguenti correlazioni tra i toni di una risposta restituita da un forum e la possibilità che tale risposta riceva apprezzamento:

-   Più la risposta è fiduciosa e più è probabile che guadagni apprezzamento (correlazione del 0.23 tra un punteggio di elevato valore sulla fiducia e l'apprezzamento).
-   Più la risposta è incerta ed è meno probabile che guadagni appezzamento (correlazione negativa di -0.27 tra un punteggio di elevato valore sull'incertezza e l'apprezzamento).

## Previsione della soddisfazione del cliente nelle risposte Twitter
{: #twitterResponses}

Molte aziende stanno passando il loro supporto clienti su Twitter. Twitter permette risposte in tempo reale, che aiutano a dimostrare che la marca utilizza persone reali che si prendono cura dei propri clienti.

IBM ha analizzato 333 conversazioni di supporto clienti su Twitter. I clienti erano soddisfatti su 240 conversazioni e non soddisfatti su 93 delle interazioni. IBM ha misurato la soddisfazione leggendo le conversazioni ed etichettandole. Le risposte sono state etichettate con "customer satisfied" quando il problema è stato risolto e il cliente sembrava soddisfatto. Sono state etichettate come "customer not satisfied" quando il problema non è stato risolto in modo ritenuto soddisfacente dal cliente.

### Obiettivi
{: #twitterResponsesGoals}

Convalidare se il tono della conversazione tra l'agente e il cliente ha influenzato la soddisfazione generale del cliente. Identificare inoltre le caratteristiche del tono che si ripercuotono in modo significativo sulla soddisfazione del cliente.

### Azioni
{: #twitterResponsesActions}

-   Tolta la punteggiatura, i riferimenti e i link dai tweet.
-   Suddivisa ogni interazione in tweet cliente e supporto.
-   Analizzato ogni lato della conversazione con il servizio {{site.data.keyword.toneanalyzershort}} e confrontati i risultati per trovare le correlazioni.

### Risultati
{: #twitterResponsesResults}

Il servizio può prevedere la soddisfazione del cliente dal tono della risposta con un'accuratezza del 67 percento. IBM ha scoperto la seguente correlazione tra il tono dei tweet del cliente e se era soddisfatto della risposta:

-   Più sono arrabbiati i clienti e meno sembrano essere soddisfatti della risposta. Esiste una correlazione negativa di -0.198 tra un punteggio di elevato valore per l'arrabbiatura in un tweet del cliente e la sua soddisfazione.

## Previsione degli elogi di TED Talk
{: #tedTalks}

TED è un'organizzazione no profit che effettua conferenze globali con lo slogan "Ideas worth spreading." Gli oratori TED Talk hanno 18 minuti per utilizzare una narrazione innovativa e coinvolgente per affrontare un'ampia gamma di argomenti nella ricerca e pratica di scienza e cultura. Non tutti i TED Talk sono popolari e un modo per misurare la soddisfazione del pubblico per un talk è di misurare la quantità di elogi che riceve.

### Obiettivi
{: #tedTalksGoals}

Rilevare quali modelli di toni nei TED Talk portano ad elogi e quali no. Prevedere inoltre l'elogio in base al tono di una frase.

### Azioni
{: #tedTalksActions}

Le frasi che ricevono l'elogio sono già state contrassegnate nel dataset.

-   Controllati 1931 TED Talk.
-   Categorizzata come "applause text" una frase contrassegnata con "Applause." Contrassegnate inoltre le tre frasi prima di quella con "applause text" e le tre dopo di quella con "non-applause text."
-   Analizzati sia i testi con l'elogio che senza con il servizio {{site.data.keyword.toneanalyzershort}}.
-   In base alle correlazioni che sono state trovate, sono stati creati dei classificatori per prevedere l'elogio in altri TED Talk in base al loro tono.

### Risultati
{: #tedTalksResults}

Il servizio può prevedere l'elogio con l'accuratezza del 75 percento. IBM ha trovato le seguenti correlazioni tra il tono di ogni serie di frasi e se tali frasi ricevono l'elogio:

-   Più tristemente un oratore si esprime ed è meno probabile che riceva un elogio (correlazione negativa di -0.055 tra un elevato valore di tristezza e l'elogio).
-   Più impassibile e impersonale un oratore sembra ed è meno probabile che riceva un elogio (correlazione negativa di -0.29 tra un elevato valore di metodicità e l'elogio).
-   Più gioioso, contento e soddisfatto un oratore sembra ed è più probabile che riceva un elogio (correlazione di 0.21 un elevato valore di gioia e l'elogio).

## Previsione di mi piace e retweet di Twitter
{: #twitterRetweets}

Creare un marchio su Twitter sta diventando un requisito per il successo delle aziende. Una parte essenziale che tu o la tua azienda deve decidere è di creare tweet che ottengono molti mi piace e retweet.

### Obiettivi
{: #twitterRetweetsGoals}

Trovare le correlazioni tra il tono di un tweet e se tale tweet è piaciuto o è stato fatto un retweet.

### Azioni
{: #twitterRetweetsActions}

-   Effettuata una ricerca per indicizzazione di 5881 tweet da diversi account di business su Twitter.
-   Tolta la punteggiatura, i riferimenti e i link dai tweet.
-   Analizzato ogni tweet con il servizio {{site.data.keyword.toneanalyzershort}} e confrontati i risultati per trovare le correlazioni.

### Risultati
{: #twitterRetweetsResults}

IBM ha trovato le correlazioni tra il tono di un tweet e se è piaciuto e tra il tono di un tweet e se ne è stato fatto un retweet.

## Previsione delle corrispondenze di appuntamenti online
{: #onlineDating}

Milioni di persone nel mondo utilizzano gli appuntamenti online per trovare qualcuno di speciale per loro. Le persone utilizzano gli appuntamenti online per trovare altri che hanno molto in comune con loro e per proporsi come potenziali partner.

### Obiettivi
{: #onlineDatingGoals}

Correlare il tono di un profilo individuale con il tono di un profilo potenzialmente corrispondente. Rilevare inoltre se tale correlazione prevede una corrispondenza positiva.

### Azioni
{: #onlineDatingActions}

-   È stata effettuata una ricerca per indicizzazione di circa 50.000 profili utente.
-   È stato analizzato ogni profilo con il servizio {{site.data.keyword.toneanalyzershort}}.
-   Sono state definite delle potenziali corrispondenze degli utenti che hanno comunicato tramite il sito.
-   È stata confrontata l'analisi del tono delle corrispondenze potenziali per trovare le correlazioni.
-   È stato sviluppato un modello statistico dalla similarità del tono dei profili per prevedere se due utenti potrebbero comunicare. È stato quindi confrontato il modello con più riferimenti che prendono in considerazione altri attributi, come ad esempio la demografia.

### Risultati
{: #onlineDatingResults}

La similarità del tono tra i profili può portare a un miglioramento del 45 percento nella previsione della possibile comunicazione tra due utenti rispetto ai predittori che i siti web di appuntamenti normalmente utilizzano. IBM ha rilevato una forte correlazione tra la similarità del tono e il numero di messaggi scambiati, come mostrato nella seguente immagine.

![Una forte correlazione tra i toni analizzati e il numero di messaggi scambiati.](images/case-study.svg)
