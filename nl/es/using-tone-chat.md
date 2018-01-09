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

# Utilización del punto final de fidelización del cliente

El punto final de fidelización del cliente de {{site.data.keyword.toneanalyzershort}} analiza el tono del servicio al cliente y de las conversaciones de soporte. Puede ayudarle a comprender mejor sus interacciones con los clientes y a mejorar la comunicación en general o la correspondiente a clientes específicos. Para obtener información detallada sobre la interfaz, incluidos los SDK Node.js, Java y Python que están disponibles para llamar al servicio, reviste la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Solicitud de un análisis de tono
{: #request}

Para analizar el tono con el punto final de fidelización del cliente, debe llamar al método `POST /v3/tone_chat` con los parámetros siguientes.

<table>
  <caption>Tabla 1. Parámetros del método <code>POST /v3/tone_chat</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parámetro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo de datos</th>
    <th style="text-align:left">Descripción</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Obligatorio</em></td>
    <td style="text-align:center">Cuerpo</td>
    <td style="text-align:center">Objeto JSON</td>
    <td>
      Un objeto JSON <code>ToneChatInput</code> con el contenido que se va a analizar. Consulte <a href="#JSONrequest">Especificación de la entrada JSON</a>.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obligatorio</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Serie</td>
    <td>
      La versión solicitada de la interfaz como una fecha con el formato
      <code>AAAA-MM-DD</code>; por ejemplo, especifique <code>2017-09-21</code>
      para el 21 de septiembre de 2017.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Opcional</em></td>
    <td style="text-align:center">Cabecera</td>
    <td style="text-align:center">Serie</td>
    <td>
      El idioma deseado de la respuesta:
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (árabe)
        </li>
        <li style="margin:0px; padding:0px">
          de (alemán)
        </li>
        <li style="margin:0px; padding:0px">
          en (inglés, valor predeterminado)
        </li>
        <li style="margin:0px; padding:0px">
          es (español)
        </li>
        <li style="margin:0px; padding:0px">
          fr (francés)
        </li>
        <li style="margin:0px; padding:0px">
          it (italiano)
        </li>
        <li style="margin:0px; padding:0px">
          ja (japonés)
        </li>
        <li style="margin:0px; padding:0px">
          ko (coreano)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (portugués de Brasil)
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (chino simplificado)
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (chino tradicional)
        </li>
      </ul>
    </td>
  </tr>
</table>

Si envía más de 50 expresiones, el servicio devuelve un campo `warning` para el contenido general a nivel de `utterances_tone` de su respuesta; solo analiza las 50 primeras expresiones. Si envía una sola expresión que contiene más de 500 caracteres, el servicio devuelve un campo `error` para dicha expresión y no la analiza. En ambos casos, la solicitud sigue siendo satisfactoria con el código de respuesta HTTP 200.

> **Nota:** El servicio devuelve el código de respuesta 400 si todas las expresiones de la entrada tienen más de 500 caracteres.

### Solicitud de ejemplo
{: #exampleRequest}

El siguiente mandato cURL de ejemplo llama al punto final de fidelización del cliente con el archivo de entrada <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> y una versión de `2017-09-21`:

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Especificación de la entrada JSON
{: #JSONrequest}

Puede pasar al método un objeto JSON `ToneChatInput` con el formato siguiente. El campo `utterances` ofrece una matriz de objetos `utterance`, donde `text` es una serie obligatoria que proporciona una expresión con la que ha contribuido un usuario a la conversación que se va a analizar y `user` es una serie opcional que identifica el usuario que ha contribuido a la expresión.

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

En el ejemplo siguiente se muestra el contenido del archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json.<img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a> El archivo incluye un breve intercambio entre un cliente (<code>customer</code>) y un agente (<code>agent</code>).

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

## Contenido de la respuesta JSON
{: #JSONresponse}

El servicio devuelve un objeto JSON `UtteranceAnalyses` que contiene un solo campo, `utterances_tone`. Este campo contiene una matriz de objetos `UtteranceAnalysis`, cada uno de las cuales proporciona la siguiente información sobre una expresión del contenido de la entrada:

-   `utterance_id` (integer) proporciona el identificador exclusivo de la expresión. La primera expresión tiene el ID 0, y el ID de cada expresión siguiente se incrementa en uno.
-   `utterance_text` (string) proporciona el texto de la expresión.
-   `tones` es una matriz de objetos `ToneChatScore` que proporciona resultados para los tonos dominantes, aquellos cuya puntuación es de al menos 0.5. La matriz está vacía si la expresión no tiene ningún tono con una puntuación que cumpla este umbral.

Cada objeto `ToneChatScore` proporciona la información siguiente sobre un tono que califica:

-   `score` (double) es la puntuación correspondiente al tono comprendido entre 0.5 y 1. Una puntuación mayor que 0.75 indica una alta probabilidad de que el tono se perciba en la expresión.
-   `tone_id` (string) es el identificador exclusivo y no localizado del tono; para ver descripciones de los tonos, consulte [Tonos de fidelización del cliente](#tones).
-   `tone_name` (string) es el nombre del tono localizado que ve el usuario.

En el ejemplo siguiente se muestra la estructura del objeto `UtterancesAnalyses`:

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

### Respuesta de ejemplo
{: #exampleResponse}

Se devuelve la siguiente salida para la [Solicitud de ejemplo](#exampleRequest). (Se devuelve la misma salida para el ejemplo de la [Guía de aprendizaje de iniciación](/docs/services/tone-analyzer/getting-started.html#customerEngagement)). Todos los tonos notificados tienen una puntuación de al menos 0.5; los que tienen una puntuación de al menos 0.75 tienen una alta probabilidad de ser percibidos por los participantes en la conversación.

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

## Tonos de fidelización del cliente
{: #tones}

El servicio puede devolver puntuaciones para los siete tonos siguientes.

<table style="width:90%">
  <caption>Tabla 2. Tonos de fidelización del cliente</caption>
  <tr>
    <th style="text-align:left; width:20%">Tono / ID</th>
    <th style="text-align:left">Descripción</th>
  </tr>
  <tr>
    <td>Entusiasmado<br/><code>excited</code></td>
    <td>
      Muestra entusiasmo e interés personal
    </td>
  </tr>
  <tr>
    <td>Frustrado<br/><code>frustrated</code></td>
    <td>
      Se define cuando alguien está molesto o irritable
    </td>
  </tr>
  <tr>
    <td>Descortés<br/><code>impolite</code></td>
    <td>
      Muestra falta de respeto y mala educación
    </td>
  </tr>
  <tr>
    <td>Cortés<br/><code>polite</code></td>
    <td>
      Comportamiento racional y orientado a un objetivo
    </td>
  </tr>
  <tr>
    <td>Triste<br/><code>sad</code></td>
    <td>
      Emoción pasiva de desagrado
    </td>
  </tr>
  <tr>
    <td>Satisfecho<br/><code>satisfied</code></td>
    <td>
      Una respuesta efectiva a la calidad del servicio percibida
    </td>
  </tr>
  <tr>
    <td>Empático<br/><code>sympathetic</code></td>
    <td>
      Modo afectivo de comprensión que implica resonancia emocional
    </td>
  </tr>
</table>
