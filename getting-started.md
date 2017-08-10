---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-09"

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

# Getting started tutorial

The {{site.data.keyword.toneanalyzershort}} service analyzes the tone of input content. This tutorial shows commands that analyze different sample content. The examples demonstrate both the general purpose and the customer engagement endpoints.
{: shortdesc}

> **Note:** The examples use cURL to call methods of the HTTP interface. You can install the version of cURL for your operating system from [curl.haxx.se](https://curl.haxx.se/){: new_window}. You must install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

## Step 1: Log in, create the service, and get your credentials

If you already know the credentials for your {{site.data.keyword.toneanalyzershort}} service instance, skip this step.
{: tip}

1.  Go to the [{{site.data.keyword.toneanalyzershort}} service](https://console.bluemix.net/catalog/services/tone-analyzer/){: new_window} and either sign up for a free Bluemix account or log in.
1.  After you log in, enter `tone-tutorial` in the **Service name field** of the {{site.data.keyword.toneanalyzershort}} page. Click **Create**.
1.  Copy your credentials:
    1.  Click **Service credentials**.
    1.  Click **View credentials** under **Actions**.
    1.  Copy the `username` and `password` values.

## Step 2. Use the general purpose endpoint via the POST request method
{: #generalPurposePost}

The following commands call the `POST /v3/tone` method to analyze the contents of the file `tone.json`. The file includes a single paragraph of plain text written by one person. The examples demonstrate various uses of the method's `tones` and `sentences` query parameters.

1.  Download the sample file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1.  Issue the following command to analyze the input for all available tones: `emotion`, `language`, and `social`. The command analyzes the tones of the overall content and of each individual sentence.
    -   Replace `{username}` and `{password}` with your service credentials from the previous step.
    -   Modify `{path_to_file}` to specify the location of the `tone.json` file.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19"
    ```
    {: pre}

1.  Issue the following command to limit the results to only the `emotion` tone by using the `tones` parameter. The command analyzes the emotional tone of the overall content and of each individual sentence.
    -   Replace `{username}` and `{password}` with your service credentials.
    -   Modify `{path_to_file}` to specify the location of the `tone.json` file.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19&tones=emotion"
    ```
    {: pre}

    You can set the `tones` parameter to any combination of `emotion`, `language`, and `social`; for example, `tones=emotion,social`.
    {: tip}

1.  Issue the following command to analyze all available tones for the overall content only by setting the `sentences` parameter to `false`.
    -   Replace `{username}` and `{password}` with your service credentials.
    -   Modify `{path_to_file}` to specify the location of the `tone.json` file.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19&sentences=false" \
    ```
    {: pre}

For an example of the method's output, see [Example response](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Step 3. Use the general purpose endpoint via the GET request method
{: #generalPurposeGet}

The interface also offers a `GET /v3/tone` method. The `GET` method provides the same functionality and produces the same results as the `POST` method, but you use the method's `text` query parameter to specify the content to be analyzed. The method accepts only plain text input.

1.  The following example specifies the text of the file `tone.json` via the `text` parameter; as shown, you must URL-encode the text. The command omits the `tones` and `sentences` parameters, so it returns the same output as the first `POST` example shown previously. (The example includes line breaks for readability; do not include them in an actual command.)
    -   Replace `{username}` and `{password}` with your service credentials.

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Step 4. Use the customer engagement endpoint
{: #customerEngagement}

The following command calls the `POST /v3/tone_chat` method to analyze the contents of the file `tone-chat.json`. The file includes a brief exchange of messages between two people, a <code>customer</code> and an <code>agent</code>.

1.  Download the sample file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1.  Issue the following command to analyze the tone of the exchange in the sample file.
    -   Replace `{username}` and `{password}` with your service credentials.
    -   Modify `{path_to_file}` to specify the location of the `tone-chat.json` file.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2016-05-19"
    ```
    {: pre}

The service's response indicates the most prevalent tones detected for each utterance of the input. To view the content of the response for this request, see [Example response](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Next steps

-   For more information about the `/v3/tone` method, see [Using the general purpose endpoint](/docs/services/tone-analyzer/using-tone.html).
-   For more information about the `/v3/tone-chat` method, see [Using the customer engagement endpoint](/docs/services/tone-analyzer/using-tone-chat.html).
-   For detailed information about the methods of the service's interface, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Interact with the API in the [API explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}.
