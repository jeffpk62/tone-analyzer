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

# Usando o terminal de engajamento do cliente

O terminal de engajamento do cliente do {{site.data.keyword.toneanalyzershort}} analisa o tom das conversas do atendimento ao cliente e do suporte. Pode ajudá-lo a entender melhor suas interações com clientes e melhorar suas comunicações em geral ou com clientes específicos. Para obter informações detalhadas sobre a interface, incluindo os SDKs de Node.js, Java e Python que estão disponíveis para chamar o serviço, consulte a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Solicitando uma análise de tom
{: #request}

Para analisar tom com o terminal de engajamento do cliente, você chama o método `POST /v3/tone_chat` com os parâmetros a seguir.

<table>
  <caption>Tabela 1. Parâmetros do método <code>POST /v3/tone_chat</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parâmetro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo de dados</th>
    <th style="text-align:left">Descrição</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Necessário</em></td>
    <td style="text-align:center">Corpo</td>
    <td style="text-align:center">Objeto JSON</td>
    <td>
      Um objeto JSON <code>ToneChatInput</code> que contém o conteúdo a ser analisado. Consulte <a href="#JSONrequest">Especificando a entrada JSON</a>.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Necessário</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Sequência</td>
    <td>
      A versão solicitada da interface como uma data no formato <code>YYYY-MM-DD</code>; por exemplo, especifique <code>2017-09-21</code> para 21 de setembro de 2017.
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
    </td>
  </tr>
</table>

Se você enviar mais de 50 elocuções, o serviço retornará um campo `warning` para o conteúdo geral no nível de `utterances_tone` de sua resposta; ele analisará apenas as primeiras 50 elocuções. Se você enviar uma única elocução com mais de 500 caracteres, o serviço retornará um campo `error` para essa elocução e não a analisará. Em ambos os casos, a solicitação ainda é bem-sucedida com o código de resposta HTTP 200.

> **Nota:** o serviço retornará o código de resposta 400 se todas as elocuções da entrada tiverem mais de 500 caracteres.

### Solicitação de exemplo
{: #exampleRequest}

O comando cURL de exemplo a seguir chama o terminal de engajamento do cliente com o arquivo de entrada <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a> e uma versão de `2017-09-21`:

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Especificando entrada em JSON
{: #JSONrequest}

Você passa ao método um objeto JSON `ToneChatInput` com o formato a seguir. O campo `utterances` fornece uma matriz de objetos `utterance`, em que `text` é uma sequência necessária que fornece uma elocução de contribuição de um usuário para a conversa que deve ser analisada e `user` é uma sequência opcional que identifica o usuário que fez a contribuição da elocução.

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

O exemplo a seguir mostra o conteúdo do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo" class="style-scope doc-content"></a>. O arquivo inclui uma breve troca entre um <code>customer</code> e um <code>agent</code>.

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

## Conteúdo de resposta em JSON
{: #JSONresponse}

O serviço retorna um objeto JSON `UtteranceAnalyses` que contém um único campo, `utterances_tone`. Esse campo contém uma matriz de objetos `UtteranceAnalysis`, cada um fornecendo as informações a seguir sobre uma elocução do conteúdo de entrada:

-   `utterance_id` (número inteiro) fornece o identificador exclusivo da elocução. A primeira elocução tem o ID 0 e o ID de cada elocução subsequente é incrementado em um.
-   `utterance_text` (sequência) fornece o texto da elocução.
-   `tones` é uma matriz de objetos `ToneChatScore` que fornece resultados para os tons dominantes, aqueles cujas pontuações são de pelo menos 0,5. A matriz estará vazia se a elocução não tiver nenhum tom com uma pontuação que atenda a esse limite.

Cada objeto `ToneChatScore` fornece as informações a seguir sobre um tom de qualificação:

-   `score` (duplo) é a pontuação do tom no intervalo de 0,5 a 1. Uma pontuação maior que 0,75 indica uma alta probabilidade de o tom ser percebido na elocução.
-   `tone_id` (sequência) é o identificador único e não localizado do tom; para obter descrições dos tons, consulte [Tons de engajamento do cliente](#tones).
-   `tone_name` (sequência) é o nome localizado do tom visível para o usuário.

O exemplo a seguir mostra a estrutura do objeto `UtterancesAnalyses`:

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

### Resposta de exemplo
{: #exampleResponse}

A saída a seguir é retornada para a [Solicitação de exemplo](#exampleRequest). (A mesma saída é retornada para o exemplo no [Tutorial de introdução](/docs/services/tone-analyzer/getting-started.html#customerEngagement).) Todos os tons relatados têm uma pontuação de pelo menos 0,5; aqueles com uma pontuação de pelo menos 0,75 muito provavelmente serão percebidos por participantes na conversa.

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

## Tons de engajamento do cliente
{: #tones}

O serviço pode retornar pontuações para os sete tons a seguir.

<table style="width:90%">
  <caption>Tabela 2. Tons de engajamento do cliente</caption>
  <tr>
    <th style="text-align:left; width:20%">Tom/ID</th>
    <th style="text-align:left">Descrição</th>
  </tr>
  <tr>
    <td>Animado<br/><code>excited</code></td>
    <td>
      Mostrando entusiasmo e interesse pessoais
    </td>
  </tr>
  <tr>
    <td>Frustrado<br/><code>frustrated</code></td>
    <td>
      Definido como se sentindo chateado e irritado
    </td>
  </tr>
  <tr>
    <td>Indelicado<br/><code>impolite</code></td>
    <td>
      Sendo desrespeitoso e rude
    </td>
  </tr>
  <tr>
    <td>Gentil<br/><code>polite</code></td>
    <td>
      Definido como comportamento racional e objetivo
    </td>
  </tr>
  <tr>
    <td>Triste<br/><code>sad</code></td>
    <td>
      Considerada como uma emoção passiva desagradável
    </td>
  </tr>
  <tr>
    <td>Satisfeito<br/><code>satisfied</code></td>
    <td>
      Uma resposta afetiva à qualidade do serviço percebida
    </td>
  </tr>
  <tr>
    <td>Compreensivo<br/><code>sympathetic</code></td>
    <td>
      Um modo afetivo de compreensão que envolve ressonância emocional
    </td>
  </tr>
</table>
