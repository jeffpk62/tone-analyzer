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

# Lernprogramm zur Einführung

Der Service {{site.data.keyword.toneanalyzershort}} analysiert den Ton des Eingabeinhalts. In diesem Lernprogramm werden Befehle gezeigt, mit denen diverser Beispielinhalt analysiert wird. Die Beispiele veranschaulichen sowohl den Endpunkt für allgemeine Zwecke als auch den Endpunkt für Kundenengagement.
{: shortdesc}

## Vorbereitende Schritte
{: #prerequisites}

- Erstellen Sie eine Instanz des Service:
    - {: download} Wenn Sie dies sehen, haben Sie Ihre Serviceinstanz erstellt. Rufen Sie nun Ihre Berechtigungsnachweise ab.
    - Erstellen Sie über einen Service ein Projekt:
        1.  Rufen Sie in der {{site.data.keyword.watson}}-Entwicklerkonsole die Seite [Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/developer/watson/services){: new_window} auf.
        1.  Wählen Sie {{site.data.keyword.toneanalyzershort}} aus, klicken Sie auf **Services hinzufügen** und erstellen Sie entweder ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
        1.  Geben Sie `tone-tutorial` als Projektnamen ein und klicken Sie auf **Projekt erstellen**.
- Kopieren Sie die Berechtigungsnachweise für die Authentifizierung in Ihre Serviceinstanz:
    - {: download} Gehen Sie im Servicedashboard (welches Sie vor sich sehen) wie folgt vor:
        1.  Klicken Sie auf die Registerkarte **Serviceberechtigungsnachweise**.
        1.  Klicken Sie im Bereich **Aktionen** auf **Berechtigungsnachweise anzeigen**.
        1.  Kopieren Sie die Werte für `username`, `password` und `url`.
        {: download}
    - Kopieren Sie über Ihr Projekt **tone-tutorial** in der Entwicklerkonsole die `username`-, `password`- und `url`-Werte für `"tone_analyzer"` aus dem Bereich **Berechtigungsnachweise**.
- Stellen Sie sicher, dass Sie cURL haben:
    - In den Beispielen wird cURL zum Aufrufen von Methoden der HTTP-Schnittstelle verwendet. Installieren Sie die für Ihr Betriebssystem geeignete Version von [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Installieren Sie die Version, die das Protokoll SSL (Secure Sockets Layer) unterstützt. Achten Sie darauf, die Binärdatei für die Installation in Ihre Umgebungsvariable `PATH` einzuschließen.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Erstellen Sie bei Verwendung von {{site.data.keyword.Bluemix_dedicated_notm}} Ihre Serviceinstanz über die Seite [{{site.data.keyword.toneanalyzershort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} im Katalog. Detaillierte Informationen dazu, wie Ihre Serviceberechtigungsnachweise zu finden sind, finden Sie unter [Serviceberechtigungsnachweise für Watson-Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Schritt 1: Endpunkt für allgemeine Zwecke über POST-Anforderungsmethode verwenden
{: #generalPurposePost}

Mit den folgenden Befehlen wird die Methode `POST /v3/tone` aufgerufen, um den Inhalt der Datei `tone.json` zu analysieren. Die Datei enthält einen einzigen, in Klartext erstellten Absatz, der von einer einzigen Person verfasst ist. Die Beispiele veranschaulichen die Abfrageparameter der Methode `sentences`.

1.  Laden Sie die Beispieldatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Setzen Sie den folgenden Befehl ab, um den Ton des gesamten Inhalts und jedes einzelnen Satzes zu analysieren.
    -   Ersetzen Sie `{username}` und `{password}` durch Ihre Serviceberechtigungsnachweise aus dem vorherigen Schritt.
    -   Ändern Sie `{path_to_file}` so, dass die Speicherposition der Datei `tone.json` angegeben wird.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Setzen Sie den folgenden Befehl ab, um nur den Ton des gesamten Inhalts zu analysieren, indem Sie den Parameter `sentences` auf `false` setzen.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

Ein Beispiel für die Ausgabe dieser Methode finden Sie im Abschnitt [Beispielantwort](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Schritt 2: Endpunkt für allgemeine Zwecke über GET-Anforderungsmethode verwenden
{: #generalPurposeGet}

Die Schnittstelle enthält auch eine Methode namens `GET /v3/tone`. Die Methode `GET` stellt dieselbe Funktionalität wie `POST` bereit und erzeugt dieselben Ergebnisse, aber mit dem Abfrageparameter `text` der Methode geben Sie den zu analysierenden Inhalt an. Die Methode akzeptiert nur Eingaben in Klartext.

1.  Im folgenden Beispiel wird der Text der Datei `tone.json` mit dem Parameter `text` angegeben. Wie nachstehend dargestellt, müssen Sie den Text in URL codieren. Da bei dem Befehl der Parameter `sentences` weggelassen wird, gibt er dieselbe Ausgabe wie das zuvor gezeigte erste Beispiel mit `POST` zurück. (Zur besseren Lesbarkeit enthält das Beispiel Zeilenumbrüche, die Sie jedoch nicht in einen echten Befehl einbauen dürfen.)

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Schritt 3: Endpunkt für Kundenengagement verwenden
{: #customerEngagement}

Mit dem folgenden Befehl wird die Methode `POST /v3/tone_chat` aufgerufen, um den Inhalt der Datei `tone-chat.json` zu analysieren. Die Datei enthält einen kurzen Nachrichtenaustausch zwischen zwei Personen, einem Kunden (<code>customer</code>) und einem Mitarbeiter (<code>agent</code>).

1.  Laden Sie die Beispieldatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> herunter.
1.  Setzen Sie den folgenden Befehl ab, um den Ton des Austauschs in der Beispieldatei zu analysieren.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

Die Serviceantwort zeigt die häufigsten Töne an, die für die einzelnen Äußerungen der Eingabe erkannt wurden. Sie können den Inhalt der Antwort auf diese Anforderung im Abschnitt [Beispielantwort](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse) einsehen.

## Nächste Schritte

-   Weitere Informationen zur Methode `/v3/tone` finden Sie im Abschnitt [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer/using-tone.html).
-   Weitere Informationen zur Methode `/v3/tone_chat` finden Sie im Abschnitt [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer/using-tone-chat.html).
-   Detaillierte Informationen zu den Methoden der Serviceschnittstelle finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Im [API Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window} können Sie mit der API interagieren.
