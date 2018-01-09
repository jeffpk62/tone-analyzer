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

# 고객 참여 엔드포인트 사용

{{site.data.keyword.toneanalyzershort}} 고객 참여 엔드포인트는 고객 서비스 및 지원 대화의 어조를 분석합니다. 이는 사용자가 자신과 고객 간의 상호작용을 더 잘 이해하고 일반 고객 또는 특정 고객과의 의사소통을 개선하는 데 도움을 줍니다. 서비스를 호출하는 데 사용 가능한 Node.js, Java 및 Python SDK를 포함, 인터페이스에 대한 자세한 정보는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}를 참조하십시오.
{: shortdesc}

## 어조 분석 요청
{: #request}

고객 참여 엔드포인트를 사용하여 어조를 분석하려는 경우에는 다음 매개변수를 사용하여 `POST /v3/tone_chat` 메소드를 호출합니다. 

<table>
  <caption>표 1. <code>POST /v3/tone_chat</code> 메소드의 매개변수</caption>
  <tr>
    <th style="text-align:left; width:20%">매개변수</th>
    <th style="text-align:center; width:12%">유형</th>
    <th style="text-align:center; width:20%">데이터 유형</th>
    <th style="text-align:left">설명</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>필수</em></td>
    <td style="text-align:center">본문</td>
    <td style="text-align:center">JSON 오브젝트</td>
    <td>
      분석할 컨텐츠를 포함하는 JSON <code>ToneChatInput</code> 오브젝트입니다.
      <a href="#JSONrequest">JSON 입력 지정</a>을 참조하십시오.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>필수</em></td>
    <td style="text-align:center">조회</td>
    <td style="text-align:center">문자열</td>
    <td>
      <code>YYYY-MM-DD</code> 양식의 날짜인, 요청된
      인터페이스 버전입니다. 예를 들면, 2017년 9월 21일의
      경우에는 <code>2017-09-21</code>을 지정하십시오.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>선택사항</em></td>
    <td style="text-align:center">헤더</td>
    <td style="text-align:center">문자열</td>
    <td>
      응답에 대한 선호 언어입니다.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar(아랍어)
        </li>
        <li style="margin:0px; padding:0px">
          de(독일어)
        </li>
        <li style="margin:0px; padding:0px">
          en(영어, 기본값)
        </li>
        <li style="margin:0px; padding:0px">
          es(스페인어)
        </li>
        <li style="margin:0px; padding:0px">
          fr(프랑스어)
        </li>
        <li style="margin:0px; padding:0px">
          it(이탈리아어)
        </li>
        <li style="margin:0px; padding:0px">
          ja(일본어)
        </li>
        <li style="margin:0px; padding:0px">
          ko(한국어)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br(포르투갈어(브라질))
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn(중국어)
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw(대만어)
        </li>
      </ul>
    </td>
  </tr>
</table>

50개 이상의 말을 제출하는 경우 서비스가 응답의 `utterances_tone` 레벨에서 전체 컨텐츠에 대해 `warning` 필드를 리턴합니다. 서비스는 처음 50개의 말만 분석합니다. 500자 이상을 포함하는 하나의 말을 제출하는 경우, 서비스는 해당 말에 대해 `error` 필드를 리턴하고 해당 말을 분석하지 않습니다. 두 경우 모두 요청은 HTTP 응답 코드 200을 출력하며 여전히 성공합니다. 

> **참고:** 입력의 모든 말이 500자를 초과하는 경우 서비스는 응답 코드 400을 리턴합니다. 

### 요청 예
{: #exampleRequest}

다음 cURL 명령 예는 입력 파일이 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>이며 버전이 `2017-09-21`인 고객 참여 엔드포인트를 호출합니다. 

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## JSON 입력 지정
{: #JSONrequest}

메소드에 다음 형식으로 JSON `ToneChatInput` 오브젝트를 전달합니다. `utterances` 필드는 `utterance` 오브젝트의 배열을 제공하며, 여기서 `text`는 사용자가 분석되는 대화에 기여한 말을 제공하는 필수 문자열이고 `user`는 발언에 기여한 사용자를 식별하는 선택적 문자열입니다. 

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

다음 예는 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일의 컨텐츠를 보여줍니다. 이 파일은 <code>customer</code>와 <code>agent</code>가 교환한 간략한 대화를 포함합니다. 

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

## JSON 응답 컨텐츠
{: #JSONresponse}

서비스는 단일 필드 `utterances_tone`을 포함하는 JSON `UtteranceAnalyses` 오브젝트를 리턴합니다. 이 필드는 입력 컨텐츠에 포함된 말에 대해 각각 다음 정보를 제공하는 `UtteranceAnalysis` 오브젝트의 배열을 포함합니다. 

-   `utterance_id`(정수)는 말의 고유 ID를 제공합니다. 첫 번째 말의 ID는 0이며, 각 후속 말의 ID는 1씩 늘어납니다. 
-   `utterance_text`(문자열)는 말의 텍스트를 제공합니다. 
-   `tones`는 점수가 0.5 이상인 우세 어조에 대한 결과를 제공하는 `ToneChatScore` 오브젝트의 배열입니다. 말에 이 임계값을 만족하는 점수를 획득한 어조가 없는 경우에는 배열이 비어 있습니다. 

각 `ToneChatScore` 오브젝트는 조건을 만족하는 어조에 대한 다음 정보를 제공합니다. 

-   `score`(Double)는 0.5 - 1 범위의 어조 점수입니다. 0.75보다 높은 점수는 해당 어조가 말에서 관찰될 가능성이 높음을 나타냅니다. 
-   `tone_id`(문자열)는 어조에 대한, 현지화되지 않은 고유 ID입니다. 어조에 대한 설명은 [고객 참여 어조](#tones)를 참조하십시오. 
-   `tone_name`(문자열)은 사용자에게 표시되는, 어조의 현지화된 이름입니다. 

다음 예는 `UtterancesAnalyses` 오브젝트의 구조를 보여줍니다. 

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

### 응답 예
{: #exampleResponse}

다음 출력은 [요청 예](#exampleRequest)에 대해 리턴된 출력입니다. ([시작하기 튜토리얼](/docs/services/tone-analyzer/getting-started.html#customerEngagement)의 예에 대해서도 동일한 출력이 리턴됩니다.) 모든 보고된 어조의 점수는 0.5 이상이며, 0.75보다 점수가 높은 어조는 대화의 참여자에 의해 관찰될 가능성이 높습니다. 

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

## 고객 참여 어조
{: #tones}

서비스는 다음 일곱 가지 어조에 대한 점수를 리턴할 수 있습니다. 

<table style="width:90%">
  <caption>표 2. 고객 참여 어조</caption>
  <tr>
    <th style="text-align:left; width:20%">어조 / ID</th>
    <th style="text-align:left">설명</th>
  </tr>
  <tr>
    <td>흥분<br/><code>excited</code></td>
    <td>
      개인적 열정 및 관심을 보임
    </td>
  </tr>
  <tr>
    <td>실망<br/><code>frustrated</code></td>
    <td>
      짜증 및 화를 내는 상태로 정의됨
    </td>
  </tr>
  <tr>
    <td>무례함<br/><code>impolite</code></td>
    <td>
      불경하고 무례한 태도
    </td>
  </tr>
  <tr>
    <td>정중함<br/><code>polite</code></td>
    <td>
      이성적이고 목표를 중시하는 태도로 정의됨
    </td>
  </tr>
  <tr>
    <td>슬픔<br/><code>sad</code></td>
    <td>
      불쾌하며 소극적인 감정으로 간주됨
    </td>
  </tr>
  <tr>
    <td>만족<br/><code>satisfied</code></td>
    <td>
      관찰된 서비스 품질에 대한 정서적 반응
    </td>
  </tr>
  <tr>
    <td>공감<br/><code>sympathetic</code></td>
    <td>
      감응을 포함하는 이해의 정서적 형태
    </td>
  </tr>
</table>
