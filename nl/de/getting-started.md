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

# Lernprogramm zur Einführung
{: #gettingStarted}

Der Service {{site.data.keyword.toneanalyzershort}} analysiert den Ton des Eingabeinhalts. In diesem Lernprogramm werden Befehle gezeigt, mit denen diverser Beispielinhalt analysiert wird. Die Beispiele veranschaulichen sowohl den Endpunkt für allgemeine Zwecke als auch den Endpunkt für das Kundenengagement.
{: shortdesc}

Im Lernprogramm werden zur Authentifizierung API-Schlüssel von {{site.data.keyword.cloud}} Identity and Access Management (IAM) verwendet. Ältere Serviceinstanzen verwenden möglicherweise weiterhin die Angaben für `{username}` und `{password}` aus den vorhandenen Cloud Foundry-Serviceberechtigungsnachweisen für die Authentifizierung. Führen Sie die Authentifizierung mithilfe der Methode durch, die sich am besten für Ihre Serviceinstanz eignet. Weitere Informationen zur Verwendung der IAM-Authentifizierung im Service finden Sie in den [Releaseinformationen](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
{: important}

## Vorbereitende Schritte
{: #prerequisites}

- {: hide-dashboard}  Erstellen Sie eine Instanz des Service:
    1.  {: hide-dashboard} Rufen Sie die Seite für [{{site.data.keyword.toneanalyzershort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} im Katalog von {{site.data.keyword.cloud_notm}} auf.
    1.  {: hide-dashboard} Registrieren Sie sich für ein kostenloses {{site.data.keyword.cloud_notm}}-Konto oder melden Sie sich an.
    1.  {: hide-dashboard} Klicken Sie auf **Erstellen**.
-   Kopieren Sie die Berechtigungsnachweise für die Authentifizierung in Ihre Serviceinstanz:
    1.  {: hide-dashboard} Klicken Sie im [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/dashboard/apps){: new_window} auf die Instanz des Service {{site.data.keyword.toneanalyzershort}}, um die Seite für das Dashboard des Service {{site.data.keyword.toneanalyzershort}} aufzurufen.
    1.  Klicken Sie auf der Seite **Verwalten** auf **Anzeigen**, um Ihre Berechtigungsnachweise anzuzeigen.
    1.  Kopieren Sie die Werte für `API-Schlüssel` und `URL`.
-   Vergewissern Sie sich, dass der Befehl `curl` verfügbar ist.
    -   In den Beispielen wird zum Aufrufen von Methoden der HTTP-Schnittstelle der Befehl `curl` verwendet. Installieren Sie die für Ihr Betriebssystem geeignete Version von [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Installieren Sie die Version, die das Protokoll SSL (Secure Sockets Layer) unterstützt. Achten Sie darauf, die Binärdatei für die Installation in Ihre Umgebungsvariable `PATH` einzuschließen.

Wenn Sie einen Befehl eingeben, ersetzen Sie `{apikey}` und `{url}` durch den tatsächlichen API-Schlüssel und die URL. Die geschweiften Klammern, die einen Variablenwert angeben, dürfen im Befehl nicht angegeben werden. Im folgenden Beispiel ist ein tatsächlicher Wert angegeben:
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## Schritt 1: Endpunkt für allgemeine Zwecke über POST-Anforderungsmethode verwenden
{: #generalPurposePost}

Mit den folgenden Befehlen wird die Methode `POST /v3/tone` aufgerufen, um den Inhalt der Datei `tone.json` zu analysieren. Die Datei enthält einen einzigen, in Klartext erstellten Absatz, der von einer einzigen Person verfasst wird. Die Beispiele veranschaulichen die Abfrageparameter der Methode `sentences`.

1.  Laden Sie die Beispieldatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> herunter.
1.  Setzen Sie den folgenden Befehl ab, um den Ton des gesamten Inhalts und jedes einzelnen Satzes zu analysieren.
    -   {: hide-dashboard} Ersetzen Sie `{apikey}` und `{url}` durch die eigenen Informationen.
    -   Ändern Sie `{path_to_file}` so, dass die Speicherposition der Datei `tone.json` angegeben wird.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  Setzen Sie den folgenden Befehl ab, um nur den Ton des gesamten Inhalts zu analysieren, indem Sie den Parameter `sentences` auf `false` setzen.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

Ein Beispiel für die Ausgabe dieser Methode finden Sie im Abschnitt [Beispielantwort](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone).

## Schritt 2: Endpunkt für allgemeine Zwecke über GET-Anforderungsmethode verwenden
{: #generalPurposeGet}

Die Schnittstelle enthält auch eine Methode namens `GET /v3/tone`. Die Methode `GET` stellt dieselbe Funktionalität wie `POST` bereit und erzeugt dieselben Ergebnisse, aber mit dem Abfrageparameter `text` der Methode geben Sie den zu analysierenden Inhalt an. Die Methode akzeptiert nur Eingaben in Klartext.

1.  Im folgenden Beispiel wird der Text der Datei `tone.json` mit dem Parameter `text` angegeben. Wie nachstehend dargestellt, müssen Sie den Text in URL codieren. Da bei dem Befehl der Parameter `sentences` weggelassen wird, gibt er dieselbe Ausgabe wie das zuvor gezeigte erste Beispiel mit `POST` zurück. (Zur besseren Lesbarkeit enthält das Beispiel Zeilenumbrüche, die Sie jedoch nicht in einen echten Befehl einbauen dürfen.)

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## Schritt 3: Endpunkt für das Kundenengagement verwenden
{: #customerEngagement}

Mit dem folgenden Befehl wird die Methode `POST /v3/tone_chat` aufgerufen, um den Inhalt der Datei `tone-chat.json` zu analysieren. Die Datei enthält einen kurzen Nachrichtenaustausch zwischen zwei Personen, einem Kunden (<code>customer</code>) und einem Mitarbeiter (<code>agent</code>).

1.  Laden Sie die Beispieldatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> herunter.
1.  Setzen Sie den folgenden Befehl ab, um den Ton des Austauschs in der Beispieldatei zu analysieren.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

Die Serviceantwort zeigt die häufigsten Töne an, die für die einzelnen Äußerungen der Eingabe erkannt wurden. Sie können den Inhalt der Antwort auf diese Anforderung im Abschnitt [Beispielantwort](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat) einsehen.

## Nächste Schritte
{: #gsns}

-   Weitere Informationen zur Methode `/v3/tone` finden Sie im Abschnitt [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe).
-   Weitere Informationen zur Methode `/v3/tone_chat` finden Sie im Abschnitt [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer?topic=tone-analyzer-utco).
-   Weitere Informationen zu den Methoden der Serviceschnittstelle finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
