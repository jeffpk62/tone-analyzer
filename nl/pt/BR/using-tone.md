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

# Usando o terminal de propósito geral

O terminal de propósito geral do {{site.data.keyword.toneanalyzershort}} analisa o tom de comunicações por escrito, de mensagens curtas de e-mail até documentos mais longos. Ele pode ajudar a entender os tons emocionais e de linguagem de suas comunicações. Para obter informações detalhadas sobre a interface, incluindo os SDKs de Node.js, Java e Python que estão disponíveis para chamar o serviço, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Solicitando uma análise de tom
{: #request}

Para analisar o tom com o terminal de propósito geral, você chama uma das duas versões do método `tone` do serviço:

-   O método `POST /v3/tone` aceita conteúdo de entrada em formato JSON, texto sem formatação ou HTML por meio do corpo necessário da solicitação. Use essa versão do método para texto mais longo ou para texto que você não deseja expor na URL.
-   O método `GET /v3/tone` aceita conteúdo de entrada por meio de seu parâmetro de consulta `text` necessário. Use essa versão do método para texto simples que é facilmente acomodado na URL.

Os métodos aceitam os parâmetros a seguir.

<table>
  <caption>Tabela 1. Parâmetros dos métodos <code>/v3/tone</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parâmetro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo de dados</th>
    <th style="text-align:left">Descrição</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Necessário para <code>POST</code></em></td>
    <td style="text-align:center">Corpo</td>
    <td style="text-align:center">Objeto JSON | Sequência</td>
    <td>
      Entrada em JSON, texto sem formatação ou HTML que contém o conteúdo a ser analisado.
Para entrada em JSON, forneça um objeto do tipo <code>ToneInput</code>; consulte <a href="#JSONinput">Especificando entrada em JSON</a>. <em>Não suportado para solicitações <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Necessário para <code>GET</code></em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Sequência</td>
    <td>
      Entrada de texto sem formatação que contém o conteúdo a ser analisado. Deve-se codificar a entrada pela URL. <em>Não suportado para solicitações <code>POST</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>Conteúdo-tipo</code><br/><em>Necessário para <code>POST</code></em></td>
    <td style="text-align:center">Cabeçalho</td>
    <td style="text-align:center">Sequência</td>
    <td>
      O tipo de conteúdo da solicitação:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> para texto sem formatação
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> para texto em HTML (o serviço remove as tags HTML e analisa apenas o conteúdo textual)
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> para texto em formato JSON
        </li>
      </ul>
    <em>Omitir para solicitações <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Necessário</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Sequência</td>
    <td>
      A versão solicitada do formato de resposta como uma data no formato <code>YYYY-MM-DD</code>; por exemplo, especifique <code>2017-09-21</code> para 21 de setembro de 2017.
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Opcional </em></td>
    <td style="text-align:center">Cabeçalho</td>
    <td style="text-align:center">Sequência</td>
    <td>
      O idioma do conteúdo de entrada:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (inglês, o padrão)
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code> (Francês)
        </li>
      </ul>
      Variantes regionais são tratadas como seu idioma pai; por exemplo, <code>en-US</code> é interpretada como <code>en</code>. O conteúdo de entrada deve corresponder ao idioma especificado. Não envie conteúdo que contenha ambos os idiomas. É possível usar diferentes idiomas para a entrada e a resposta.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Opcional </em></td>
    <td style="text-align:center">Cabeçalho</td>
    <td style="text-align:center">Sequência</td>
    <td>
      O idioma desejado da resposta:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (árabe)
        </li>
        <li style="margin:0px; padding:0px">
          de (alemão)
        </li>
        <li style="margin:0px; padding:0px">
          en (inglês, o padrão)
        </li>
        <li style="margin:0px; padding:0px">
          es (espanhol)
        </li>
        <li style="margin:0px; padding:0px">
          fr (francês)
        </li>
        <li style="margin:0px; padding:0px">
          it (italiano)
        </li>
        <li style="margin:0px; padding:0px">
          ja (japonês)
        </li>
        <li style="margin:0px; padding:0px">
          ko (coreano)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (português do Brasil)
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (chinês simplificado)
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (chinês tradicional)
        </li>
      </ul>
      Para argumentos de dois caracteres, variantes regionais são tratadas como seu idioma pai; por exemplo, <code>en-US</code> é interpretada como <code>en</code>. É possível usar diferentes idiomas para a entrada e a resposta.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>Opcional </em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Booleano</td>
    <td>
      Indica se o serviço deve retornar uma análise de cada sentença individual além da sua análise do documento completo.
      Se <code>true</code> (o padrão), o serviço retornará resultados para cada sentença.
    </td>
  </tr>
</table>

Envie no máximo 128 KB de conteúdo de entrada total e no máximo 1000 sentenças individuais. O serviço analisa as primeiras 1000 sentenças para análise no nível de documento e apenas as primeiras 100 sentenças para análise no nível da sentença. Ele retornará um campo `warning` como parte de sua resposta se você exceder o limite; a solicitação ainda será bem-sucedida com o código de resposta HTTP 200.

### Solicitações de exemplo
{: #exampleRequests}

O comando cURL de exemplo a seguir usa o método de solicitação HTTP `POST` para chamar o terminal de propósito geral com o arquivo de entrada <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> e uma versão de `2017-09-21`. O exemplo solicita uma análise do documento completo e das sentenças individuais.

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

O exemplo de comando a seguir é equivalente ao exemplo anterior, mas usa o método de solicitação HTTP `GET`:

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

Para obter exemplos adicionais, consulte o [Tutorial de introdução](/docs/services/tone-analyzer/getting-started.html).

### Especificando o conjunto de caracteres
{: #charset}

Por padrão, o serviço usa os conjuntos de caracteres a seguir para conteúdo de entrada:

-   *Para conteúdo em texto sem formatação e HTML,* o serviço usa o conjunto de caracteres da Organização de Normas Internacionais (ISO)-8859-1 (efetivamente o conjunto de caracteres ASCII) de acordo com a especificação de HTTP versão 1.1.
-   *Para conteúdo em JSON,* o serviço sempre usa efetivamente o conjunto de caracteres Unicode Transformation Format (UTF)-8 de acordo com a Seção 8.1 da International Engineering Task Force (IETF) [Solicitação de Comentários (RFC) 7159 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

Ao enviar conteúdo em texto sem formatação ou HTML, inclua o parâmetro `charset` com o cabeçalho `Content-Type` para indicar a codificação de caracteres do texto de entrada. O exemplo a seguir especifica a codificação de caracteres UTF-8 para entrada de texto sem formatação:

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

Usando o parâmetro `charset`, é possível evitar problemas em potencial associados a caracteres não ASCII ou não imprimíveis. Se você passar dados UTF-8 sem especificar o conjunto de caracteres, caracteres especiais poderão apresentar resultados incorretos ou erros de HTTP 4*nn* ou de 5*nn*.

Para evitar erros semelhantes ao usar cURL, sempre passe o conteúdo por meio da opção `--data-binary` do comando `curl` para preservar qualquer codificação UTF-8 do conteúdo. Se você usar a opção `--data` para passar o conteúdo como ASCII, o comando poderá processar a entrada, o que poderá causar problemas para dados codificados em UTF-8.

## Especificando entrada em JSON
{: #JSONinput}

Para analisar a entrada em JSON com o método de solicitação `POST`, você passa ao método um objeto JSON `ToneInput` com o formato simples a seguir:

```javascript
{
  "text": ""
}
```
{: codeblock}

O exemplo a seguir mostra o conteúdo do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> que é usado com os exemplos no [Tutorial de introdução](/docs/services/tone-analyzer/getting-started.html). O arquivo inclui um único parágrafo de texto escrito por uma pessoa. (O texto a seguir inclui quebras de linha para capacidade de leitura; não as inclua na entrada real.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## Conteúdo de resposta em JSON
{: #JSONresponse}

O serviço retorna um objeto JSON `ToneAnalysis` que sempre contém um campo `document_tone`. Esse campo contém um objeto `DocumentAnalysis` que fornece a análise do documento de entrada completo. Ele contém um único campo, `tones`, que fornece os resultados da análise de cada tom de qualificação do documento.

Se o parâmetro `sentences` da solicitação for omitido ou configurado para `true`, a resposta também incluirá um campo `sentences_tone`. Esse campo contém uma matriz de objetos `SentenceAnalysis`, cada um dos quais fornece as informações a seguir para uma sentença diferente do conteúdo de entrada:

-   `sentence_id` (número inteiro) fornece o identificador exclusivo da sentença. A primeira sentença tem o ID 0 e o ID de cada sentença subsequente é incrementado em um.
-   `text` (sequência) fornece o texto da sentença.
-   `tones` fornece os resultados da análise de cada tom de qualificação da sentença.

O exemplo a seguir mostra a estrutura de alto nível do objeto `ToneAnalysis`:

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

### Resultados de tons e pontuações

Os campos `tones` que são retornados para as análises no nível do documento e da sentença contêm uma matriz de objetos `ToneScore` que fornece resultados para os tons dominantes, aqueles cujas pontuações são de pelo menos 0,5. A matriz estará vazia se nenhum tom tiver uma pontuação que atenda a esse limite. Cada objeto `ToneScore` fornece as informações a seguir sobre um tom de qualificação:

-   `score` (duplo) é a pontuação para o tom no intervalo de 0,5 a 1. Uma pontuação maior que 0,75 indica uma alta probabilidade de que o tom será percebido no conteúdo.
-   `tone_id` (sequência) é o identificador exclusivo e não localizado do tom; para obter descrições dos tons, consulte [Tons de propósito geral](#tones).
-   `tone_name` (sequência) é o nome localizado do tom visível para o usuário.

O exemplo a seguir mostra a estrutura do objeto `ToneScore`:

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

### Resposta de exemplo
{: #exampleResponse}

A saída a seguir é retornada para as [Solicitações de exemplo](#exampleRequests). (A mesma saída é retornada para o primeiro exemplo no [Tutorial de introdução](/docs/services/tone-analyzer/getting-started.html).) A resposta inclui resultados para o documento completo e para cada sentença individual. Todos os tons relatados têm uma pontuação de pelo menos 0,5; aqueles com uma pontuação de pelo menos 0,75 muito provavelmente serão percebidos no conteúdo.

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

## Tons de propósito geral
{: #tones}

A tabela a seguir descreve os tons de propósito geral que o serviço pode retornar. Um tom cuja pontuação é menor que 0,5 será omitido, indicando que a emoção provavelmente não será percebida no conteúdo. Uma pontuação maior que 0,75 indica uma alta probabilidade de que o tom será percebido.

<table>
  <caption>Tabela 2. Tons de propósito geral</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Tom/ID</th>
    <th style="text-align:left">Descrição</th>
  </tr>
  <tr>
    <td>Raiva<br/><code>anger</code></td>
    <td>
      Raiva é evocada devido a injustiça, conflito, humilhação, negligência ou traição. Se a raiva é ativa, o indivíduo ataca o alvo verbal ou fisicamente. Se a raiva é passiva, a pessoa se cala de mau humor e sente tensão e hostilidade. (Um tom emocional.)
    </td>
  </tr>
  <tr>
    <td>Medo<br/><code>fear</code></td>
    <td>
      Medo é uma resposta ao perigo iminente. É um mecanismo de sobrevivência que é acionado como uma reação a algum estímulo negativo. Medo pode ser um cuidado leve ou uma fobia extrema. (Um tom emocional.)
    </td>
  </tr>
  <tr>
    <td>Alegria<br/><code>joy</code></td>
    <td>
      Alegria (ou felicidade) tem nuances de apreciação, satisfação e prazer.
      Alegria traz uma sensação de bem-estar, paz interior, amor, segurança e contentamento. (Um tom emocional.)
    </td>
  </tr>
  <tr>
    <td>Tristeza<br/><code>sadness</code></td>
    <td>
      Tristeza indica um sentimento de perda e desvantagem. Quando uma pessoa fica quieta,
menos enérgica e afastada, pode-se inferir que ela sente tristeza. (Um tom emocional.)
    </td>
  </tr>
  <tr>
    <td>Analítico<br/><code>analytical</code></td>
    <td>
      Um tom analítico indica o raciocínio e a atitude analítica de uma pessoa sobre as coisas. Uma pessoa analítica pode ser percebida como intelectual, racional, sistemática, sem emoção ou impessoal. (Um tom de linguagem.)
    </td>
  </tr>
  <tr>
    <td>Confiante<br/><code>confident</code></td>
    <td>
      Um tom confiante indica o grau de certeza de uma pessoa. Uma pessoa confiante pode ser percebida como segura, reservada, esperançosa ou egoísta.
      (Um tom de linguagem.)
    </td>
  </tr>
  <tr>
    <td>Hesitante<br/><code>tentative</code></td>
    <td>
      Um tom hesitante indica o grau de inibição de uma pessoa. Uma pessoa hesitante pode ser percebida como questionável, duvidosa ou discutível. (Um tom de linguagem.)
    </td>
  </tr>
</table>
