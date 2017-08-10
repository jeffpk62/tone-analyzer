---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-08"

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

# Using the general purpose endpoint

The {{site.data.keyword.toneanalyzershort}} general purpose endpoint analyzes the tone of written communications, from short email messages to longer documents. It can help you understand the emotional, social, and language tones of your communications.
{: shortdesc}

For detailed information about the interface, including the Node.js, Java, and Python SDKs that are available for calling the service, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}. For information about the research behind the service, see [The science behind the service](/docs/services/tone-analyzer/science.html).

## Requesting a tone analysis
{: #request}

To analyze tone with the general purpose endpoint, you call one of the two versions of the service's `tone` method:

-   The `POST /v3/tone` method accepts input content in JSON, plain text, or HTML format via the required body of the request. Use this version of the method for longer text or for text that you do not want to expose on the URL.
-   The `GET /v3/tone` method accepts input content via its required `text` query parameter. Use this version of the method for simple text that is easily accommodated on the URL.

The methods accept the following parameters. For input content, submit a maximum of 128 KB of content; sentences with fewer than three words cannot be analyzed.

<table>
  <caption>Table 1. Parameters of the <code>/v3/tone</code> methods</caption>
  <tr>
    <th style="text-align:left; width:20%">Parameter</th>
    <th style="text-align:center; width:12%">Type</th>
    <th style="text-align:center; width:20%">Data type</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Required for <code>POST</code></em></td>
    <td style="text-align:center">Body</td>
    <td style="text-align:center">JSON object | String</td>
    <td>
      JSON, plain text, or HTML input that contains the content to
      be analyzed. For JSON input, provide an object of type
      <code>ToneInput</code>; see <a href="#JSONinput">Specifying JSON
        input</a>. <em>Not supported for <code>GET</code> requests.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Required for <code>GET</code></em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">String</td>
    <td>
      Plain text input that contains the content to be analyzed. You must
      URL-encode the input. <em>Not supported for <code>POST</code>
        requests.</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>Required for <code>POST</code></em></td>
    <td style="text-align:center">Header</td>
    <td style="text-align:center">String</td>
    <td>
      The content type of the request:
      <ul style="margin-left:20px; padding:0px;">
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
          <code>text/plain</code> for plain text
        </li>
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
            <code>text/html</code> for text in HTML (the service removes
            HTML tags and analyzes only the textual content)
        </li>
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
          <code>application/json</code> for text in JSON format
        </li>
      </ul>
    </td>
  </tr>
  <tr>
    <td><code>tones</code><br/><em>Optional</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">String[, String...] </td>
    <td>
      A comma-separated list of tones for which the service is to return
      its analysis of the input; the indicated tones apply both to the full
      document and to individual sentences of the document. You can specify
      one or more of the following values:
      <ul style="margin-left:20px; padding:0px;">
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
          <code>emotion</code>
        </li>
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
          <code>social</code>
        </li>
        <li style="margin:10px 0px; color:#404040; line-height:120%;">
          <code>language</code>
        </li>
      </ul>
      Omit the parameter to request results for all three tones.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>Optional</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">String</td>
    <td>
      Indicates whether the service is to return an analysis of each
      individual sentence in addition to its analysis of the full document.
      If <code>true</code> (the default), the service returns results for
      each sentence. The service returns results only for the first 100
      sentences of the input.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Required</em></td>
    <td style="text-align:center">Query</td>
    <td style="text-align:center">Boolean</td>
    <td>
      The requested version of the response format as a date in the form
      <code>YYYY-MM-DD</code>; for example, specify <code>2016-05-19</code>
      for May 19, 2016. The parameter allows the service to update its
      interface and response format for new versions without breaking
      existing clients.
    </td>
  </tr>
</table>

The following example cURL command use the HTTP `POST` request method to call the general purpose endpoint with the input file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> and a version of `2016-05-19`. The example requests an analysis of all tones for both the full document and the individual sentences.

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19"
```
{: pre}

The following example command is equivalent to the previous example but uses the HTTP `GET` request method:

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

For additional examples, see [Getting started tutorial](/docs/services/tone-analyzer/getting-started.html).

### Specifying the character set
{: #charset}

By default, the service uses the following character sets for input content:

-   *For plain text and HTML content,* the service uses the International Standards Organization (ISO)-8859-1 character set (effectively the ASCII character set) per the HTTP version 1.1 specification.
-   *For JSON content,* the service effectively always uses the Unicode Transformation Format (UTF)-8 character set per Section 8.1 of the International Engineering Task Force (IETF) [Request for Comment (RFC) 7159 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

When submitting plain text or HTML content, include the `charset` parameter with the `Content-Type` header to indicate the character encoding of the input text. The following example specifies UTF-8 character encoding for plain text input:

```javascript
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

By using the `charset` parameter, you can avoid potential problems associated with non-ASCII or non-printable characters. If you pass UTF-8 data without specifying the character set, special characters can result in incorrect results or in HTTP 4*nn* or 5*nn* errors.

### Specifying JSON input
{: #JSONinput}

To analyze JSON input, you pass the method a JSON `ToneInput` object with the following simple format.

```javascript
{
  "text": ""
}
```
{: codeblock}

The following example shows the contents of the <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a> file that is used with the examples in [Getting started tutorial](/docs/services/tone-analyzer/getting-started.html). The file includes a single paragraph of text written by one person. (The following text includes line breaks for readability; do not include them in actual input.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been disappointing for the past three quarters.
  We have a competitive product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## JSON response content
{: #JSONresponse}

The service returns a JSON `ToneAnalysis` object that always contains a `document_tone` field. This field contains a `DocumentAnalysis` object that provides the analysis of the full input document. It contains a single field, `tone_categories`, that contains an array of `ToneCategory` objects, one for each of the requested tones.

If the `sentences` parameter of the request is set to `true`, the response also includes a `sentences_tone` field. This field contains an array of `SentenceAnalysis` objects, each of which provides the following information for a different sentence from the input content:

-   `sentence_id` (integer) provides the unique identifier for the sentence. The first sentence has ID 0, and the ID of each subsequent sentence is incremented by one.
-   `text` (string) provides the text of the sentence.
-   `input_from` (integer) identifies the offset of the first character of the sentence in the overall input content.
-   `input_to` (integer) identifies the offset of the last character of the sentence in the overall input content.
-   `tone_categories` contains an array of `ToneCategory` objects, one for each of the requested tones.

The following example shows the high-level structure of the `ToneAnalysis` object:

```javascript
{
  "document_tone": {
    "tone_categories": [
      . . .
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": {integer},
      "text": "{string}",
      "input_from": {integer},
      "input_to": {integer},
      "tone_categories": [
        . . .
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### Tone category and score results

The `ToneCategory` objects that are returned for both document and sentence analyses have the following fields:

-   `category_id` (string) is the unique, non-localized identifier of the category for the results: `emotion_tone`, `social_tone`, or `language_tone`. For both the document and its sentences, the service returns results only for the tones requested with the `sentences` query parameter.
-   `category_name` (string) is the user-visible, localized name of the category.
-   `tones` contains an array of `ToneScore` objects that provides the results for the tones of the category.

The `ToneScore` objects that are returned for each tone category have the following fields:

-   `score` (double) provides the score for the tone in the range of 0 to 1.
-   `tone_id` (string) is the unique, non-localized identifier of the tone; for descriptions of the tones, [General purpose tones](#tones). The service returns scores for all tones of a category, regardless of their values.
-   `tone_name` (string) is the user-visible, localized name of the tone.

The following example shows the high-level structure of the `ToneCategory` object:

```javascript
"tone_categories": [
  {
    "category_id": "{string}",
    "category_name": "{string}"
    "tones": [
      {
        "score": {double},
        "tone_id": "{string}",
        "tone_name": "{string}"
      },
      . . .
    ]
  }
  . . .
]
```
{: codeblock}

### Example response
{: #exampleResponse}

The following output is returned for the example in [Requesting a tone analysis](#request). (The same output is returned for the first example in [Getting started](/docs/services/tone-analyzer/getting-started.html).) The response includes results for the full document and for each individual sentence. To save space, the output omits many of the tones and scores.

```javascript
{
  "document_tone": {
    "tone_categories": [
      {
        "tones": [
          {
            "score": 0.134622,
            "tone_id": "anger",
            "tone_name": "Anger"
          },
          . . .
        ],
        "category_id": "emotion_tone",
        "category_name": "Emotion Tone"
      },
      {
        "tones": [
          {
            "score": 0.829888,
            "tone_id": "analytical",
            "tone_name": "Analytical"
          },
          . . .
        ],
        "category_id": "language_tone",
        "category_name": "Language Tone"
      },
      {
        "tones": [
          {
            "score": 0.230392,
            "tone_id": "openness_big5",
            "tone_name": "Openness"
          },
          . . .
        ],
        "category_id": "social_tone",
        "category_name": "Social Tone"
      }
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": 0,
      "text": "Team, I know that times are tough!",
      "input_from": 0,
      "input_to": 34,
      "tone_categories": [
        {
          "tones": [
            {
              "score": 0.150882,
              "tone_id": "anger",
              "tone_name": "Anger"
            },
            . . .
          ],
          "category_id": "emotion_tone",
          "category_name": "Emotion Tone"
        },
        . . .
      ]
    },
    {
      "sentence_id": 1,
      "text": "Product sales have been disappointing for the past three quarters.",
      "input_from": 35,
      "input_to": 101,
      "tone_categories": [
        {
          "tones": [
            {
              "score": 0.106857,
              "tone_id": "anger",
              "tone_name": "Anger"
            },
            . . .
          ],
          "category_id": "emotion_tone",
          "category_name": "Emotion Tone"
        },
        . . .
      ]
    },
    {
      "sentence_id": 2,
      "text": "We have a competitive product, but we need to do a better job of selling it!",
      "input_from": 102,
      "input_to": 178,
      "tone_categories": [
        {
          "tones": [
            {
              "score": 0.094095,
              "tone_id": "anger",
              "tone_name": "Anger"
            },
            . . .
          ],
          "category_id": "emotion_tone",
          "category_name": "Emotion Tone"
        },
        . . .
      ]
    }
  ]
}
```
{: codeblock}

## General purpose tones
{: #tones}

The following sections describe the emotion, social, and language tones that the service can return. For each tone, a score of less than 0.5 indicates that the emotion is unlikely to be perceived in the content. A score greater than 0.75 indicates a high likelihood that the tone will be perceived.

### Emotion tones

Emotion tones (ID `emotion_tone`) measure different types of emotions and feelings that people express.

<table>
  <caption>Table 2. Emotion tones</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Tone / ID</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td>Anger<br/><code>anger</code></td>
    <td>
      Anger is evoked due to injustice, conflict, humiliation, negligence,
      or betrayal. If anger is active, the individual attacks the target,
      verbally or physically. If anger is passive, the person silently
      sulks and feels tension and hostility.
    </td>
  </tr>
  <tr>
    <td>Disgust<br/><code>disgust</code></td>
    <td>
      Disgust is an emotional response of revulsion to something considered
      offensive or unpleasant. The sensation refers to something revolting.
    </td>
  </tr>
  <tr>
    <td>Fear<br/><code>fear</code></td>
    <td>
      Fear is a response to impending danger. It is a survival mechanism that
      is triggered as a reaction to some negative stimulus. Fear may be a mild
      caution or an extreme phobia.
    </td>
  </tr>
  <tr>
    <td>Joy<br/><code>joy</code></td>
    <td>
      Joy (or happiness) has shades of enjoyment, satisfaction, and pleasure.
      Joy brings a sense of well-being, inner peace, love, safety, and
      contentment.
    </td>
  </tr>
  <tr>
    <td>Sadness<br/><code>sadness</code></td>
    <td>
      Sadness indicates a feeling of loss and disadvantage. When a person is
      quiet, less energetic, and withdrawn, it may be inferred that they feel
      sadness.
    </td>
  </tr>
</table>

### Social tones

Social tones (ID `social_tone`) measure the social tendencies in people's writing. The tones are adopted from the Big Five personality model; for more information, see the [Personality models](http://www.ibm.com/watson/developercloud/doc/personality-insights/models.html) described for the {{site.data.keyword.personalityinsightsfull}} service.

<table>
  <caption>Table 3. Social tones</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom">Tone / ID</th>
    <th style="text-align:left; vertical-align:bottom">Tone</th>
    <th style="text-align:left; vertical-align:bottom">People with a score of &lt;0.5 are more likely to be perceived as...</th>
    <th style="text-align:left; vertical-align:bottom">People with a score of &gt;0.75 are more likely to be perceived as...</th>
  </tr>
  <tr>
    <td>Agreeableness<br/><code>agreeableness_big5</code></td>
    <td>
      The tendency to be compassionate and cooperative towards others
    </td>
    <td>
      Selfish, uncaring, uncooperative, self-interested, confrontational,
      skeptical, or arrogant
    </td>
    <td>
      Caring, sympathetic, cooperative, compromising, trustworthy, or humble
    </td>
  </tr>
  <tr>
    <td>Conscientiousness<br/><code>conscientiousness_big5</code></td>
    <td>
      The tendency to act in an organized or thoughtful way
    </td>
    <td>
      Spontaneous, laid-back, reckless, unmethodical, remiss, or disorganized
    </td>
    <td>
      Disciplined, dutiful, achievement-striving, confident, driven, or
      organized
    </td>
  </tr>
  <tr>
    <td>Emotional range<br/><code>emotional_range_big5</code></td>
    <td>
      The extent to which a person's emotions are sensitive to their
      environment
    </td>
    <td>
      Calm, bland, content, relaxed, unconcerned, or careful
    </td>
    <td>
      Concerned, frustrated, angry, passionate, upset, stressed, insecure,
      or impulsive
    </td>
  </tr>
  <tr>
    <td>Extraversion<br/><code>extraversion_big5</code></td>
    <td>
      The tendency to seek stimulation in the company of others
    </td>
    <td>
      Independent, timid, introverted, restrained, boring, or dreary
    </td>
    <td>
      Engaging, seeking attention, needy, assertive, outgoing, sociable,
      cheerful, excitement-seeking, or busy
    </td>
  </tr>
  <tr>
    <td>Openness<br/><code>openness_big5</code></td>
    <td>
      The extent to which a person is open to experiencing a variety of
      activities
    </td>
    <td>
      No-nonsense, straightforward, blunt, or preferring tradition and the
      obvious over the complex, ambiguous, and subtle
    </td>
    <td>
      Intellectual, curious, emotionally aware, imaginative, willing to try
      new things, appreciating beauty, or open to change
    </td>
  </tr>
</table>

### Language tones

Language tones (ID `language_tone`) describe a person's perceived writing style. A score of less than 0.5 indicates that the content offered little or no evidence of the tone.

<table>
  <caption>Table 4. Language tones</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Tone / ID</th>
    <th style="text-align:left; vertical-align:bottom; width:40%">Description</th>
    <th style="text-align:left">People with a score of &gt;0.75 are more likely to be perceived as...</th>
  </tr>
  <tr>
    <td>Analytical<br/><code>analytical</code></td>
    <td>
      A person's reasoning and analytical attitude about things
    </td>
    <td>
      Intellectual, rational, systematic, emotionless, or impersonal
    </td>
  </tr>
  <tr>
    <td>Confident<br/><code>confident</code></td>
    <td>
      A person's degree of certainty
    </td>
    <td>
      Assured, collected, hopeful, or egotistical
    </td>
  </tr>
  <tr>
    <td>Tentative<br/><code>tentative</code></td>
    <td>
      A person's degree of inhibition
    </td>
    <td>
      Questionable, doubtful, or debatable
    </td>
  </tr>
</table>
