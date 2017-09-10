---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-10"

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

# Using the customer engagement endpoint

The {{site.data.keyword.toneanalyzershort}} customer engagement endpoint analyzes the tone of customer service and support conversations. It can help you better understand your interactions with customers and improve your communications in general or for specific customers.
{: shortdesc}

For detailed information about the interface, including the Node.js, Java, and Python SDKs that are available for calling the service, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}. For information about the research behind the service, see [The science behind the service](/docs/services/tone-analyzer/science.html).

## Requesting a tone analysis
{: #request}

To analyze tone with the customer engagement endpoint, you call the `POST /v3/tone-chat` method with the following parameters.

<table>
  <caption>Table 1. Parameters of the <code>POST /v3/tone-chat</code>
    method</caption>
  <tr>
    <th style="text-align:left; width:20%">Parameter</th>
    <th style="text-align:center; width:12%">Type</th>
    <th style="text-align:center; width:20%">Data type</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Required</em></td>
    <td style="text-align:center">Body</td>
    <td style="text-align:center">JSON object</td>
    <td>
      A JSON <code>ToneChatInput</code> object that contains the content
      to be analyzed. See <a href="#JSONrequest">Specifying JSON input</a>.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Required</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">String</td>
    <td>
      The requested version of the interface as a date in the form
      <code>YYYY-MM-DD</code>; for example, specify <code>2016-05-19</code>
      for May 19, 2016. The parameter allows the service to update its
      interface and response format for new versions without breaking
      existing clients.
    </td>
  </tr>
</table>

The following example cURL command calls the customer engagement endpoint with the input file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> and a version of `2016-05-19`:

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2016-05-19"
```
{: pre}

### Specifying JSON input
{: #JSONrequest}

You pass the method a JSON `ToneChatInput` object with the following format. The `utterances` field provides an array of `utterance` objects, where `text` is a required string that provides an utterance contributed by a user to the conversation that is to be analyzed, and `user` is an optional string that identifies the user who contributed the utterance.

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

The following example shows the contents of the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file. The file includes a brief exchange between a <code>customer</code> and an <code>agent</code>.

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

## JSON response content
{: #JSONresponse}

The service returns a JSON `UtteranceAnalyses` object that contains a single field, `utterances_tone`. This field contains an array of `UtteranceAnalysis` objects, each of which provides the following information about an utterance of the input content:

-   `utterance_id` (integer) provides the unique identifier of the utterance. The first utterance has ID 0, and the ID of each subsequent utterance is incremented by one.
-   `utterance_text` (string) provides the text of the utterance.
-   `tones` is an array of `ToneChatScore` objects that provides results for any tone whose score is at least 0.5. The array is empty if the utterance has no tone with a score that meets this threshold.

Each `ToneChatScore` object provides the following information about one of the qualifying tones:

-   `score` (double) provides the score for the tone in the range of 0.5 to 1. A score greater than 0.75 indicates a high likelihood that the tone is perceived in the utterance.
-   `tone_id` (string) is the unique, non-localized identifier of the tone; for descriptions of the tones, see [Customer engagement tones](#tones).
-   `tone_name` (string) is the user-visible, localized name of the tone.

The following example shows the high-level structure of an `UtterancesAnalyses` object:

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

### Example response
{: #exampleResponse}

The following output is returned for the example in [Requesting a tone analysis](#request). (The same output is returned for the example in the [Getting started tutorial](/docs/services/tone-analyzer/getting-started.html#customerEngagement).) All reported tones have a score of at least 0.5; those with a score of at least 0.75 are very likely to be perceived by participants in the conversation.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.711722,
          "tone_id": "polite",
          "tone_name": "polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": [
        {
          "score": 0.814275,
          "tone_id": "polite",
          "tone_name": "polite"
        }
      ]
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.753187,
          "tone_id": "frustrated",
          "tone_name": "frustrated"
        },
        {
          "score": 0.940611,
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
          "score": 0.992159,
          "tone_id": "polite",
          "tone_name": "polite"
        },
        {
          "score": 0.772394,
          "tone_id": "sympathetic",
          "tone_name": "sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Customer engagement tones
{: #tones}

The service can return scores for the following seven tones.

<table style="width:90%">
  <caption>Table 2. Customer engagement tones</caption>
  <tr>
    <th style="text-align:left; width:20%">Tone / ID</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td>Excited<br/><code>excited</code></td>
    <td>
      Showing personal enthusiasm and interest
    </td>
  </tr>
  <tr>
    <td>Frustrated<br/><code>frustrated</code></td>
    <td>
      Defined as feeling annoyed and irritable
    </td>
  </tr>
  <tr>
    <td>Impolite<br/><code>impolite</code></td>
    <td>
      Being disrespectful and rude
    </td>
  </tr>
  <tr>
    <td>Polite<br/><code>polite</code></td>
    <td>
      Defined as rational, goal-oriented behavior
    </td>
  </tr>
  <tr>
    <td>Sad<br/><code>sad</code></td>
    <td>
      Regarded as an unpleasant passive emotion
    </td>
  </tr>
  <tr>
    <td>Satisfied<br/><code>satisfied</code></td>
    <td>
      An affective response to perceived service quality
    </td>
  </tr>
  <tr>
    <td>Sympathetic<br/><code>sympathetic</code></td>
    <td>
      An affective mode of understanding that involves emotional resonance
    </td>
  </tr>
</table>
