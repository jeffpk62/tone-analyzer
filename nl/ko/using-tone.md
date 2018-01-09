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

# 일반 목적 엔드포인트 사용

{{site.data.keyword.toneanalyzershort}} 일반 목적 엔드포인트는 짧은 이메일 메시지부터 긴 문서에 이르기까지, 기록된 컨텐츠의 어조를 분석합니다. 이는 자신이 수행하는 의사소통의 감정적 및 언어적 톤을 이해하는 데 도움을 줍니다. 서비스를 호출하는 데 사용 가능한 Node.js, Java 및 Python SDK를 포함, 인터페이스에 대한 자세한 정보는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}를 참조하십시오.
{: shortdesc}

## 어조 분석 요청
{: #request}

일반 목적 엔드포인트를 사용하여 어조를 분석하려는 경우에는 서비스의 두 가지 `tone` 메소드 중 하나를 호출합니다. 

-   `POST /v3/tone` 메소드는 필수 요청 본문을 통해 JSON, 일반 텍스트 또는 HTML 형식의 입력 컨텐츠를 수락합니다. 긴 텍스트 또는 URL에 노출시키지 않을 텍스트에 대해서는 이 메소드 버전을 사용하십시오. 
-   `GET /v3/tone` 메소드는 필수 `text` 조회 매개변수를 통해 입력 컨텐츠를 수락합니다. URL이 쉽게 수용할 수 있는 간단한 텍스트의 경우에는 이 메소드 버전을 사용하십시오. 

메소드는 다음 매개변수를 수락합니다. 

<table>
  <caption>표 1. <code>/v3/tone</code> 메소드의 매개변수</caption>
  <tr>
    <th style="text-align:left; width:20%">매개변수</th>
    <th style="text-align:center; width:12%">유형</th>
    <th style="text-align:center; width:20%">데이터 유형</th>
    <th style="text-align:left">설명</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em><code>POST</code>의 필수 항목</em></td>
    <td style="text-align:center">본문</td>
    <td style="text-align:center">JSON 오브젝트 | 문자열</td>
    <td>
      분석할 컨텐츠를 포함하는 JSON, 일반 텍스트 또는 HTML 입력입니다.
      JSON 입력의 경우에는 유형이 <code>ToneInput</code>인 오브젝트를
      제공하십시오. <a href="#JSONinput">JSON 입력 지정</a>을
      참조하십시오. <em><code>GET</code> 요청에는 지원되지 않습니다. </em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em><code>GET</code>의 필수 항목</em></td>
    <td style="text-align:center">조회</td>
    <td style="text-align:center">문자열</td>
    <td>
      분석할 컨텐츠를 포함하는 일반 텍스트 입력입니다. 이 입력은
      URL 인코딩해야 합니다. <em><code>POST</code> 요청에는
      지원되지 않습니다. </em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em><code>POST</code>의 필수 항목</em></td>
    <td style="text-align:center">헤더</td>
    <td style="text-align:center">문자열</td>
    <td>
      요청의 컨텐츠 유형입니다.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          일반 텍스트의 경우 <code>text/plain</code>
        </li>
        <li style="margin:0px; padding:0px">
            HTML의 경우 <code>text/html</code>(서비스는
            HTML 태그를 제거하고 텍스트 컨텐츠만 분석함)
        </li>
        <li style="margin:0px; padding:0px">
          JSON 형식의 텍스트의 경우 <code>application/json</code>
        </li>
      </ul>
    <em><code>GET</code> 요청의 경우 생략합니다. </em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>필수</em></td>
    <td style="text-align:center">조회</td>
    <td style="text-align:center">문자열</td>
    <td>
      <code>YYYY-MM-DD</code> 양식의 날짜인, 요청된
      응답 형식 버전입니다. 예를 들면, 2017년 9월 21일의
      경우에는 <code>2017-09-21</code>을 지정하십시오.
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>선택사항</em></td>
    <td style="text-align:center">헤더</td>
    <td style="text-align:center">문자열</td>
    <td>
      입력 컨텐츠의 언어입니다.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code>(영어, 기본값)
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code>(프랑스어)
        </li>
      </ul>
      방언은 해당 상위 언어로 간주됩니다. 예를 들어,
      <code>en-US</code>는 <code>en</code>으로 해석됩니다. 입력 컨텐츠는
      지정된 언어와 일치해야 합니다. 두 언어를 모두 포함하는 컨텐츠를
      제출하지 마십시오. 입력과 응답에는 각각 다른 언어를 사용할 수
      있습니다.
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
      2문자 인수의 경우, 방언은 해당 상위 언어로 간주됩니다.
      예를 들면, <code>en-US</code>는 <code>en</code>으로 해석됩니다.
      입력과 응답에는 각각 다른 언어를 사용할 수 있습니다.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>선택사항</em></td>
    <td style="text-align:center">조회</td>
    <td style="text-align:center">부울</td>
    <td>
      서비스가 전체 문서의 분석 외에 각 개별 문장의
      분석 또한 리턴해야 하는지 표시합니다.
      <code>true</code>(기본값)인 경우 서비스는
      각 문장에 대한 결과를 리턴합니다.
    </td>
  </tr>
</table>

128KB 이상의 전체 입력 컨텐츠, 1000개 이상의 개별 문장을 제출하지 마십시오. 서비스는 문서 레벨 분석의 경우 처음 1000개 문장, 문장 레벨 분석의 경우 처음 100개 문장만 분석합니다. 두 가지 한계 중 하나를 초과하는 경우에는 응답의 일부로서 `warning` 필드가 리턴되지만, 요청은 HTTP 응답 코드 200을 출력하며 여전히 성공합니다. 

### 요청 예
{: #exampleRequests}

다음 cURL 명령 예는 HTTP `POST` 요청 메소드를 사용하여 입력 파일이 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a>이며 버전이 `2017-09-21`인 일반 목적 엔드포인트를 호출합니다. 이 예는 전체 문서와 개별 문장의 분석을 둘 다 요청합니다. 

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

다음 명령 예는 이전 예와 동일하지만 HTTP `GET` 요청 메소드를 사용합니다. 

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

추가 예를 보려면 [시작하기 튜토리얼](/docs/services/tone-analyzer/getting-started.html)을 참조하십시오. 

### 문자 세트 지정
{: #charset}

기본적으로 서비스는 입력 컨텐츠에 다음 문자 세트를 사용합니다. 

-   *일반 텍스트 및 HTML 컨텐츠의 경우,* 서비스는 HTTP 버전 1.1 스펙에 따라 ISO(International Standards Organization)-8859-1 문자 세트(사실상 ASCII 문자 세트)를 사용합니다. 
-   *JSON 컨텐츠의 경우,* 서비스는 IETF(International Engineering Task Force) [Request for Comment(RFC) 7159 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}의 8.1절에 따라 사실상 항상 UTF(Unicode Transformation Format)-8 문자 세트를 사용합니다. 

일반 텍스트 또는 HTML 컨텐츠를 제출할 때는 `Content-Type` 헤더에 `charset` 매개변수를 포함시켜 입력 텍스트의 문자 인코딩을 표시하십시오. 다음 예는 일반 텍스트 입력에 대해 UTF-8 문자 인코딩을 지정합니다. 

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

`charset` 매개변수를 사용하면 비ASCII 또는 인쇄할 수 없는 문자와 연관되어 발생할 수 있는 잠재적 문제점을 방지할 수 있습니다. 문자 세트를 지정하지 않고 UTF-8 데이터를 전달하면 특수 문자의 결과가 올바르지 않거나 HTTP 4*nn* 또는 5*nn* 오류가 발생할 수 있습니다. 

cURL 사용 시 유사한 오류를 방지하기 위해, 항상 컨텐츠를 `curl` 명령의 `--data-binary` 옵션을 통해 전달함으로써 컨텐츠의 UTF-8 인코딩을 유지하십시오. 컨텐츠를 ASCII로 전달하기 위해 `--data` 옵션을 사용하는 경우 이 명령은 입력을 처리할 수 있고 데이터가 UTF-8로 인코딩된 경우 문제점이 발생할 수 있습니다. 

## JSON 입력 지정
{: #JSONinput}

`POST` 요청 메소드를 사용하여 JSON 입력을 분석하려는 경우에는 다음과 같은 간단한 형식을 사용하여 메소드에 JSON `ToneInput` 오브젝트를 전달합니다. 

```javascript
{
  "text": ""
}
```
{: codeblock}

다음 예는 [시작하기 튜토리얼](/docs/services/tone-analyzer/getting-started.html)에서 사용된 <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="외부 링크 아이콘" title="외부 링크 아이콘" class="style-scope doc-content"></a> 파일의 컨텐츠를 보여줍니다. 이 파일은 한 사람이 작성한 텍스트로 된 하나의 단락을 포함하고 있습니다. (다음 텍스트에는 가독성을 위한 행 바꾸기가 포함되어 있습니다. 이를 실제 입력에 포함시키지 마십시오.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## JSON 응답 컨텐츠
{: #JSONresponse}

서비스는 항상 `document_tone` 필드를 포함하는 JSON `ToneAnalysis` 오브젝트를 리턴합니다. 이 필드는 전체 입력 문서의 분석을 제공하는 `DocumentAnalysis` 오브젝트를 포함합니다. 이는 문서에서 조건을 만족하는 각 어조에 대한 분석 결과를 제공하는 단일 필드 `tones`를 포함합니다. 

요청의 `sentences` 매개변수가 생략되었거나 `true`로 설정된 경우 응답은 `sentences_tone` 필드 또한 포함합니다. 이 필드는 입력 컨텐츠에 포함된 서로 다른 문장에 대해 각각 다음 정보를 제공하는 `SentenceAnalysis` 오브젝트의 배열을 포함합니다. 

-   `sentence_id`(정수)는 문장의 고유 ID를 제공합니다. 첫 번째 문장의 ID는 0이며, 각 후속 문장의 ID는 1씩 늘어납니다. 
-   `text`(문자열)는 문장의 텍스트를 제공합니다. 
-   `tones`는 문장에서 조건을 만족하는 각 어조에 대한 분석 결과를 제공합니다. 

다음 예는 `ToneAnalysis` 오브젝트의 상위 레벨 구조를 보여줍니다. 

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

### 어조 및 점수 결과

문서 및 문장 레벨 분석에서 리턴된 `tones` 필드는 점수가 0.5 이상인 우세 어조에 대한 결과를 제공하는 `ToneScore` 오브젝트의 배열을 포함합니다. 이 임계값을 만족하는 점수를 획득한 어조가 없는 경우에는 배열이 비어 있습니다. 각 `ToneScore` 오브젝트는 조건을 만족하는 어조에 대한 다음 정보를 제공합니다. 

-   `score`(Double)는 0.5 - 1 범위의 어조 점수입니다. 0.75보다 높은 점수는 해당 어조가 컨텐츠에서 관찰될 가능성이 높음을 나타냅니다. 
-   `tone_id`(문자열)는 어조에 대한, 현지화되지 않은 고유 ID입니다. 어조에 대한 설명은 [일반 목적 어조](#tones)를 참조하십시오. 
-   `tone_name`(문자열)은 사용자에게 표시되는, 어조의 현지화된 이름입니다. 

다음 예는 `ToneScore` 오브젝트의 구조를 보여줍니다. 

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

### 응답 예
{: #exampleResponse}

다음 출력은 [요청 예](#exampleRequests)에 대해 리턴된 출력입니다. ([시작하기 튜토리얼](/docs/services/tone-analyzer/getting-started.html)의 첫 번째 예에 대해서도 동일한 출력이 리턴됩니다.) 응답은 전체 문서 및 각 개별 문장에 대한 결과를 포함합니다. 모든 보고된 어조의 점수는 0.5 이상이며, 0.75보다 점수가 높은 어조는 컨텐츠에서 관찰될 가능성이 높습니다. 

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

## 일반 목적 어조
{: #tones}

다음 표에서는 서비스가 리턴할 수 있는 일반 목적 어조에 대해 설명합니다. 점수가 0.5 미만인 어조는 생략되며, 이는 해당 감정이 컨텐츠에서 관찰될 가능성이 낮음을 나타냅니다. 0.75보다 높은 점수는 해당 어조가 관찰될 가능성이 높음을 나타냅니다. 

<table>
  <caption>표 2. 일반 목적 어조</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">어조 / ID</th>
    <th style="text-align:left">설명</th>
  </tr>
  <tr>
    <td>분노<br/><code>anger</code></td>
    <td>
      분노는 부당함, 충돌, 굴욕, 소홀함, 또는 배신으로 인해
      발생합니다. 분노가 표출되는 경우 사람은 대상을 말로,
      또는 물리적으로 공격합니다. 분노가 표출되지 않는 경우
      개인은 토라진 상태로 긴장과 적개심을 느낍니다. (감정적 톤)
    </td>
  </tr>
  <tr>
    <td>두려움<br/><code>fear</code></td>
    <td>
      두려움은 임박한 위험에 반응하여 발생합니다. 이는 어떤 부정적인 자극에 대한
      반응으로서 촉발되는 생존 메커니즘입니다. 두려움은 가벼운 경계일 수도,
      극도의 공포증일 수도 있습니다. (감정적 톤)
    </td>
  </tr>
  <tr>
    <td>기쁨<br/><code>joy</code></td>
    <td>
      기쁨(또는 행복)에는 즐거움, 만족과 유쾌함이 조금씩 포함되어 있습니다.
      기쁨은 행복, 내적 평화, 사랑, 안전, 만족과 같은 감정을 불러옵니다. (감정적 톤)
    </td>
  </tr>
  <tr>
    <td>슬픔<br/><code>sadness</code></td>
    <td>
      슬픔은 상실감 및 불편감을 나타냅니다. 사람이 조용하거나,
      활기차지 않거나 소극적인 경우에는 슬픔을 느끼는 것으로
      추측할 수 있습니다. (감정적 톤)
    </td>
  </tr>
  <tr>
    <td>분석적<br/><code>analytical</code></td>
    <td>
      분석적 어조는 사람이 주변에 대해 이성적이고 분석적 태도를
      취하고 있음을 나타냅니다. 분석적인 사람은 지적이거나, 이성적이거나,
      체계적이거나, 무감동하거나 냉담한 사람으로 인식될 수 있습니다. (언어적 톤)
    </td>
  </tr>
  <tr>
    <td>자신 있음<br/><code>confident</code></td>
    <td>
      자신 있는 어조는 사람이 확신하는 정도를 나타냅니다. 자신 있는 사람은
      대담하거나, 침착하거나, 희망에 차 있거나 자기 중심적인 사람으로 인식될 수 있습니다.
      (언어적 톤)
    </td>
  </tr>
  <tr>
    <td>자신 없음<br/><code>tentative</code></td>
    <td>
      자신 없는 어조는 사람이 망설이는 정도를 나타냅니다. 자신 없는 사람은
      불확실하거나, 회의적이거나 의심스러운 사람으로 인식될 수 있습니다.
      (언어적 톤)
    </td>
  </tr>
</table>
