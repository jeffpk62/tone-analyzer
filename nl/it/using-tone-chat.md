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

# Utilizzo dell'endpoint di coinvolgimento del cliente
{: #utco}

L'endpoint di coinvolgimento del cliente {{site.data.keyword.toneanalyzershort}} analizza il tono delle conversazioni del supporto e del servizio clienti. Può essere utile per comprendere in modo migliore le interazioni con i clienti e migliorare le tue comunicazioni in generale o per clienti specifici. Per ulteriori informazioni sull'interfaccia, inclusi gli SDK Node.js, Java e Python disponibili per il richiamo del servizio, consulta [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
{: shortdesc}

La registrazione della richiesta è disabilitata per il servizio {{site.data.keyword.toneanalyzershort}}. A prescindere dalla tua impostazione dell'intestazione della richiesta `X-Watson-Learning-Opt-Out`, il servizio non registra o conserva i dati da richieste e risposte.
{: note}

## Richiesta di analisi del tono
{: #request-tone-chat}

Per analizzare il tono con l'endpoint di coinvolgimento del cliente, richiami il metodo `POST /v3/tone_chat` con i seguenti parametri.

<table>
  <caption>Tabella 1. Parametri del metodo <code>POST /v3/tone_chat</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parametro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo di dati</th>
    <th style="text-align:left">Descrizione</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Obbligatorio</em></td>
    <td style="text-align:center">Corpo</td>
    <td style="text-align:center">Oggetto JSON</td>
    <td>
      Un oggetto <code>ToneChatInput</code> JSON che contiene il contenuto che deve
      essere analizzato. Per ulteriori informazioni, vedi
      [Specifica dell'input JSON](#JSONrequest).
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obbligatorio</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">Stringa</td>
    <td>
      La versione dell'API che vuoi utilizzare come una data nel formato
      <code>YYYY-MM-DD</code>; ad esempio, specifica <code>2017-09-21</code>
      per il 21 settembre 2017 (la versione più recente). Per ulteriori informazioni su tutte
      le versioni disponibili vedi le
      [Note sulla release](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Facoltativo</em></td>
    <td style="text-align:center">Intestazione</td>
    <td style="text-align:center">Stringa</td>
    <td>
      La lingua del contenuto di input.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (inglese, valore predefinito)
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code> (francese)
        </li>
      </ul>
      Le varianti regionali sono trattate come le loro lingue principali; ad esempio,
      <code>en-US</code> viene interpretato come <code>en</code>. Il contenuto di input
      deve corrispondere alla lingua specificata. Non inviare contenuto
      che contiene entrambe le lingue. Puoi utilizzare lingue differenti per
      l'input e la risposta.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Facoltativo</em></td>
    <td style="text-align:center">Intestazione</td>
    <td style="text-align:center">Stringa</td>
    <td>
      La lingua richiesta della risposta.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code> (Arabo)
        </li>
        <li style="margin:0px; padding:0px">
          <code>de</code> (Tedesco)
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code> (Inglese, valore predefinito)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code> (Spagnolo)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (Francese)
        </li>
        <li style="margin:0px; padding:0px">
          <code>it</code> (Italiano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code> (Giapponese)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code> (Coreano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code> (Portoghese brasiliano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code> (Cinese semplificato)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code> (Cinese tradizionale)
        </li>
      </ul>
      Per gli argomenti a due caratteri, le varianti regionali sono trattate come le loro lingue principali; ad esempio,
      <code>en-US</code> viene interpretato come
      <code>en</code>. Puoi utilizzare lingue differenti per
      l'input e la risposta.
    </td>
  </tr>
</table>

Se invii più di 50 affermazioni, il servizio restituisce un campo `warning` con il contenuto generale al livello della risposta `utterances_tone`; analizza solo le prime 50 affermazioni. Se invii una sola affermazione che contiene più di 500 caratteri, il servizio restituisce un campo `error` per l'affermazione e non esegue l'analisi. In entrambi i casi, la richiesta ancora riesce con il codice di risposta HTTP 200.

Il servizio restituisce il codice di risposta 400 se tutte le affermazioni dell'input hanno più di 500 caratteri.
{: note}

### Richiesta di esempio
{: #exampleRequest}

Il seguente comando `curl` di esempio richiama l'endpoint di coinvolgimento del cliente con il file di input <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a> e una versione di `2017-09-21`:

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Specifica dell'input JSON
{: #JSONrequest}

Passi il metodo a un oggetto `ToneChatInput` JSON con il seguente formato. Il campo `utterances` fornisce un array di oggetti `utterance`. Il campo `text` è una stringa obbligatoria che fornisce un'affermazione fornita da un utente nella conversazione che deve essere analizzata. Il campo `user` è una stringa facoltativa che identifica l'utente che ha fornito l'affermazione.

```javascript
{
  "utterances": [
    {
      "text": "",
      "user": ""
    },
    . . .
  ]
}
```
{: codeblock}

Il seguente esempio illustra i contenuti del file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>. Il file include un breve scambio tra un <code>customer</code> e un <code>agent</code>.

```javascript
{
  "utterances": [
    {
      "text": "Hello, I'm having a problem with your product.",
      "user": "customer"
    },
    {
      "text": "OK, let me know what's going on, please.",
      "user": "agent"
    },
    {
      "text": "Well, nothing is working :(",
      "user": "customer"
    },
    {
      "text": "Sorry to hear that.",
      "user": "agent"
    }
  ]
}
```
{: codeblock}

## Contenuto della risposta JSON
{: #JSONresponse-tone-chat}

Il servizio restituisce un oggetto `UtteranceAnalyses` JSON che contiene un solo campo, `utterances_tone`. Questo campo contiene un array di oggetti `UtteranceAnalysis`, ognuno dei quali fornisce le seguenti informazioni su un'affermazione del contenuto di input:

-   `utterance_id` (numero intero) fornisce l'identificativo univoco dell'affermazione. La prima affermazione ha un ID 0 e l'ID di ogni affermazione successiva viene incrementato di uno.
-   `utterance_text` (stringa) fornisce il testo dell'affermazione.
-   `tones` è un array di oggetti `ToneChatScore` che fornisce i risultati per i toni dominanti. Questi toni hanno dei punteggi di almeno 0.5. L'array è vuoto se l'affermazione non ha un tono con un punteggio che soddisfa questa soglia.

Ogni oggetto `ToneChatScore` fornisce le seguenti informazioni sul tono qualificato:

-   `score` (doppio) è il punteggio del tono nell'intervallo compreso tra 0.5 e 1. Un punteggio maggiore di 0.75 indica un'alta probabilità che il tono sia stato percepito nell'affermazione.
-   `tone_id` (stringa) è l'identificativo non localizzato e univoco del tono; per le descrizioni dei toni, consulta [Toni di coinvolgimento del cliente](#tones-tone-chat).
-   `tone_name` (stringa) è il nome del tono localizzato e visibile dall'utente.

Il seguente esempio illustra la struttura dell'oggetto `UtteranceAnalyses`:

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": {integer},
      "utterance_text": "{string}",
      "tones": [
        {
          "score": {double},
          "tone_id": "{string",
          "tone_name": "{string}"
        }
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### Risposta di esempio
{: #exampleResponse-tone-chat}

Il seguente output viene restituito per le [Richiesta di esempio](#exampleRequest). (Lo stesso output viene restituito per l'esempio nell'[Esercitazione introduttiva](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted#customerEngagement).) Tutti i toni riportati hanno un punteggio di almeno 0.5. I toni con un punteggio di almeno 0.75 è molto probabile che siano stati percepiti dai partecipanti alla conversazione.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.686361,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": [
        {
          "score": 0.92724,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997795,
          "tone_id": "sad",
          "tone_name": "sad"
        }
      ]
    },
    {
      "utterance_id": 3,
      "utterance_text": "Sorry to hear that.",
      "tones": [
        {
          "score": 0.730982,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.672499,
          "tone_id": "sympathetic",
          "tone_name": "Sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Toni di coinvolgimento del cliente
{: #tones-tone-chat}

Il servizio può restituire i punteggi per i seguenti sette toni.

<table style="width:90%">
  <caption>Tabella 2. Toni di coinvolgimento del cliente</caption>
  <tr>
    <th style="text-align:left; width:20%">Tono / ID</th>
    <th style="text-align:left">Descrizione</th>
  </tr>
  <tr>
    <td>Eccitato<br/><code>excited</code></td>
    <td>
      Mostra interesse e entusiasmo personali.
    </td>
  </tr>
  <tr>
    <td>Frustrato<br/><code>frustrated</code></td>
    <td>
      Definito come sentirsi annoiato o irritabile.
    </td>
  </tr>
  <tr>
    <td>Maleducato<br/><code>impolite</code></td>
    <td>
      Essere sgarbati o scortesi
    </td>
  </tr>
  <tr>
    <td>Educato<br/><code>polite</code></td>
    <td>
      Definito come un comportamento orientato agli obiettivi, razionale
    </td>
  </tr>
  <tr>
    <td>Triste<br/><code>sad</code></td>
    <td>
      Considerato come un'emozione passiva non piacevole
    </td>
  </tr>
  <tr>
    <td>Soddisfatto<br/><code>satisfied</code></td>
    <td>
      Una risposta affettiva alla qualità del servizio percepita
    </td>
  </tr>
  <tr>
    <td>Comprensivo<br/><code>sympathetic</code></td>
    <td>
      Una modalità affettiva di comprensione che coinvolge risonanza emotiva
    </td>
  </tr>
</table>
