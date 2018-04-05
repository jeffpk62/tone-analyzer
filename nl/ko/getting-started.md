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

# 시작하기 튜토리얼
{: #gettingStarted}

{{site.data.keyword.toneanalyzershort}} 서비스는 입력 컨텐츠의 어조를 분석합니다. 이 튜토리얼은 다양한 샘플 컨텐츠를 분석하는 명령을 보여줍니다. 예는 일반 목적 엔드포인트 및 고객 참여 엔드포인트를 모두 보여줍니다.
{: shortdesc}

## 시작하기 전에
{: #prerequisites}

- 서비스의 인스턴스를 작성하십시오.
    - {: download} 이 메시지가 표시되는 경우에는 서비스 인스턴스를 작성한 것입니다. 이제 신임 정보를 가져오십시오.
    - 서비스에서 프로젝트를 작성하십시오.
        1.  {{site.data.keyword.watson}} 개발자 콘솔 [서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/developer/watson/services){: new_window} 페이지로 이동하십시오.
        1.  {{site.data.keyword.toneanalyzershort}}를 선택하고, **서비스 추가**를 클릭하고, 무료 {{site.data.keyword.Bluemix_notm}} 계정으로 가입하거나 로그인하십시오.
        1.  프로젝트 이름으로 `tone-tutorial`을 입력하고 **프로젝트 작성**을 클릭하십시오.
- 서비스 인스턴스를 인증하기 위해 신임 정보를 복사하십시오.
    - {: download} 화면에 표시된 서비스 대시보드에서 다음 작업을 수행하십시오.
        1.  **서비스 신임 정보** 탭을 클릭하십시오.
        1.  **조치**에 있는 **신임 정보 보기**를 클릭하십시오.
        1.  `username`, `password` 및 `url` 값을 복사하십시오.
        {: download}
    - 개발자 콘솔의 **tone-tutorial** 프로젝트에서, `"tone_analyzer"`의 `username`,  `password` 및 `url` 값을 **신임 정보** 섹션으로부터 복사하십시오.
- cURL이 있는지 확인하십시오.
    - 예에서는 HTTP 인터페이스의 메소드를 호출하기 위해 cURL을 사용합니다. [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 사용자의 운영 체제에 맞는 버전을 설치하십시오. SSL(Secure Sockets Layer) 프로토콜을 지원하는 버전을 설치하십시오. `PATH` 환경 변수에 설치된 2진 파일을 포함시키십시오.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}}를 사용하는 경우에는 카탈로그의 [{{site.data.keyword.toneanalyzershort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} 페이지에서 서비스 인스턴스를 작성하십시오. 서비스 신임 정보를 찾는 방법에 대한 세부사항은 [Watson 서비스의 서비스 신임 정보 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}를 참조하십시오.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 1단계: POST 요청 메소드를 통한 일반 목적 엔드포인트 사용
{: #generalPurposePost}

다음 명령은 파일 `tone.json`의 컨텐츠를 분석하기 위해 `POST /v3/tone` 메소드를 호출합니다. 이 파일은 한 사람이 작성한 일반 텍스트로 된 하나의 단락을 포함하고 있습니다. 예는 메소드의 `sentences` 조회 매개변수를 보여줍니다.

1.  샘플 파일 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>을 다운로드하십시오.
1.  다음 명령을 실행하여 전체 컨텐츠 및 각 개별 문장의 어조를 분석하십시오.
    -   `{username}` 및 `{password}`를 이전 단계에서 가져온 사용자의 서비스 신임 정보로 대체하십시오.
    -   `{path_to_file}`을 수정하여 `tone.json` 파일의 위치를 지정하십시오.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  다음 명령을 실행하여, `sentences` 매개변수를 `false`로만 설정하여 전체 컨텐츠의 어조를 분석하십시오.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

메소드 출력의 예는 [응답 예](/docs/services/tone-analyzer/using-tone.html#exampleResponse)를 참조하십시오.

## 2단계: GET 요청 메소드를 통한 일반 목적 엔드포인트 사용
{: #generalPurposeGet}

인터페이스는 `GET /v3/tone` 메소드도 제공합니다. `GET` 메소드는 `POST` 메소드와 동일한 기능을 제공하며 동일한 결과를 생성하지만, 분석할 컨텐츠를 지정하는 데 메소드의 `text` 조회 매개변수가 사용됩니다. 이 메소드는 일반 텍스트 입력만을 수락합니다.

1.  다음 예는 `text` 매개변수를 통해 파일 `tone.json`의 텍스트를 지정하며, 표시되어 있는 바와 같이 텍스트는 URL 인코딩해야 합니다. 이 명령은 `sentences` 매개변수를 생략하므로, 이전에 표시된 첫 번째 `POST` 예와 동일한 결과가 리턴됩니다. (이 예에는 가독성을 위한 행 바꾸기가 포함되어 있습니다. 이를 실제 명령에 포함시키지 마십시오.)

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## 3단계: 고객 참여 엔드포인트 사용
{: #customerEngagement}

다음 명령은 파일 `tone-chat.json`의 컨텐츠를 분석하기 위해 `POST /v3/tone_chat` 메소드를 호출합니다. 이 파일은 두 사람(<code>customer</code>와 <code>agent</code>)이 교환한 간략한 대화 메시지를 포함합니다.

1.  샘플 파일 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>을 다운로드하십시오.
1.  다음 명령을 실행하여 샘플 파일에 포함된 대화의 어조를 분석하십시오.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

서비스의 응답은 입력의 각 말에서 감지된 가장 우세한 어조를 나타냅니다. 이 요청에 대한 응답의 컨텐츠를 보려면 [응답 예](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse)를 참조하십시오.

## 다음 단계

-   `/v3/tone` 메소드에 대한 자세한 정보는 [일반 목적 엔드포인트 사용](/docs/services/tone-analyzer/using-tone.html)을 참조하십시오.
-   `/v3/tone_chat` 메소드에 대한 자세한 정보는 [고객 참여 엔드포인트 사용](/docs/services/tone-analyzer/using-tone-chat.html)을 참조하십시오.
-   서비스 인터페이스의 메소드에 대한 자세한 정보는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}를 참조하십시오.
-   [API 탐색기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}에서 API와 상호작용하십시오.
