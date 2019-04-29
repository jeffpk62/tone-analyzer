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

# 시작하기 튜토리얼
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} 서비스는 입력 컨텐츠의 어조를 분석합니다. 이 튜토리얼은 다양한 샘플 컨텐츠를 분석하는 명령을 보여줍니다. 예는 범용 엔드포인트 및 고객 참여 엔드포인트를 모두 보여줍니다.
{: shortdesc}

튜토리얼은 인증을 위해 {{site.data.keyword.cloud}} Identity and Access Management(IAM) API 키를 사용합니다. 이전 서비스 인스턴스는 인증을 위해 기존 Cloud Foundry 서비스 인증 정보에서 `{username}` 및 `{password}`를 계속 사용할 수 있습니다. 서비스 인스턴스에 적합한 방법을 사용하여 인증하십시오. 서비스의 IAM 인증 사용에 대한 자세한 정보는 [릴리스 정보](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn)를 참조하십시오.
{: important}

## 시작하기 전에
{: #prerequisites}

- {: hide-dashboard}서비스의 인스턴스를 작성하십시오.
    1.  {: hide-dashboard} {{site.data.keyword.cloud_notm}} 카탈로그의 [{{site.data.keyword.toneanalyzershort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} 페이지로 이동하십시오. 
    1.  {: hide-dashboard} 무료 {{site.data.keyword.cloud_notm}} 계정에 가입하거나 로그인하십시오.
    1.  {: hide-dashboard} **작성**을 클릭하십시오.
-   서비스 인스턴스를 인증하기 위해 인증 정보를 복사하십시오.
    1.  {: hide-dashboard} [{{site.data.keyword.cloud_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/dashboard/apps){: new_window}에서 {{site.data.keyword.toneanalyzershort}} 서비스 인스턴스를 클릭하여 {{site.data.keyword.toneanalyzershort}} 서비스 대시보드 페이지로 이동하십시오. 
    1.  **관리** 페이지에서 **표시**를 클릭하여 인증 정보를 보십시오. 
    1.  `API Key` 및 `URL` 값을 복사하십시오. 
-   `curl` 명령이 있는지 확인하십시오. 
    -   예에서는 HTTP 인터페이스의 메소드를 호출하기 위해 `curl` 명령을 사용합니다. [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 사용자의 운영 체제에 맞는 버전을 설치하십시오. SSL(Secure Sockets Layer) 프로토콜을 지원하는 버전을 설치하십시오. `PATH` 환경 변수에 설치된 바이너리 파일을 포함시키십시오.

명령 입력 시 `{apikey}` 및 `{url}`을 실제 API 키 및 URL로 대체하십시오. 명령에서 변수값을 표시하는 중괄호를 생략하십시오. 실제 값은 다음 예와 유사합니다.
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## 1단계: POST 요청 메소드를 통한 범용 엔드포인트 사용
{: #generalPurposePost}

다음 명령은 파일 `tone.json`의 컨텐츠를 분석하기 위해 `POST /v3/tone` 메소드를 호출합니다. 이 파일은 한 사람이 작성한 일반 텍스트로 된 하나의 단락을 포함하고 있습니다. 예는 메소드의 `sentences` 조회 매개변수를 보여줍니다.

1.  샘플 파일 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>을 다운로드하십시오.
1.  다음 명령을 실행하여 전체 컨텐츠 및 각 개별 문장의 어조를 분석하십시오.
    -   {: hide-dashboard} `{apikey}` 및 `{url}`을 사용자 정보로 대체하십시오. 
    -   `{path_to_file}`을 수정하여 `tone.json` 파일의 위치를 지정하십시오.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  다음 명령을 실행하여, `sentences` 매개변수를 `false`로만 설정하여 전체 컨텐츠의 어조를 분석하십시오.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

메소드 출력의 예는 [응답 예](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone)를 참조하십시오.

## 2단계: GET 요청 메소드를 통한 범용 엔드포인트 사용
{: #generalPurposeGet}

인터페이스는 `GET /v3/tone` 메소드도 제공합니다. `GET` 메소드는 `POST` 메소드와 동일한 기능을 제공하며 동일한 결과를 생성하지만, 분석할 컨텐츠를 지정하는 데 메소드의 `text` 조회 매개변수가 사용됩니다. 이 메소드는 일반 텍스트 입력만을 수락합니다.

1.  다음 예는 `text` 매개변수를 통해 파일 `tone.json`의 텍스트를 지정하며, 표시되어 있는 바와 같이 텍스트는 URL 인코딩해야 합니다. 이 명령은 `sentences` 매개변수를 생략하므로, 이전에 표시된 첫 번째 `POST` 예와 동일한 결과가 리턴됩니다. (이 예에는 가독성을 위한 행 바꾸기가 포함되어 있습니다. 이를 실제 명령에 포함시키지 마십시오.)

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## 3단계: 고객 참여 엔드포인트 사용
{: #customerEngagement}

다음 명령은 파일 `tone-chat.json`의 컨텐츠를 분석하기 위해 `POST /v3/tone_chat` 메소드를 호출합니다. 이 파일은 두 사람(<code>customer</code>와 <code>agent</code>)이 교환한 간략한 대화 메시지를 포함합니다.

1.  샘플 파일 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘"></a>을 다운로드하십시오.
1.  다음 명령을 실행하여 샘플 파일에 포함된 대화의 어조를 분석하십시오.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

서비스의 응답은 입력의 각 발화(utterance)에서 감지된 가장 우세한 어조를 나타냅니다. 이 요청에 대한 응답의 컨텐츠를 보려면 [응답 예](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat)를 참조하십시오.

## 다음 단계
{: #gsns}

-   `/v3/tone` 메소드에 대한 자세한 정보는 [범용 엔드포인트 사용](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)을 참조하십시오. 
-   `/v3/tone_chat` 메소드에 대한 자세한 정보는 [고객 참여 엔드포인트 사용](/docs/services/tone-analyzer?topic=tone-analyzer-utco)을 참조하십시오. 
-   서비스 인터페이스의 메소드에 대한 자세한 정보는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/tone-analyzer){: new_window}를 참조하십시오. 
