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

# Endpunkt für Kundenengagement verwenden
{: #utco}

Mit dem Endpunkt für das Kundenengagement von {{site.data.keyword.toneanalyzershort}} wird der Ton von Konversationen des Kundenservice und der Kundenunterstützung analysiert. Er kann dazu beitragen, dass Sie Ihre Interaktionen mit Kunden besser verstehen und Ihre Kommunikation insgesamt oder mit bestimmten Kunden verbessern. Weitere Informationen zu der Schnittstelle, einschließlich der für den Aufruf des Service verfügbaren Node.js-, Java- und Python-SDKs, finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
{: shortdesc}

Die Anforderungsprotokollierung ist für den Service {{site.data.keyword.toneanalyzershort}} inaktiviert. Unabhängig davon, ob der Anforderungsheader `X-Watson-Learning-Opt-Out` definiert wurde, protokolliert der Service die Daten von Anforderungen und der entsprechenden Antworten nicht und bewahrt diese Daten auch nicht auf.
{: note}

## Tonanalyse anfordern
{: #request-tone-chat}

Zur Tonanalyse mit dem Endpunkt für das Kundenengagement rufen Sie die Methode `POST /v3/tone_chat` mit den folgenden Parametern auf.

<table>
  <caption>Tabelle 1. Parameter der Methode <code>POST /v3/tone_chat</code></caption>
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
      Ein JSON-Objekt <code>ToneChatInput</code>, das den zu analysierenden
      Inhalt enthält. Weitere Informationen hierzu finden Sie in
      [JSON-Eingabe angeben](#JSONrequest).
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Erforderlich</em></td>
    <td style="text-align:center">Abfrage</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die Version der API, die Sie als Datum im Format
      <code>JJJJ-MM-TT</code> verwenden wollen; Beispiel: Geben Sie <code>2017-09-21</code>
      für den 21. September 2017 (aktuellste Version) an. Weitere Informationen zu allen
      verfügbaren Versionen finden Sie in den
      [Releaseinformationen](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Optional</em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die Sprache des Eingabeinhalts.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (Englisch, die Standardeinstellung)
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code> (Französisch)
        </li>
      </ul>
      Regionale Varianten werden als deren übergeordnete Sprache aufgefasst. Beispielsweise
      wird <code>en-US</code> als <code>en</code> interpretiert. Der Eingabeinhalt
      muss der angegebenen Sprache entsprechen. Übergeben Sie keinen Inhalt, der
      beide Sprachen enthält. Sie können verschiedene Sprachen für die Eingabe und
      die Antwort verwenden.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Optional</em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die angeforderte Sprache der Antwort.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code> (Arabisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>de</code> (Deutsch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code> (Englisch, die Standardeinstellung)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code> (Spanisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (Französisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>it</code> (Italienisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code> (Japanisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code> (Koreanisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code> (Brasilianisches Portugiesisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code> (Vereinfachtes Chinesisch)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code> (Traditionelles Chinesisch)
        </li>
      </ul>
      Bei Argumenten, die aus zwei Zeichen bestehen, werden regionale Varianten als
      deren übergeordnete Sprache aufgefasst. Beispielsweise wird <code>en-US</code> als
      <code>en</code> interpretiert. Sie können verschiedene Sprachen für die Eingabe und
      die Antwort verwenden.
    </td>
  </tr>
</table>

Wenn Sie mehr als 50 Äußerungen übergeben, gibt der Service auf der Ebene `warning` seiner Antwort ein Feld `warning` für den Gesamtinhalt zurück. Er analysiert nur die ersten 50 Äußerungen. Wenn Sie eine einzelne Äußerung übergeben, die mehr als 500 Zeichen enthält, gibt der Service ein Feld `error` für diese Äußerung zurück und analysiert sie nicht. In beiden Fällen ist die Anforderung dennoch mit dem HTTP-Antwortcode 200 erfolgreich.

Der Service gibt den Antwortcode 400 zurück, wenn alle Äußerungen der Eingabe mehr als 500 Zeichen aufweisen.
{: note}

### Beispielanforderung
{: #exampleRequest}

Der folgende Beispielbefehl `curl` ruft den Endpunkt für das Kundenengagement mit der Eingabedatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a> und der Version `2017-09-21` auf:

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## JSON-Eingabe angeben
{: #JSONrequest}

Sie übergeben an die Methode ein JSON-Objekt namens `ToneChatInput` im folgenden Format. Im Feld `utterances` ist ein Array mit `utterance`-Objekten angegeben. Das Feld `text` enthält die erforderliche Zeichenfolge, die eine Äußerung angibt, die von einem Benutzer zu der zu analysierenden Konversation beigetragen wurde. Im Feld `user` ist eine optionale Zeichenfolge enthalten, die den Benutzer identifiziert, der die Äußerung beigetragen hat.

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

Das folgende Beispiel zeigt den Inhalt der Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link"></a>. Die Datei enthält einen kurzen Austausch zwischen einem Kunden (<code>customer</code>) und einem Mitarbeiter (<code>agent</code>).

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
{: #JSONresponse-tone-chat}

Der Service gibt das JSON-Objekt `UtteranceAnalyses` zurück, das als einziges Feld `utterances_tone` enthält. Dieses Feld enthält ein Array von `UtteranceAnalysis`-Objekten, von denen jedes die folgenden Informationen zu einer Äußerung aus dem Eingabeinhalt bereitstellt:

-   `utterance_id` (Ganzzahl) stellt die eindeutige ID für die Äußerung bereit. Die erste Äußerung hat die ID 0 und die ID jeder nachfolgenden Äußerung wird um einen Schritt erhöht.
-   `utterance_text` (Zeichenfolge) stellt den Text der Äußerung bereit.
-   `tones` ist ein Array von `ToneChatScore`-Objekten, das Ergebnisse zu den vorherrschenden Tönen bereitstellt. Diese Töne verfügen über Bewertungen mit einem Wert von mindestens 0,5. Wenn die Äußerung keinen Ton mit einer Bewertung hat, die diesem Schwellenwert entspricht, ist das Array leer.

Jedes `ToneChatScore`-Objekt stellt die folgenden Informationen zu einem qualifizierenden Ton bereit:

-   `score` (Doppelbyte) ist der Wert für den Ton im Bereich von 0,5 bis 1. Ein Wert größer als 0,75 gibt an, dass der Ton mit großer Wahrscheinlichkeit in der Äußerung wahrgenommen wird.
-   `tone_id` (Zeichenfolge) ist eine eindeutige, nicht lokalisierte ID für den Ton. Beschreibungen der Töne finden Sie im Abschnitt [Töne für das Kundenengagement](#tones-tone-chat).
-   `tone_name` (Zeichenfolge) ist der für den Benutzer sichtbare, lokalisierte Name des Tons.

Das folgende Beispiel zeigt die Struktur des Objekts `UtteranceAnalyses`:

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
{: #exampleResponse-tone-chat}

Die folgende Ausgabe wird für die [Beispielanforderung](#exampleRequest) zurückgegeben. (Dieselbe Ausgabe wird für das Beispiel im [Lernprogramm zur Einführung](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted#customerEngagement) zurückgegeben). Alle berichteten Töne haben eine Bewertung von mindestens 0,5. Töne mit einer Bewertung von mindestens 0,75 werden mit großer Wahrscheinlichkeit von den Teilnehmern der Konversation wahrgenommen.

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

## Töne für das Kundenengagement
{: #tones-tone-chat}

Der Service kann Bewertungen für die folgenden sieben Töne zurückgeben.

<table style="width:90%">
  <caption>Tabelle 2. Töne für das Kundenengagement</caption>
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
