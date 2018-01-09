---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Esercitazione introduttiva

Il servizio {{site.data.keyword.toneanalyzershort}} analizza il tono del contenuto di input. Questa esercitazione mostra i comandi che analizzano diverso contenuto di esempio. Gli esempi illustrano gli endpoint di utilizzo generico e di coinvolgimento del cliente.
{: shortdesc}

## Prima di cominciare
{: #prerequisites}

- Crea un'istanza del servizio:
    - {: download} Se stai visualizzando questo, hai creato la tua istanza del servizio. Ora ottieni le tue credenziali. 
    - Crea un progetto da un servizio: 
        1.  Vai alla pagina {{site.data.keyword.watson}} Developer Console [Services ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/developer/watson/services){: new_window}. 
        1.  Seleziona {{site.data.keyword.toneanalyzershort}}, fai clic su **Add Services** e registrati per un account gratuito di {{site.data.keyword.Bluemix_notm}} o accedi.
        1.  Immetti `tone-tutorial` come nome del progetto e fai clic su **Create Project**.
- Copia le credenziali per autenticarti con la tua istanza del servizio: 
    - {: download} Dal dashboard del servizio (che stai guardando): 
        1.  Fai clic sulla scheda **Service credentials**. 
        1.  Fai clic su **View credentials** in **Actions**. 
        1.  Copia i valori `username`, `password` e `url`.
        {: download}
    - Dal tuo progetto **tone-tutorial** nella Developer Console, copia i valori `username`,  `password` e `url` per `"tone_analyzer"` dalla sezione **Credentials**.
- Assicurati di avere cURL: 
    - Gli esempi utilizzano cURL per richiamare i metodi dell'interfaccia HTTP. Installa la versione per il tuo sistema operativo da [curl.haxx.se ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://curl.haxx.se/){: new_window}. Installa la versione che supporta il protocollo SSH (Secure Sockets Layer). Assicurati di includere il file binario installato nella tua variabile di ambiente `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se utilizzi {{site.data.keyword.Bluemix_dedicated_notm}}, crea la tua istanza del servizio dalla pagina [{{site.data.keyword.toneanalyzershort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} nel catalogo. Per i dettagli su come trovare le tue credenziali del servizio, consulta [Credenziali del servizio per i servizi Watson ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}. 

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Passo 1: utilizza l'endpoint di utilizzo generico tramite il metodo di richiesta POST.
{: #generalPurposePost}

I seguenti comandi richiamano il metodo `POST /v3/tone` per analizzare i contenuti del file `tone.json`. Il file include un solo paragrafo di testo semplice scritto da una persona. Gli esempi illustrano i parametri di query `sentences` del metodo.

1.  Scarica il file di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Immetti il seguente comando per analizzare il tono del contenuto generale di ogni singola frase.
    -   Sostituisci `{username}` e `{password}` con le tue credenziali del servizio dal passo precedente.
    -   Modifica `{path_to_file}` per specificare l'ubicazione del file `tone.json`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Immetti il seguente comando per analizzare il tono del contenuto generale solo impostando il parametro `sentences` su `false`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

Per un esempio dell'output del metodo, consulta [Risposta di esempio](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Passo 2: utilizza l'endpoint di utilizzo generico tramite il metodo di richiesta GET.
{: #generalPurposeGet}

L'interfaccia offre inoltre un metodo `GET /v3/tone`. Il metodo `GET` fornisce la stessa funzionalità e produce gli stessi risultati del metodo `POST`, ma utilizzi il parametro di query `text` del metodo per specificare il contenuto che deve essere analizzato. Il metodo accetta solo input di testo semplice.

1.  Il seguente esempio specifica il testo del file `tone.json` tramite il parametro `text`; come mostrato, devi codificare tramite URL il testo. Il comando omette il parametro `sentences`, per cui restituisce lo stesso output del primo esempio `POST` mostrato in precedenza. (L'esempio include le interruzioni di linea per la leggibilità; non includerle in un comando effettivo.)

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Passo 3: utilizza l'endpoint di coinvolgimento del cliente
{: #customerEngagement}

Il seguente comando richiama il metodo `POST /v3/tone_chat` per analizzare i contenuti del file `tone-chat.json`. Il file include un breve scambio di messaggi tra due persone, un <code>customer</code> e un <code>agent</code>.

1.  Scarica il file di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno" class="style-scope doc-content"></a>.
1.  Immetti il seguente comando per analizzare il tono dello scambio nel file di esempio. 

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

La risposta del servizio indica i toni più diffusi individuati per ogni affermazione dell'input. Per visualizzare il contenuto della risposta di questa richiesta, consulta [Risposta di esempio](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Passi successivi

-   Per ulteriori informazioni sul metodo `/v3/tone`, consulta [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer/using-tone.html).
-   Per ulteriori informazioni sul metodo `/v3/tone_chat`, consulta [Utilizzo dell'endpoint di coinvolgimento cliente](/docs/services/tone-analyzer/using-tone-chat.html).
-   Per informazioni dettagliate sui metodi dell'interfaccia del servizio, consulta [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Interagisci con l'API in [API explorer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}.
