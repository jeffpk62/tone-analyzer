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
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Esercitazione introduttiva
{: #gettingStarted}

Il servizio {{site.data.keyword.toneanalyzershort}} analizza il tono del contenuto di input. Questa esercitazione mostra i comandi che analizzano diverso contenuto di esempio. Gli esempi illustrano sia gli endpoint di utilizzo generico sia quelli di coinvolgimento del cliente.
{: shortdesc}

L'esercitazione utilizza le chiavi API {{site.data.keyword.cloud}} IAM (Identity and Access Management) per l'autenticazione. Le istanze del servizio meno recenti potrebbero continuare a utilizzare `{username}` e `{password}` dalle loro credenziali del servizio Cloud Foundry esistenti per l'autenticazione. Esegui l'autenticazione utilizzando l'approccio corretto per la tua istanza del servizio. Per ulteriori informazioni sull'utilizzo da parte del servizio dell'autenticazione IAM, vedi le [Note sulla release](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
{: important}

## Prima di cominciare
{: #prerequisites}

- {: hide-dashboard}  Crea una istanza del servizio:
    1.  {: hide-dashboard} Vai alla pagina [{{site.data.keyword.toneanalyzershort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} nel catalogo {{site.data.keyword.cloud_notm}}.
    1.  {: hide-dashboard} Registrati per un account {{site.data.keyword.cloud_notm}} gratuito o accedi.
    1.  {: hide-dashboard} Fai clic su **Crea**.
-   Copia le credenziali per autenticarti con la tua istanza del servizio:
    1.  {: hide-dashboard} Dal dashboard [{{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/dashboard/apps){: new_window}, fai clic sulla tua istanza del servizio {{site.data.keyword.toneanalyzershort}} per andare alla pagina del dashboard del servizio {{site.data.keyword.toneanalyzershort}}.
    1.  Nella pagina **Gestisci**, fai clic su **Mostra** per visualizzare le tue credenziali.
    1.  Copia i valori `API Key` e `URL`.
-   Assicurati di avere il comando `curl`.
    -   Gli esempi utilizzano il comando `curl` per richiamare i metodi dell'interfaccia HTTP. Installa la versione per il tuo sistema operativo da [curl.haxx.se ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://curl.haxx.se/){: new_window}. Installa la versione che supporta il protocollo SSH (Secure Sockets Layer). Assicurati di includere il file binario installato nella tua variabile di ambiente `PATH`.

Quando immetti un comando, sostituisci `{apikey}` e `{url}` con la tua chiave API e il tuo URL effettivi. Ometti le parentesi graffe, che indicano un valore variabile, nel comando. Un valore effettivo è simile al seguente esempio:
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## Passo 1: utilizzo dell'endpoint di utilizzo generico tramite il metodo di richiesta POST.
{: #generalPurposePost}

I seguenti comandi richiamano il metodo `POST /v3/tone` per analizzare i contenuti del file `tone.json`. Il file include un singolo paragrafo di testo semplice scritto da una sola persona. Gli esempi illustrano i parametri di query `sentences` del metodo.

1.  Scarica il file di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>.
1.  Immetti il seguente comando per analizzare il tono del contenuto generale di ogni singola frase.
    -   {: hide-dashboard} Sostituisci `{apikey}` e `{url}` con le tue informazioni.
    -   Modifica `{path_to_file}` per specificare l'ubicazione del file `tone.json`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  Immetti il seguente comando per analizzare il tono del contenuto generale solo impostando il parametro `sentences` su `false`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

Per un esempio dell'output del metodo, consulta [Risposta di esempio](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone).

## Passo 2: utilizzo dell'endpoint di utilizzo generico tramite il metodo di richiesta GET.
{: #generalPurposeGet}

L'interfaccia offre inoltre un metodo `GET /v3/tone`. Il metodo `GET` fornisce la stessa funzionalità e produce gli stessi risultati del metodo `POST`, ma utilizzi il parametro di query `text` del metodo per specificare il contenuto che deve essere analizzato. Il metodo accetta solo input di testo semplice.

1.  Il seguente esempio specifica il testo del file `tone.json` tramite il parametro `text`; come mostrato, devi codificare tramite URL il testo. Il comando omette il parametro `sentences`, per cui restituisce lo stesso output del primo esempio `POST` mostrato in precedenza. (L'esempio include le interruzioni di linea per la leggibilità; non includerle in un comando effettivo.)

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## Passo 3: Utilizzo dell'endpoint di coinvolgimento del cliente
{: #customerEngagement}

Il seguente comando richiama il metodo `POST /v3/tone_chat` per analizzare i contenuti del file `tone-chat.json`. Il file include un breve scambio di messaggi tra due persone, un <code>customer</code> e un <code>agent</code>.

1.  Scarica il file di esempio <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icona link esterno" title="Icona link esterno"></a>.
1.  Immetti il seguente comando per analizzare il tono dello scambio nel file di esempio. 

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

La risposta del servizio indica i toni più diffusi individuati per ogni affermazione dell'input. Per visualizzare il contenuto della risposta di questa richiesta, consulta [Risposta di esempio](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat).

## Passi successivi
{: #gsns}

-   Per ulteriori informazioni sul metodo `/v3/tone`, consulta [Utilizzo dell'endpoint di utilizzo generico](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe).
-   Per ulteriori informazioni sul metodo `/v3/tone_chat`, consulta [Utilizzo dell'endpoint di coinvolgimento del cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco).
-   Per ulteriori informazioni sui metodi dell'interfaccia del servizio, consulta [API reference ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
