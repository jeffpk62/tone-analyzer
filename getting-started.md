---

copyright:
  years: 2015, 2018
lastupdated: "2018-09-26"

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

# Getting started tutorial
{: #gettingStarted}

The {{site.data.keyword.toneanalyzershort}} service analyzes the tone of input content. This tutorial shows commands that analyze different sample content. The examples demonstrate both the general-purpose and the customer-engagement endpoints.
{: shortdesc}

> **Important:** The tutorial uses {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) API keys for authentication. Some service instances continue to use service credentials (`{username}:{password}`) for authentication. Authenticate by using the approach that is right for your region and service instance. For more information about where and how the service uses IAM authentication, see the [Release notes](/docs/services/tone-analyzer/release-notes.html).

## Before you begin
{: #prerequisites}

-   {: download} If you're seeing this, you created your service instance. Now get your credentials.
- Create an instance of the service:
    1.  Go to the [{{site.data.keyword.toneanalyzershort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/tone-analyzer){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Click **Create**.
-   Copy the credentials to authenticate to your service instance:
    1.  From the [{{site.data.keyword.Bluemix_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/dashboard/apps){: new_window}, click on your {{site.data.keyword.toneanalyzershort}} service instance to go to the {{site.data.keyword.toneanalyzershort}} service dashboard page.
    1.  On the **Manage** page, click **Show** to view your credentials.
    1.  Copy the `apikey` and `url` values.
-   Make sure that you have cURL.
    -   The examples use cURL to call methods of the HTTP interface. Install the version for your operating system from [curl.haxx.se ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://curl.haxx.se/){: new_window}. Install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

**Note:** When you enter a command, replace `{api_key}` with your actual API key. Omit the braces, which indicate a variable value, from the command. An actual value resembles the following example:

```bash
curl -X POST --user "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
```
{:pre}

## Step 1: Using the general-purpose endpoint via the POST request method
{: #generalPurposePost}

The following commands call the `POST /v3/tone` method to analyze the contents of the file `tone.json`. The file includes a single paragraph of plain text that is written by one person. The examples demonstrate the method's `sentences` query parameters.

1.  Download the sample file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1.  Issue the following command to analyze the tone of the overall content and of each individual sentence.
    -   Replace `{api_key}` with your IAM API key from the previous step.
    -   Modify `{path_to_file}` to specify the location of the `tone.json` file.

    ```bash
    curl -X POST --user "apikey:{api_key}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Issue the following command to analyze the tone of the overall content only by setting the `sentences` parameter to `false`.

    ```bash
    curl -X POST --user "apikey:{api_key}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

For an example of the method's output, see [Example response](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Step 2: Using the general-purpose endpoint via the GET request method
{: #generalPurposeGet}

The interface also offers a `GET /v3/tone` method. The `GET` method provides the same functionality and produces the same results as the `POST` method, but you use the method's `text` query parameter to specify the content to be analyzed. The method accepts only plain text input.

1.  The following example specifies the text of the file `tone.json` via the `text` parameter; as shown, you must URL-encode the text. The command omits the `sentences` parameter, so it returns the same output as the first `POST` example shown previously. (The example includes line breaks for readability; do not include them in an actual command.)

    ```bash
    curl -X GET --user "apikey:{api_key}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Step 3: Using the customer-engagement endpoint
{: #customerEngagement}

The following command calls the `POST /v3/tone_chat` method to analyze the contents of the file `tone-chat.json`. The file includes a brief exchange of messages between two people, a <code>customer</code> and an <code>agent</code>.

1.  Download the sample file <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.
1.  Issue the following command to analyze the tone of the exchange in the sample file.

    ```bash
    curl -X POST --user "apikey:{api_key}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

The service's response indicates the most prevalent tones that are detected for each utterance of the input. To view the content of the response for this request, see [Example response](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Next steps

-   For more information about the `/v3/tone` method, see [Using the general-purpose endpoint](/docs/services/tone-analyzer/using-tone.html).
-   For more information about the `/v3/tone_chat` method, see [Using the customer-engagement endpoint](/docs/services/tone-analyzer/using-tone-chat.html).
-   For more information about the methods of the service's interface, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
