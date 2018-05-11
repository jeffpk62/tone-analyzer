---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-21"

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

# Endpunkt für allgemeine Zwecke verwenden

Der Endpunkt für allgemeine Zwecke von {{site.data.keyword.toneanalyzershort}} analysiert den Ton schriftlicher Kommunikation, von kurzen E-Mail-Nachrichten bis hin zu langen Dokumenten. Er kann Ihnen das Verständnis der emotionalen und der Sprachtöne Ihrer Kommunikation erleichtern. Detaillierte Informationen zu der Schnittstelle, einschließlich der für den Aufruf des Service verfügbaren Node.js, Java und Python SDKs, finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Tonanalyse anfordern
{: #request}

Zur Analyse von Tönen mit dem Endpunkt für allgemeine Zwecke können Sie eine von zwei Methoden `tone` des Service aufrufen:

-   Die Methode `POST /v3/tone` akzeptiert Eingabeinhalt in JSON, Klartext oder HTML über den erforderlichen Hauptteil der Anforderung. Verwenden Sie diese Version der Methode für längere Texte oder für Texte, die Sie nicht in der URL verfügbar machen wollen.
-   Die Methode `GET /v3/tone` akzeptiert Eingabeinhalt über ihren erforderlichen Abfrageparameter `text`. Verwenden Sie diese Version der Methode für einfache Texte, die sich leicht in der URL unterbringen lassen.

Die Methoden akzeptieren die folgenden Parameter.

<table>
  <caption>Tabelle 1. Parameter der Methoden<code>/v3/tone</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parameter</th>
    <th style="text-align:center; width:12%">Typ</th>
    <th style="text-align:center; width:20%">Datentyp</th>
    <th style="text-align:left">Beschreibung</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Erforderlich für <code>POST</code></em></td>
    <td style="text-align:center">Hauptteil</td>
    <td style="text-align:center">JSON-Objekt | Zeichenfolge</td>
    <td>
      Eingabe in JSON, Klartext oder HTML, die den zu analysierenden Inhalt enthält.
      Stellen Sie bei einer JSON-Eingabe ein Objekt vom Typ
      <code>ToneInput</code> bereit (siehe <a href="#JSONinput">JSON-Eingabe
        angeben</a>). <em>Wird bei <code>GET</code>-Anforderungen nicht unterstützt.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Erforderlich für <code>GET</code></em></td>
    <td style="text-align:center">Abfrage</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Eingabe in Klartext, die den zu analysierenden Inhalt enthält. Sie müssen
      den Text in URL codieren. <em>Wird bei <code>POST</code>-Anforderungen nicht
        unterstützt.</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>Erforderlich für <code>POST</code></em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Der Inhaltstyp der Anforderung:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> für Klartext
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> für Text in HTML (Der Service entfernt
            die HTML-Tags und analysiert nur den Textinhalt)
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> für Text im JSON-Format
        </li>
      </ul>
    <em>Für <code>GET</code>-Anforderungen weglassen.</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Erforderlich</em></td>
    <td style="text-align:center">Abfrage</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die angeforderte Version des Antwortformats als Datum im Format
      <code>JJJJ-MM-TT</code>. Geben Sie z. B. <code>2017-09-21</code>
      für den 21. September 2017 an.
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Optional</em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">Zeichenfolge</td>
    <td>
      Die Sprache des Eingabeinhalts:
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
      Bei Argumenten, die aus zwei Zeichen bestehen, werden regionale Varianten als
      deren übergeordnete Sprache aufgefasst. Beispielsweise wird <code>en-US</code> als
      <code>en</code> interpretiert. Sie können verschiedene Sprachen für die Eingabe und
      die Antwort verwenden.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>Optional</em></td>
    <td style="text-align:center">Abfrage</td>
    <td style="text-align:center">Boolesch</td>
    <td>
      Gibt an, ob der Service neben seiner Analyse des Gesamtdokuments
      eine Analyse der einzelnen Sätze zurückgeben soll.
      Bei <code>true</code> (Standardeinstellung) gibt der Service Ergebnisse
      für jeden einzelnen Satz zurück.
    </td>
  </tr>
</table>

Übergeben Sie maximal 128 KB Eingabeinhalt insgesamt und höchstens 1000 einzelne Sätze. Der Service analysiert die ersten 1000 Sätze auf Dokumentebene und nur die ersten 100 Sätze auf Satzebene. Er gibt als Teil der Antwort ein Feld `warning` zurück, wenn Sie einen der Grenzwerte überschreiten. Die Anforderung ist dennoch mit dem HTTP-Antwortcode 200 erfolgreich.

### Beispielanforderungen
{: #exampleRequests}

Der folgende cURL-Beispielbefehl ruft mithilfe der HTTP-Anforderungsmethode `POST` den Endpunkt für allgemeine Zwecke mit der Eingabedatei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a> und der Version `2017-09-21` auf. Im Beispiel wird eine Analyse für das gesamte Dokument und für die einzelnen Sätze angefordert.

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

Der folgende Beispielbefehl entspricht dem vorherigen Beispiel, verwendet jedoch die HTTP-Abrufanforderung `GET`:

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

Weitere Beispiele finden Sie im [Lernprogramm zur Einführung](/docs/services/tone-analyzer/getting-started.html).

### Zeichensatz angeben
{: #charset}

Standardmäßig verwendet der Service die folgenden Zeichensätze für Eingabeinhalt:

-   *Für Inhalt in Klartext und HTML* verwendet der Service bei der Spezifikation der HTTP-Version 1.1 den Zeichensatz ISO-8859-1 (ISO - International Organization for Standardization), also effektiv den ASCII-Zeichensatz.
-   *Für JSON-Inhalt* verwendet der Service effektiv stets den Zeichensatz UTF-8 (UTF - Unicode Transformation Format) bei Abschnitt 8.1 der International Engineering Task Force (IETF) [Request for Comment (RFC) 7159 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

Schließen Sie bei der Übergabe von Inhalt in Klartext oder HTML den Parameter `charset` in den Header `Content-Type` ein, um die Zeichencodierung des Eingabetexts anzugeben. Im folgenden Beispiel wird die Zeichencodierung UTF-8 für Eingabe in Klartext angegeben:

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

Mit der Verwendung des Parameters `charset` können Sie potenzielle Probleme mit Nicht-ASCII-Zeichen oder nicht druckbaren Zeichen vermeiden. Bei der Übergabe von UTF 8-Daten ohne Angabe des Zeichensatzes können Sonderzeichen falsche Ergebnisse oder Fehler in HTTP 4*nn* oder 5*nn* zur Folge haben.

Übergeben Sie zur Vermeidung ähnlicher Fehler bei Verwendung von cURL den Inhalt stets mit der Option `--data-binary` des Befehls `curl`, um alle UTF-8-Codierungen des Inhalts zu erhalten. Wenn Sie den Inhalt mit der Option `--data` als ASCII übergeben, kann der Befehl den Inhalt verarbeiten, was Probleme für Daten in UTF-8-Codierung auslösen kann.

## JSON-Eingabe angeben
{: #JSONinput}

Zur Analyse einer JSON-Eingabe mit der Anforderungsmethode `POST` übergeben Sie die Methode eines JSON-Objekts `ToneInput` mit dem folgenden einfachen Format:

```javascript
{
  "text": ""
}
```
{: codeblock}

Das folgende Beispiel zeigt den Inhalt der Datei <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Symbol für externen Link" title="Symbol für externen Link" class="style-scope doc-content"></a>, die bei den Beispielen im [Lernprogramm zur Einführung](/docs/services/tone-analyzer/getting-started.html) verwendet wird. Die Datei enthält einen einzigen Absatz mit Text, der von einer einzigen Person verfasst ist. (Zur besseren Lesbarkeit enthält der folgende Text Zeilenumbrüche, die Sie jedoch nicht in eine echte Eingabe einbauen dürfen.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## Inhalt von JSON-Antworten
{: #JSONresponse}

Der Service gibt das JSON-Objekt `ToneAnalysis` zurück, das immer ein Feld namens `document_tone` enthält. Dieses Feld enthält ein Objekt namens `DocumentAnalysis`, das die Analyse des gesamten Eingabedokuments bereitstellt. Es enthält ein einziges Feld namens `tones`, das die Ergebnisse der Analyse der einzelnen qualifizierenden Töne des Dokuments bereitstellt.

Wenn der Parameter `sentences` der Anforderung weggelassen oder auf `true` eingestellt wird, enthält die Antwort außerdem das Feld `sentences_tone`. Dieses Feld enthält ein Array von `SentenceAnalysis`-Objekten, von denen jedes die folgenden Informationen zu einem anderen Satz des Eingabeinhalts bereitstellt:

-   `sentence_id` (Ganzzahl) stellt die eindeutige ID für den Satz bereit. Der erste Satz hat die ID 0 und die ID jedes nachfolgenden Satzes wird um einen Schritt erhöht.
-   `text` (Zeichenfolge) stellt den Text des Satzes bereit.
-   `tones` stellt die Ergebnisse der Analyse der einzelnen qualifizierenden Töne des Satzes bereit.

Das folgende Beispiel zeigt die allgemeine Struktur des Objekts `ToneAnalysis`:

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

### Töne und Bewertungsergebnisse

Die `tones`-Felder, die bei den Analysen auf Dokument- und Satzebene zurückgegeben werden, enthalten ein Array von `ToneScore`-Objekten, die Ergebnisse zu den vorherrschenden Tönen bereitstellen, deren Wert mindestens 0,5 beträgt. Wenn kein Ton eine Bewertung hat, die diesem Schwellenwert entspricht, ist das Array leer. Jedes `ToneScore`-Objekt stellt die folgenden Informationen zu einem qualifizierenden Ton bereit:

-   `score` (Doppelbyte) ist der Wert für den Ton im Bereich von 0,5 bis 1. Ein Wert größer als 0,75 gibt an, dass der Ton mit großer Wahrscheinlichkeit im Inhalt wahrgenommen wird.
-   `tone_id` (Zeichenfolge) ist eine eindeutige, nicht lokalisierte ID für den Ton. Beschreibungen der Töne finden Sie im Abschnitt [Töne für allgemeine Zwecke](#tones).
-   `tone_name` (Zeichenfolge) ist der für den Benutzer sichtbare, lokalisierte Name des Tons.

Das folgende Beispiel zeigt die Struktur des Objekts `ToneScore`:

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

### Beispielantwort
{: #exampleResponse}

Die folgende Ausgabe wird für die [Beispielanforderungen](#exampleRequests) zurückgegeben. (Dieselbe Ausgabe wird für das erste Beispiel im [Lernprogramm zur Einführung](/docs/services/tone-analyzer/getting-started.html) zurückgegeben). Die Antwort umfasst Ergebnisse für das vollständige Dokument und für jeden einzelnen Satz. Alle berichteten Töne haben einen Wert von mindestens 0,5. Töne mit einem Wert von mindestens 0,75 werden mit großer Wahrscheinlichkeit im Inhalt wahrgenommen.

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

## Töne für allgemeine Zwecke
{: #tones}

In der folgenden Tabelle werden die Töne für allgemeine Zwecke beschrieben, die der Service zurückgeben kann. Ein Ton, dessen Wert weniger als 0,5 beträgt, wird weggelassen. Dies zeigt an, dass die Emotion wahrscheinlich nicht im Inhalt wahrgenommen wird. Ein Wert größer als 0,75 gibt an, dass der Ton mit großer Wahrscheinlichkeit wahrgenommen wird.

<table>
  <caption>Tabelle 2. Töne für allgemeine Zwecke</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Ton / ID</th>
    <th style="text-align:left">Beschreibung</th>
  </tr>
  <tr>
    <td>Ärger<br/><code>anger</code></td>
    <td>
      Ärger wird durch Ungerechtigkeit, Konflikt, Demütigung, Vernachlässigung oder
      Verrat hervorgerufen. Ist der Ärger aktiv, greift die Person das Ziel verbal
      oder physisch an. Ist der Ärger passiv, schmollt die Person und empfindet
      Spannung und Feindseligkeit. (Ein emotionaler Ton.)
    </td>
  </tr>
  <tr>
    <td>Furcht<br/><code>fear</code></td>
    <td>
      Furcht ist eine Antwort auf eine potenzielle Gefahr. Sie ist ein Überlebensmechanismus,
      der als Reaktion auf einen negativen Reiz ausgelöst wird. Furcht kann als leichte
      Vorsicht oder als extreme Phobie vorliegen. (Ein emotionaler Ton.)
    </td>
  </tr>
  <tr>
    <td>Freude<br/><code>joy</code></td>
    <td>
      Freude (oder Glück) hat die Schattierungen Vergnügen, Zufriedenheit
      und Lust. Freude bringt ein Gefühl von Wohlbefinden, innerem Frieden, Liebe,
      Sicherheit und Behagen. (Ein emotionaler Ton.)
    </td>
  </tr>
  <tr>
    <td>Traurigkeit<br/><code>sadness</code></td>
    <td>
      Traurigkeit zeigt ein Gefühl von Verlorenheit und Benachteiligung an. Wenn
      eine Person still, antriebslos und zurückgezogen ist, kann man ableiten,
      dass sie Traurigkeit empfindet. (Ein emotionaler Ton.)
    </td>
  </tr>
  <tr>
    <td>Analytisch<br/><code>analytical</code></td>
    <td>
      Ein analytischer Ton zeigt das Denken und die analytische Haltung einer
      Person zu Dingen an. Eine analytische Person kann als intellektuell, rational,
      systematisch, emotionslos oder unpersönlich wahrgenommen werden. (Ein Sprachton.)
    </td>
  </tr>
  <tr>
    <td>Zuversichtlich<br/><code>confident</code></td>
    <td>
      Ein zuversichtlicher Ton zeigt den Grad der Sicherheit einer Person an. Eine
      zuversichtliche Person kann als selbstsicher, gefasst, hoffnungsvoll oder egoistisch
      wahrgenommen werden. (Ein Sprachton.)
    </td>
  </tr>
  <tr>
    <td>Zögernd<br/><code>tentative</code></td>
    <td>
      Ein zögernder Ton zeigt den Grad der Gehemmtheit einer Person an. Eine zögernde
      Person kann als fragwürdig, unsicher oder fragwürdig wahrgenommen werden. (Ein
      Sprachton.)
    </td>
  </tr>
</table>
