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
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Usando o terminal de engajamento do cliente
{: #utco}

O terminal de engajamento do cliente {{site.data.keyword.toneanalyzershort}} analisa o tom do atendimento ao cliente e das conversas de suporte. Pode ajudá-lo a entender melhor suas interações com clientes e melhorar suas comunicações em geral ou com clientes específicos. Para obter mais informações sobre a interface, incluindo os SDKs
do Node.js, Java e Python que estão disponíveis para chamar o serviço, veja a [Referência da API ![Ícone de link externo](../../icons/launch-glyph.svg "Íconede link externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

{: shortdesc}

A criação de log da solicitação está desativada para o serviço {{site.data.keyword.toneanalyzershort}}. Independentemente de você configurar o cabeçalho
da solicitação `X-Watson-Learning-Opt-Out`, o serviço não registra nem retém
dados de solicitações e respostas.
{: note}

## Solicitando uma análise de tom
{: #request-tone-chat}

Para analisar o tom com o terminal de engajamento do cliente, você chama o método `POST /v3/tone_chat` com os parâmetros a seguir.

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
      Um objeto JSON <code>ToneChatInput</code> com o conteúdo que
      deve ser analisado. Para obter mais informações, veja [Especificando a entrada JSON](#JSONrequest).
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Necessário</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Sequência</td>
    <td>
      A versão da API que você deseja usar como uma data no formato
      <code>YYYY-MM-DD</code>; por exemplo, especifique <code>2017-09-21</code>
      para 21 de setembro de 2017 (a versão mais recente). Para obter mais informações sobre todas as versões disponíveis, consulte as [Notas sobre a liberação](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Opcional </em></td>
    <td style="text-align:center">Cabeçalho</td>
    <td style="text-align:center">Sequência</td>
    <td>
      O idioma do conteúdo de entrada.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (Inglês, o padrão)
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
      O idioma solicitado da resposta.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code> (árabe)
        </li>
        <li style="margin:0px; padding:0px">
          <code>de</code>
(Alemão)
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code> (Inglês, o padrão)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code>
(Espanhol)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (Francês)
        </li>
        <li style="margin:0px; padding:0px">
          <code>it</code>
(Italiano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code> (Japonês)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code>
(Coreano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code> (português do Brasil)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code> (chinês simplificado)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code> (chinês tradicional)
        </li>
      </ul>
      Para argumentos de dois caracteres, variantes regionais são tratadas como seu idioma pai; por exemplo, <code>en-US</code> é interpretada como <code>en</code>. É possível usar diferentes idiomas para a entrada e a resposta.
    </td>
  </tr>
</table>

Se você enviar mais de 50 elocuções, o serviço retornará um campo `warning` para o conteúdo geral no nível de `utterances_tone` de sua resposta; ele analisará apenas as primeiras 50 elocuções. Se você enviar uma única elocução com mais de 500 caracteres, o serviço retornará um campo `error` para essa elocução e não a analisará. Em ambos os casos, a solicitação ainda é bem-sucedida com o código de resposta HTTP 200.

O serviço retornará o código de resposta 400 se todas as elocuções da entrada tiverem mais
de 500 caracteres.
{: note}

### Solicitação de exemplo
{: #exampleRequest}

O comando `curl` de exemplo a seguir chama o terminal de engajamento do cliente
com o arquivo de entrada <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a> e uma
versão de `2017-09-21`:

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Especificando entrada em JSON
{: #JSONrequest}

Você passa ao método um objeto JSON `ToneChatInput` com o formato a seguir. O
campo `utterances` fornece uma matriz de objetos `utterance`. O campo `text` é uma sequência obrigatória que fornece uma elocução cuja contribuição foi feita por um
usuário para a conversa que será analisada. O campo `user` é uma sequência opcional que identifica o usuário que contribuiu com a elocução.

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

O exemplo a seguir mostra o conteúdo do arquivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Ícone de link externo" title="Ícone de link externo"></a>. O arquivo inclui uma breve troca entre um <code>customer</code> e um <code>agent</code>.

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
{: #JSONresponse-tone-chat}

O serviço retorna um objeto JSON `UtteranceAnalyses` que contém um único campo, `utterances_tone`. Esse campo contém uma matriz de objetos `UtteranceAnalysis`, cada um fornecendo as informações a seguir sobre uma elocução do conteúdo de entrada:

-   `utterance_id` (número inteiro) fornece o identificador exclusivo da elocução. A primeira elocução tem o ID 0 e o ID de cada elocução subsequente é incrementado em um.
-   `utterance_text` (sequência) fornece o texto da elocução.
-   `tones` é uma matriz de objetos `ToneChatScore` que fornece resultados para os tons dominantes. Esses tons têm pontuações de pelo menos 0,5. A matriz estará vazia se a elocução não tiver nenhum tom com uma pontuação que atenda a esse limite.

Cada objeto `ToneChatScore` fornece as informações a seguir sobre um tom de qualificação:

-   `score` (duplo) é a pontuação do tom no intervalo de 0,5 a 1. Uma pontuação maior que 0,75 indica uma alta probabilidade de o tom ser percebido na elocução.
-   `tone_id` (sequência) é o identificador exclusivo e não localizado do tom. Para obter descrições dos tons, veja [Tons de engajamento do cliente](#tones-tone-chat).
-   `tone_name` (sequência) é o nome localizado do tom visível para o usuário.

O exemplo a seguir mostra a estrutura do objeto `UtteranceAnalyses`:

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
{: #exampleResponse-tone-chat}

A saída a seguir é retornada para a [Solicitação de exemplo](#exampleRequest). (A mesma saída é retornada para o exemplo no [Tutorial de introdução](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted#customerEngagement).) Todos os tons relatados têm uma pontuação de pelo menos 0,5. Os tons com uma pontuação
de pelo menos 0,75 são percebidos pelos participantes da conversa.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.686361,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": [
        {
          "score": 0.92724,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997795,
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
          "score": 0.730982,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.672499,
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
{: #tones-tone-chat}

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
