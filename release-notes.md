---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-11"

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

# Release notes

The following sections document the new features and changes that were included for each release of the {{site.data.keyword.toneanalyzershort}} service. The changes do not break existing code.
{: shortdesc}

> **Note:** The release notes now document the *service version* and *interface version* for each update. You specify the *interface version* with the `version` query parameter to use new features and functionality made available with that update. The service returns both versions with the `X-Service-Api-Version` response header.

## 6 July 2017
{: #July2017b}

**Service version:** `3.3.6`<br/> **Interface version:** `2016-05-19`

The service was updated for a small defect fix to the customer engagement endpoint.

## 1 July 2017
{: #July2017a}

**Service version:** `3.3.5`<br/> **Interface version:** `2016-05-19`

The customer engagement endpoint of the {{site.data.keyword.toneanalyzershort}} service is now generally available (GA). All calls to the endpoint are now charged at the same rate as calls to the general purpose endpoint.

## 8 May 2017
{: #May2017}

**Service version:** `3.3.4`<br/> **Interface version:** `2016-05-19`

IBM updated the emotion tone and customer-care engagement tone score models by further expanding the training data set. The models now have greater precision on the benchmark data set.

## Older releases

-   [17 April 2017](#April2017)
-   [15 March 2017](#March2017)
-   [1 December 2016](#December2016)
-   [18 October 2016](#October2016b)
-   [3 October 2016](#October2016a)
-   [19 May 2016](#May2016)

### 17 April 2017
{: #April2017}

-   A new set of tones specific to the customer-engagement domain are now available: *frustrated*, *satisfied*, *excited*, *polite*, *impolite*, *sad*, and *sympathetic*. The service detects these tones from the text of a conversation between a customer and an agent. The tones are currently beta functionality.
-   IBM released updates to the emotion tone score model that improve the emotion results.

### 15 March 2017
{: #March2017}

IBM updated the emotion tone score model. The training data set was expanded. As a result, the models now have greater precision on the benchmark data set.

### 1 December 2016
{: #December2016}

IBM updated the document emotion tone scores. The new model takes into account the emotion profile of sentences to aggregate the document score.

### 18 October 2016
{: #October2016b}

IBM enhanced the social tone. The service now uses an open-source word-embedding technique called [GloVe ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://nlp.stanford.edu/projects/glove/){: new_window} to infer social tone scores. This change allows the service to cover a larger vocabulary of words when calculating social tones. For more information about how social tones are inferred, see [The science behind the service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) for the {{site.data.keyword.personalityinsightsshort}} service.

### 3 October 2016
{: #October2016a}

IBM enhanced sentence-level emotion detection. The service uses new training data, a new feature-selection process, and augmented lexicons for words, emojis, and slang. These changes produce different but significantly improved emotion scores at the sentence level. The service's API has not changed.

### 19 May 2016
{: #May2016}

The generally available (GA) release of the {{site.data.keyword.toneanalyzershort}} service includes these new features:

-   The service's models use improved context sensitivity to interpret tone. The models now use more than just lexical tokens. They now consider additional features such as punctuation, emoticons, language parameters such as sentence structure, and sentence complexity.
-   The writing tone model has been renamed to language tone.
-   The language and emotion tone models now handle negations.
-   The service no longer returns a response for sentences with fewer than three words.
-   The service now has a simplified and improved [demo ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://tone-analyzer-demo.mybluemix.net){: new_window}.
