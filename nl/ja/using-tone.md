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

# 汎用エンドポイントの使用

{{site.data.keyword.toneanalyzershort}} 汎用エンドポイントは、短い E メール・メッセージから長い文書まで、書面によるコミュニケーションを分析します。コミュニケーションの感情トーンと言語トーンを理解するのに役立ちます。サービスの呼び出しに使用できる Node.js SDK、Java SDK、Python SDK などのインターフェースについて詳しくは、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window} を参照してください。
{: shortdesc}

## トーン分析の要求
{: #request}

汎用エンドポイントを使用してトーンを分析するには、サービスの `tone` メソッドの次の 2 つのバージョンのいずれかを呼び出します。

-   `POST /v3/tone` メソッドは、必須の要求本体を介して、JSON、プレーン・テキスト、または HTML 形式の入力コンテンツを受け入れます。このバージョンのメソッドは、比較的長いテキストや、URL に表示したくないテキストに使用します。
-   `GET /v3/tone` メソッドは、このメソッドの必須の `text` 照会パラメーターを介して、入力コンテンツを受け入れます。このバージョンのメソッドは、URL に容易に収まるシンプルなテキストに使用します。

これらのメソッドは、以下のパラメーターを受け入れます。

<table>
  <caption>表 1. <code>/v3/tone</code> メソッドのパラメーター</caption>
  <tr>
    <th style="text-align:left; width:20%">パラメーター</th>
    <th style="text-align:center; width:12%">タイプ</th>
    <th style="text-align:center; width:20%">データ・タイプ</th>
    <th style="text-align:left">説明</th>
  </tr>
  <tr>
    <td><code>本文</code><br/><em><code>POST</code> に必須</em></td>
    <td style="text-align:center">本文</td>
    <td style="text-align:center">JSON オブジェクト | ストリング</td>
    <td>
      分析対象のコンテンツを含む JSON、プレーン・テキスト、または HTML 入力。
JSON 入力の場合は、<code>ToneInput</code> タイプのオブジェクトを指定します。<a href="#JSONinput">JSON 入力の指定</a>を参照してください。<em><code>GET</code> 要求ではサポートされません。</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em><code>GET</code> に必須</em></td>
    <td style="text-align:center">照会</td>
    <td style="text-align:center">ストリング</td>
    <td>
      分析対象のコンテンツを含むプレーン・テキスト入力。入力を URL にエンコードする必要があります。<em><code>POST</code> 要求ではサポートされません。</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em><code>POST</code> に必須</em></td>
    <td style="text-align:center">ヘッダー</td>
    <td style="text-align:center">ストリング</td>
    <td>
      要求のコンテンツ・タイプ:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          プレーン・テキストの場合は <code>text/plain</code>
        </li>
        <li style="margin:0px; padding:0px">
            HTML のテキストの場合は <code>text/html</code> (サービスは HTML タグを削除し、テキストのコンテンツのみ分析します)
        </li>
        <li style="margin:0px; padding:0px">
          JSON 形式のテキストの場合は <code>application/json</code>
        </li>
      </ul>
    <em><code>GET</code> 要求の場合は省略してください。</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>必須</em></td>
    <td style="text-align:center">照会</td>
    <td style="text-align:center">ストリング</td>
    <td>
      応答形式の要求バージョン。<code>YYYY-MM-DD</code> 形式の日付を使用します。例えば、2017 年 9 月 21 日の場合は、<code>2017-09-21</code> を指定します。
</td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>オプション</em></td>
    <td style="text-align:center">ヘッダー</td>
    <td style="text-align:center">ストリング</td>
    <td>
      入力コンテンツの言語:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (英語 (デフォルト))
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code> (フランス語)
        </li>
      </ul>
      地域バリエーションはその親言語として扱われます。例えば、<code>en-US</code> は <code>en</code> と解釈されます。入力コンテンツは、指定した言語と一致しなければなりません。
両方の言語を含むコンテンツを送信しないでください。
入力と応答に異なる言語を使用できます。
</td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>オプション</em></td>
    <td style="text-align:center">ヘッダー</td>
    <td style="text-align:center">ストリング</td>
    <td>
      目的の応答言語:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (アラビア語)
        </li>
        <li style="margin:0px; padding:0px">
          de (ドイツ語)
        </li>
        <li style="margin:0px; padding:0px">
          en (英語 (デフォルト))
        </li>
        <li style="margin:0px; padding:0px">
          es (スペイン語)
        </li>
        <li style="margin:0px; padding:0px">
          fr (フランス語)
        </li>
        <li style="margin:0px; padding:0px">
          it (イタリア語)
        </li>
        <li style="margin:0px; padding:0px">
          ja (日本語)
        </li>
        <li style="margin:0px; padding:0px">
          ko (韓国語)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (ブラジル・ポルトガル語)
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (中国語 (簡体字))
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (中国語 (繁体字))
        </li>
      </ul>
      2 文字の引数の場合、地域バリエーションはその親言語として扱われます。例えば、<code>en-US</code> は <code>en</code> と解釈されます。入力と応答に異なる言語を使用できます。
</td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>オプション</em></td>
    <td style="text-align:center">照会</td>
    <td style="text-align:center">ブール値</td>
    <td>
      ドキュメント全体の分析に加えて個々のセンテンスの分析をサービスから返すかどうかを指定します。
<code>true</code> (デフォルト) の場合、サービスは各センテンスの結果を返します。
</td>
  </tr>
</table>

送信する入力コンテンツは合計 128 KB 以下で、センテンス数は 1000 以下にしてください。サービスは、ドキュメント・レベルの分析として最初の 1000 センテンスを分析し、センテンス・レベルの分析として最初の 100 センテンスのみ分析します。どちらの制限を超えた場合も、応答の一部として `warning` フィールドが返されます。ただし、要求は HTTP 応答コード 200 で成功します。

### 要求の例
{: #exampleRequests}

次の cURL コマンド例は、HTTP `POST` 要求メソッドを使用して汎用エンドポイントを呼び出します。入力ファイルとして <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> を、バージョンとして `2017-09-21` を指定しています。この例では、ドキュメント全体と各センテンスの両方の分析を要求しています。

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

次のコマンド例は、上記の例と同じですが、HTTP `GET` 要求メソッドを使用します。

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

追加の例については、[入門チュートリアル](/docs/services/tone-analyzer/getting-started.html)を参照してください。

### 文字セットの指定
{: #charset}

デフォルトでは、サービスは以下の文字セットを入力コンテンツに使用します。

-   *プレーン・テキスト・コンテンツと HTML コンテンツの場合、*サービスは、HTTP バージョン 1.1 仕様に従って、国際標準化機構 (ISO)-8859-1 文字セット (事実上 ASCII 文字セット) を使用します。
-   *JSON コンテンツの場合、*サービスは、International Engineering Task Force (IETF) [Request for Comment (RFC) 7159 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window} のセクション 8.1 に従って、Unicode Transformation Format (UTF)-8 文字セットを事実上常に使用します。

プレーン・テキスト・コンテンツまたは HTML コンテンツを送信する場合は、`Content-Type` ヘッダーに `charset` パラメーターを含めて、入力テキストの文字エンコード方式を指定してください。次の例は、プレーン・テキスト入力に UTF-8 文字エンコードを指定しています。

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

`charset` パラメーターを使用することで、非 ASCII 文字や印刷不能文字に関連して起こり得る問題を防止できます。文字セットを指定せずに UTF-8 データを渡すと、特殊文字のために正しくない結果が返されたり、HTTP 4*nn* エラーや 5*nn* エラーが返されたりすることがあります。

cURL を使用する場合に同じようなエラーを防止するために、常に `curl` コマンドの `--data-binary` オプションを使用してコンテンツを渡して、コンテンツの UTF-8 エンコードを維持してください。`--data` オプションを使用して ASCII としてコンテンツを渡した場合、コマンドはその入力を処理できますが、UTF-8 でエンコードされたデータに問題が起こる可能性があります。

## JSON 入力の指定
{: #JSONinput}

`POST` 要求メソッドを使用して JSON 入力を分析するには、次のシンプルな形式で JSON `ToneInput` オブジェクトをメソッドに渡します。

```javascript
{
  "text": ""
}
```
{: codeblock}

次の例は、[入門チュートリアル](/docs/services/tone-analyzer/getting-started.html)の中の例で使用している <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="外部リンク・アイコン" title="外部リンク・アイコン" class="style-scope doc-content"></a> ファイルのコンテンツを示しています。このファイルには、ある人が記述したテキストの段落が 1 つ含まれています (次のテキストでは読みやすいように改行していますが、実際の入力には改行を入れないでください)。

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## JSON 応答コンテンツ
{: #JSONresponse}

サービスは JSON オブジェクト `ToneAnalysis` を返します。このオブジェクトには常に `document_tone` フィールドが含まれます。このフィールドには、入力ドキュメント全体の分析を示す `DocumentAnalysis` オブジェクトが含まれます。このオブジェクトには単一のフィールド `tones` が含まれ、ドキュメントのトーンとして該当するトーンごとに分析結果が示されます。

要求の `sentences` パラメーターが省略されたか `true` に設定された場合、応答には `sentences_tone` フィールドも含まれます。このフィールドには `SentenceAnalysis` オブジェクトで構成された配列が含まれ、各オブジェクトには入力コンテンツの 1 つのセンテンスについての以下の情報が入っています。

-   `sentence_id` (整数) は、センテンスの固有 ID を示します。最初のセンテンスの ID は 0 で、その後のセンテンスの ID は 1 つずつ増えていきます。
-   `text` (ストリング) は、センテンスのテキストを示します。
-   `tones` は、センテンスのトーンとして該当するトーンの分析結果を示します。

次の例は、`ToneAnalysis` オブジェクトの大まかな構造を示しています。

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

### トーンとスコアの結果

ドキュメント・レベルの分析でもセンテンス・レベルの分析でも返される `tones` フィールドには、`ToneScore` オブジェクトの配列が含まれます。この配列は、支配的なトーン (スコアが 0.5 以上のトーン) の結果を示します。このしきい値を満たすスコアのトーンが 1 つもない場合、配列は空になります。各 `ToneScore` オブジェクトには、該当するトーンに関する以下の情報が示されます。

-   `score` (倍精度浮動小数点数) は、0.5 から 1 までの範囲のトーンのスコアです。0.75 より大きいスコアは、コンテンツでそのトーンが受け取られる可能性が高いことを示します。
-   `tone_id` (ストリング) は、トーンの (ローカライズされない) 固有 ID です。各トーンの説明については、[汎用トーン](#tones)を参照してください。
-   `tone_name` (ストリング) は、ユーザーに表示されるトーンのローカライズ名です。

次の例は、`ToneScore` オブジェクトの構造を示しています。

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

### 応答の例
{: #exampleResponse}

前の[要求の例](#exampleRequests)に対して、次の出力が返されます ([入門チュートリアル](/docs/services/tone-analyzer/getting-started.html)の最初の例でも同じ出力が返されます)。応答には、ドキュメント全体の結果とセンテンスごとの結果が含まれます。報告されるトーンはすべてスコアが 0.5 以上のものです。スコアが 0.75 以上のトーンは、コンテンツでそのトーンが受け取られる可能性が非常に高いものです。

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

## 汎用トーン
{: #tones}

次の表は、サービスが返すことができる汎用トーンを示しています。スコアが 0.5 未満の場合は、コンテンツでそのトーンの感情が受け取られる可能性が低いことを示し、このようなトーンは省略されます。0.75 より大きいスコアは、そのトーンが受け取られる可能性が高いことを示します。

<table>
  <caption>表 2. 汎用トーン</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">トーン / ID</th>
    <th style="text-align:left">説明</th>
  </tr>
  <tr>
    <td>怒り<br/><code>anger</code></td>
    <td>
      怒りは、不当行為、対立、屈辱、怠慢、裏切りから呼び起こされます。
能動的な怒りの場合、人は言葉や暴力でターゲットを攻撃します。
受動的な怒りの場合、人は黙って不機嫌になり、緊張と敵意を感じます。
(感情トーン)
    </td>
  </tr>
  <tr>
    <td>不安<br/><code>fear</code></td>
    <td>
      不安は、差し迫った危険に対する反応です。これは、何らかの負の刺激に対する反応として引き起こされる生存メカニズムです。
不安は、軽い用心である場合や、極度の恐怖である場合があります。
(感情トーン)
    </td>
  </tr>
  <tr>
    <td>喜び<br/><code>joy</code></td>
    <td>
      喜び (つまり幸福) には、楽しみ、満足、娯楽という微妙な違いがあります。
喜びは、幸福、心の平穏、愛、安全、安心という感覚をもたらします。
(感情トーン)
    </td>
  </tr>
  <tr>
    <td>悲しみ<br/><code>sadness</code></td>
    <td>
      悲しみは、喪失と損害の感情を示します。人が静かで、意欲的でなく、引きこもっているときは、悲しみを感じているということを推測できます。
(感情トーン)
    </td>
  </tr>
  <tr>
    <td>分析的<br/><code>analytical</code></td>
    <td>
      分析的トーンは、物事に対する人の論理的思考と分析的態度を示します。
分析的な人は、知的、理性的、きちょうめん、無感情、あるいは冷淡であると受け取られる可能性があります。
(言語トーン)
    </td>
  </tr>
  <tr>
    <td>自信<br/><code>confident</code></td>
    <td>
      自信トーンは、人の確信の度合いを示します。自信のある人は、堂々としている、落ち着いている、希望に満ちている、あるいは尊大であると受け取られる可能性があります。
(言語トーン)
    </td>
  </tr>
  <tr>
    <td>ためらい<br/><code>tentative</code></td>
    <td>
      ためらいトーンは、人の内気さの度合いを示します。ためらう人は、不審、はっきりしない、あるいは疑わしいと受け取られる可能性があります。
(言語トーン)
    </td>
  </tr>
</table>
