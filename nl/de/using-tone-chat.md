---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-28"

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

# Endpunkt für Kundenengagement verwenden

Mit dem Endpunkt für Kundenengagement von {{site.data.keyword.toneanalyzershort}} wird der Ton von Konversationen des Kundenservice und der Kundenunterstützung analysiert. Er kann dazu beitragen, dass Sie Ihre Interaktionen mit Kunden besser verstehen und Ihre Kommunikation insgesamt oder mit bestimmten Kunden verbessern. Detaillierte Informationen zu der Schnittstelle, einschließlich der für den Aufruf des Service verfügbaren Node.js, Java und Python SDKs, finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Tonanalyse anfordern
{: #request}

Zur Tonanalyse mit dem Endpunkt für Kundenengagement rufen Sie die Methode `POST /v3/tone_chat` mit den folgenden Parametern auf.

<table>
  <caption>Tabelle 1. Parameter der Methode <code>POST /v3/tone_chat</code>
</caption>
  <tr>
    <th style="text-align:left; width:20%">Parameter</th>
    <th style="text-align:center; width:12%">Typ</th>
    <th style="text-align:center; width:20%">Datentyp</th>
    <th style="text-align:left">Beschreibung</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Erforderlich</em></td>
    <td style="text-align:center">Hauptteil</td>
    <td style="text-align:center">JSON-Objekt</td>
    <td>
      Ein JSON-Objekt namens <code>ToneChatInput</code>, das den Inhalt enthält, der analysiert
      werden soll. Weitere Informationen finden Sie im Abschnitt <a href="#JSONrequest">JSON-Eingabe angeben</a>.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Erforderlich</em></td>
    <td style="text-align:center">Abfrage</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die angeforderte Version der Schnittstelle als Datum im Format
      <code>JJJJ-MM-TT</code>. Geben Sie z. B. <code>2017-09-21</code>
      für den 21. September 2017 an.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Optional</em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die gewünschte Sprache der Antwort:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (Arabisch)
        </li>
        <li style="margin:0px; padding:0px">
          de (Deutsch)
        </li>
        <li style="margin:0px; padding:0px">
          en (Englisch, die Standardeinstellung)
        </li>
        <li style="margin:0px; padding:0px">
          es (Spanisch)
        </li>
        <li style="margin:0px; padding:0px">
          fr (Französisch)
        </li>
        <li style="margin:0px; padding:0px">
          it (Italienisch)
        </li>
        <li style="margin:0px; padding:0px">
          ja (Japanisch)
        </li>
        <li style="margin:0px; padding:0px">
          ko (Koreanisch)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (Portugiesisch (Brasilien))
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (Vereinfachtes Chinesisch)
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (Traditionelles Chinesisch)
        </li>
      </ul>
    </td>
  </tr>
</table>

Wenn Sie mehr als 50 Äußerungen übergeben, gibt der Service auf der Ebene `warning` seiner Antwort ein Feld `warning` für den Gesamtinhalt zurück. Er analysiert nur die ersten 50 Äußerungen. Wenn Sie eine einzelne Äußerung übergeben, die mehr als 500 Zeichen enthält, gibt der Service ein Feld `error` für diese Äußerung zurück und analysiert sie nicht. In beiden Fällen ist die Anforderung dennoch mit dem HTTP-Antwortcode 200 erfolgreich.

> **Hinweis:** Der Service gibt den Antwortcode 400 zurück, wenn alle Äußerungen der Eingabe mehr als 500 Zeichen aufweisen.

### Beispielanforderung
{: #exampleRequest}

Der folgende cURL-Beispielbefehl ruft den Endpunkt für Kundenengagement mit der Eingabedatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> und der Version `2017-09-21` auf:

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## JSON-Eingabe angeben
{: #JSONrequest}

Sie übergeben an die Methode ein JSON-Objekt namens `ToneChatInput` im folgenden Format. Das Feld `utterances` stellt ein Array von `utterance`-Objekten bereit. Dabei ist `text` eine erforderliche Zeichenfolge, mit der eine Äußerung, die ein Benutzer in der zu analysierenden Konversation gemacht hat, bereitgestellt wird, und `user` ist eine optionale Zeichenfolge, die den Benutzer angibt, der die Äußerung gemacht hat.

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

Das folgende Beispiel zeigt den Inhalt der Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a>. Die Datei enthält einen kurzen Austausch zwischen einem Kunden (<code>customer</code>) und einem Mitarbeiter (<code>agent</code>).

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

## Inhalt von JSON-Antworten
{: #JSONresponse}

Der Service gibt das JSON-Objekt `UtteranceAnalyses` zurück, das als einziges Feld `utterances_tone` enthält. Dieses Feld enthält ein Array von `UtteranceAnalysis`-Objekten, von denen jedes die folgenden Informationen zu einer Äußerung aus dem Eingabeinhalt bereitstellt:

-   `utterance_id` (Ganzzahl) stellt die eindeutige ID für die Äußerung bereit. Die erste Äußerung hat die ID 0 und die ID jeder nachfolgenden Äußerung wird um einen Schritt erhöht.
-   `utterance_text` (Zeichenfolge) stellt den Text der Äußerung bereit.
-   `tones` ist ein Array von `ToneChatScore`-Objekten, die Ergebnisse zu den vorherrschenden Tönen bereitstellen, deren Wert mindestens 0,5 beträgt. Wenn die Äußerung keinen Ton mit einer Bewertung hat, die diesem Schwellenwert entspricht, ist das Array leer. 

Jedes `ToneChatScore`-Objekt stellt die folgenden Informationen zu einem qualifizierenden Ton bereit:

-   `score` (Doppelbyte) ist der Wert für den Ton im Bereich von 0,5 bis 1. Ein Wert größer als 0,75 gibt an, dass der Ton mit großer Wahrscheinlichkeit in der Äußerung wahrgenommen wird.
-   `tone_id` (Zeichenfolge) ist eine eindeutige, nicht lokalisierte ID für den Ton. Beschreibungen der Töne finden Sie im Abschnitt [Töne für Kundenengagement](#tones).
-   `tone_name` (Zeichenfolge) ist der für den Benutzer sichtbare, lokalisierte Name des Tons.

Das folgende Beispiel zeigt die Struktur des Objekts `UtterancesAnalyses`:

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

### Beispielantwort
{: #exampleResponse}

Die folgende Ausgabe wird für die [Beispielanforderung](#exampleRequest) zurückgegeben. (Dieselbe Ausgabe wird für das Beispiel im [Lernprogramm zur Einführung](/docs/services/tone-analyzer/getting-started.html#customerEngagement) zurückgegeben). Alle berichteten Töne haben einen Wert von mindestens 0,5. Töne mit einem Wert von mindestens 0,75 werden mit großer Wahrscheinlichkeit von den Teilnehmern der Konversation wahrgenommen.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.718352,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": []
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997149,
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
          "score": 0.689109,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.663203,
          "tone_id": "sympathetic",
          "tone_name": "Sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Töne für Kundenengagement
{: #tones}

Der Service kann Bewertungen für die folgenden sieben Töne zurückgeben.

<table style="width:90%">
  <caption>Tabelle 2. Töne für Kundenengagement</caption>
  <tr>
    <th style="text-align:left; width:20%">Ton / ID</th>
    <th style="text-align:left">Beschreibung</th>
  </tr>
  <tr>
    <td>Begeistert<br/><code>excited</code></td>
    <td>
      Zeigt persönlichen Enthusiasmus und Interesse
    </td>
  </tr>
  <tr>
    <td>Frustriert<br/><code>frustrated</code></td>
    <td>
      Definiert als verärgert und reizbar
    </td>
  </tr>
  <tr>
    <td>Unhöflich<br/><code>impolite</code></td>
    <td>
      Respektlos und grob
    </td>
  </tr>
  <tr>
    <td>Höflich<br/><code>polite</code></td>
    <td>
      Definiert als rationales, zielorientiertes Verhalten
    </td>
  </tr>
  <tr>
    <td>Traurig<br/><code>sad</code></td>
    <td>
      Wird als unangenehme passive Emotion betrachtet
    </td>
  </tr>
  <tr>
    <td>Zufrieden<br/><code>satisfied</code></td>
    <td>
      Eine affektbetonte Antwort auf eine gefühlte Servicequalität
    </td>
  </tr>
  <tr>
    <td>Mitfühlend<br/><code>sympathetic</code></td>
    <td>
      Eine affektbetonte Art von Verständnis, die eine emotionale Resonanz beinhaltet
    </td>
  </tr>
</table>
