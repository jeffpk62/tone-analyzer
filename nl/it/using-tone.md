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

# Utilizzo dell'endpoint di utilizzo generico
{: #utgpe}

L'endpoint di utilizzo generico {{site.data.keyword.toneanalyzershort}} analizza il tono delle comunicazioni scritte, da brevi messaggi email a documenti più lunghi. Può essere utile a comprendere i toni linguistici ed emotivi delle tue comunicazioni. Per ulteriori informazioni sull'interfaccia, inclusi gli SDK Node.js, Java e Python disponibili per il richiamo del servizio, consulta [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
{: shortdesc}

La registrazione della richiesta è disabilitata per il servizio {{site.data.keyword.toneanalyzershort}}. A prescindere dalla tua impostazione dell'intestazione della richiesta `X-Watson-Learning-Opt-Out`, il servizio non registra o conserva i dati da richieste e risposte.
{: note}

## Richiesta di analisi del tono
{: #request-tone}

Per analizzare il tono con l'endpoint di utilizzo generico, richiama una delle due versioni del metodo `tone` del servizio:

-   Il metodo `POST /v3/tone` accetta contenuti di input in formato JSON, testo semplice o HTML tramite il corpo della richiesta. Utilizza questa versione del metodo per il testo più lungo o per il testo che non vuoi esporre nell'URL.
-   Il metodo `GET /v3/tone` accetta i contenuti di input tramite il proprio parametro di query `text` obbligatorio. Utilizza questa versione del metodo per il testo semplice che viene facilmente ospitato nell'URL.

I metodi accettano i seguenti parametri.

<table>
  <caption>Tabella 1. Parametri dei metodi <code>/v3/tone</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parametro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo di dati</th>
    <th style="text-align:left">Descrizione</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Obbligatorio per <code>POST</code></em></td>
    <td style="text-align:center">Corpo</td>
    <td style="text-align:center">Oggetto JSON | Stringa</td>
    <td>
      Input JSON, testo semplice o HTML che contiene il contenuto che deve
      essere analizzato. Per l'input JSON, fornisci un oggetto di tipo
      <code>ToneInput</code>. Per ulteriori informazioni, vedi
      [Specifica dell'input JSON](#JSONinput). <em>Non supportato per le richieste <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Obbligatorio per <code>GET</code></em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">Stringa</td>
    <td>
      L'input di testo semplice che contiene il contenuto che deve essere analizzato. Devi codificare
      tramite URL l'input. <em>Non supportato per le richieste <code>POST</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>Obbligatorio per <code>POST</code></em></td>
    <td style="text-align:center">Intestazione</td>
    <td style="text-align:center">Stringa</td>
    <td>
      Il tipo di contenuto della richiesta.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> per il testo semplice
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> per il testo in HTML (il servizio rimuove le tag
            HTML e analizza solo il contenuto testuale)
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> per il testo nel formato JSON
        </li>
      </ul>
    <em>Ometti per le richieste <code>GET</code>.</em>
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
          <code>en</code> (inglese, valore predefinito)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code> (Spagnolo)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (francese)
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
  <tr>
    <td><code>sentences</code><br/><em>Facoltativo</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">Booleano</td>
    <td>
      Indica se il servizio deve restituire un'analisi di ogni singola
      frase in aggiunta alla propria analisi del documento completo.
      Se <code>true</code> (valore predefinito), il servizio restituisce i risultati per
      ogni frase.
    </td>
  </tr>
</table>

Invia non più di 128 KB di contenuto di input totale e non più di 1000 frasi singole. Il servizio analizza le prime 1000 frasi per l'analisi al livello del documento e solo le prime 100 frasi per l'analisi al livello della frase. Restituisce un campo `warning` come parte della propria risposta se superi il limite; la richiesta ancora riesce con il codice di risposta HTTP 200.

### Richieste di esempio
{: #exampleRequests}

Il seguente comando `curl` di esempio utilizza il metodo di richiesta `POST` HTTP per richiamare l'endpoint di utilizzo generico con il file di input <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a> e una versione di `2017-09-21`. L'esempio richiede un'analisi del documento completo e di singole frasi.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

Il seguente comando di esempio è equivalente all'esempio precedente ma utilizza il metodo di richiesta `GET` HTTP:

```bash
curl -X GET -u "apikey:{apikey}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

Per ulteriori esempi, vedi l'[Esercitazione introduttiva](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted).

### Specificare la serie di caratteri
{: #charset}

Per impostazione predefinita, il servizio utilizza le seguenti serie di caratteri per il contenuto di input:

-   *Per il testo semplice e il contenuto HTML,* il servizio utilizza la serie di caratteri International Standards Organization (ISO)-8859-1 (di fatto la serie di caratteri ASCII) per la specifica 1.1 della versione HTTP.
-   *Per il contenuto JSON,* il servizio di fatto utilizza sempre la serie di caratteri Unicode Transformation Format (UTF)-8 per la sezione 8.1 di International Engineering Task Force (IETF) [Request for Comment (RFC) 7159 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

Quando inoltri del testo semplice o del contenuto HTML, includi il parametro `charset` con l'intestazione `Content-Type` per indicare la codifica del carattere del testo di input. Il seguente esempio specifica la codifica del carattere UTF-8 per l'input di testo semplice:

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

Utilizzando il parametro `charset`, puoi evitare i problemi potenziali associati ai caratteri non stampabili o non ASCII. Se passi i dati in UTF-8 senza specificare la serie di caratteri, i caratteri speciali possono provocare risultati non corretti o errori HTTP di livello 400 o 500.

Per evitare errori simili quando utilizzi il comando the `curl`, passa sempre il contenuto tramite l'opzione `--data-binary` del comando `curl` per preservare l'eventuale codifica UTF-8 per il contenuto. Se utilizzi l'opzione `--data` per trasmettere il contenuto come ASCII, il comando può elaborare l'input, che può causare problemi con i dati codificati in UTF-8.

## Specifica dell'input JSON
{: #JSONinput}

Per analizzare l'input JSON con il metodo di richiesta `POST`, passa il metodo a un oggetto `ToneInput` JSON con il seguente formato semplice:

```javascript
{
  "text": ""
}
```
{: codeblock}

Il seguente esempio illustra i contenuti del file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a> utilizzato con gli esempi nell'[Esercitazione introduttiva](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted). Il file include un solo paragrafo di testo scritto da una singola persona. (Il seguente testo include le interruzioni di linea per la leggibilità; non includerle in un input effettivo.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## Contenuto della risposta JSON
{: #JSONresponse-tone}

Il servizio restituisce un oggetto `ToneAnalysis` JSON che contiene sempre un campo `document_tone`. Questo campo contiene un oggetto `DocumentAnalysis` che fornisce l'analisi del documento di input completo. Contiene un solo campo, `tones`, che fornisce i risultati dell'analisi di ogni tono qualificato del documento.

Se il parametro `sentences` della richiesta viene omesso o impostato su `true`, la risposta include anche un campo `sentences_tone`. Questo campo contiene un array di oggetti `SentenceAnalysis`, ognuno dei quali fornisce le seguenti informazioni per una differente frase del contenuto di input:

-   `sentence_id` (numero intero) fornisce l'identificativo univoco della frase. La prima frase ha un ID 0 e l'ID di ogni frase successiva viene incrementato di uno.
-   `text` (stringa) fornisce il testo della frase.
-   `tones` fornisce i risultati dell'analisi di ogni tono qualificato della frase.

Il seguente esempio illustra la struttura di alto livello dell'oggetto `ToneAnalysis`:

```javascript
{
  "document_tone": {
    "tones": [
      . . .
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": {integer},
      "text": "{string}",
      "tones": [
        . . .
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### Risultati punteggio e tono
{: #uttsr}

I campi `tones` restituiti dalle analisi al livello della frase e del documento contengono un array di oggetti `ToneScore` che fornisce i risultati per i toni dominanti. Questi toni hanno dei punteggi di almeno 0.5. L'array è vuoto se nessun tono ha un punteggio che soddisfa questa soglia. Ogni oggetto `ToneScore` fornisce le seguenti informazioni sul tono qualificato:

-   `score` (doppio) è il punteggio del tono nell'intervallo compreso tra 0.5 e 1. Un punteggio maggiore di 0.75 indica un'alta probabilità che il tono sia stato percepito nel contenuto.
-   `tone_id` (stringa) è l'identificativo non localizzato e univoco del tono; per le descrizioni dei toni, consulta [Toni di utilizzo generico](#tones-tone).
-   `tone_name` (stringa) è il nome del tono localizzato e visibile dall'utente.

Il seguente esempio illustra la struttura dell'oggetto `ToneScore`:

```javascript
{
  "tones": [
    {
      "score": {double},
      "tone_id": "{string}",
      "tone_name": "{string}"
    },
    . . .
  ]
}
```
{: codeblock}

### Risposta di esempio
{: #exampleResponse-tone}

Il seguente output viene restituito per le [Richieste di esempio](#exampleRequests). (Lo stesso output viene restituito per il primo esempio nell'[Esercitazione introduttiva](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted).) La risposta include i risultati per il documento completo e per ogni singola frase. Tutti i toni riportati hanno un punteggio di almeno 0.5. I toni con un punteggio di almeno 0.75 è molto probabile che vengano percepiti nel contenuto.

```javascript
{
  "document_tone": {
    "tones": [
      {
        "score": 0.6165,
        "tone_id": "sadness",
        "tone_name": "Sadness"
      },
      {
        "score": 0.829888,
        "tone_id": "analytical",
        "tone_name": "Analytical"
      }
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": 0,
      "text": "Team, I know that times are tough!",
      "tones": [
        {
          "score": 0.801827,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 1,
      "text": "Product sales have been disappointing for the past three quarters.",
      "tones": [
        {
          "score": 0.771241,
          "tone_id": "sadness",
          "tone_name": "Sadness"
        },
        {
          "score": 0.687768,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 2,
      "text": "We have a competitive product, but we need to do a better job of selling it!",
      "tones": [
        {
          "score": 0.506763,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Toni di utilizzo generico
{: #tones-tone}

La seguente tabella descrive i toni di utilizzo generico che può restituire il servizio. Un tono con un punteggio inferiore a 0.5 viene omesso, il che indica che l'emozione non è stata probabilmente percepita nel contenuto. Un punteggio maggiore di 0.75 indica un'alta probabilità che il tono sia percepito.

<table>
  <caption>Tabella 2. Toni di utilizzo generico</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Tono / ID</th>
    <th style="text-align:left">Descrizione</th>
  </tr>
  <tr>
    <td>Rabbia<br/><code>anger</code></td>
    <td>
      La rabbia viene richiamata a causa di ingiustizia, conflitto, umiliazione, negligenza o
      tradimento. Se la rabbia è attiva, l'individuo attacca il bersaglio,
      verbalmente o fisicamente. Se la rabbia è passiva, la persona rimane in silenzio
      e avverte tensione e ostilità. (Un tono emotivo.)
    </td>
  </tr>
  <tr>
    <td>Paura<br/><code>fear</code></td>
    <td>
      La paura è una risposta a un pericolo imminente. È un meccanismo di sopravvivenza che viene
      attivato come una reazione ad alcuni stimoli negativi. La paura può essere una leggera cautela
      o una fobia estrema. (Un tono emotivo.)
    </td>
  </tr>
  <tr>
    <td>Gioia<br/><code>joy</code></td>
    <td>
      La gioia (o felicità) ha sfumature di appagamento, soddisfazione e piacere.
      La gioia porta un senso di benessere, pace interiore, amore, sicurezza e
      contentezza. (Un tono emotivo.)
    </td>
  </tr>
  <tr>
    <td>Tristezza<br/><code>sadness</code></td>
    <td>
      La tristezza indica una sensazione di perdita o disagio. Quando una persona
      è silenziosa, poco energica e introversa, si può dedurre che sta provando
      tristezza. (Un tono emotivo.)
    </td>
  </tr>
  <tr>
    <td>Analitico<br/><code>analytical</code></td>
    <td>
      Un tono analitico indica un'attitudine analitica e ragionevole della persona
      sulle cose. Una persona analitica potrebbe essere percepita come intellettuale,
      razionale, sistematica, impassibile o impersonale. (Un tono linguistico.)
    </td>
  </tr>
  <tr>
    <td>Sicuro<br/><code>confident</code></td>
    <td>
      Un tono sicuro indica un grado di certezza della persona. Una persona sicura
      potrebbe essere percepita come sicura, raccolta, fiduciosa o egocentrica.
      (Un tono linguistico.)
    </td>
  </tr>
  <tr>
    <td>Incerto<br/><code>tentative</code></td>
    <td>
      Un tono incerto indica un grado di inibizione della persona. Una persona incerta
      potrebbe essere percepita come discutibile, dubbiosa o contestabile. (Un
      tono linguistico.)
    </td>
  </tr>
</table>
