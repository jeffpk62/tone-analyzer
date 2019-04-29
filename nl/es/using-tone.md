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

# Utilización del punto final de finalidad general
{: #utgpe}

El punto final de finalidad general de {{site.data.keyword.toneanalyzershort}} analiza el tono de las comunicaciones escritas, desde mensajes breves de correo electrónico a documentos más largos. Le puede ayudar a comprender los tonos emocionales e idiomáticos de sus comunicaciones. Para obtener más información sobre la interfaz, incluidos los SDK Node.js, Java y Python que están disponibles para llamar al servicio, reviste la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
{: shortdesc}

El registro de solicitudes está inhabilitado para el servicio {{site.data.keyword.toneanalyzershort}}. Independientemente de si se establece la cabecera de solicitud `X-Watson-Learning-Opt-Out`, el servicio no registra ni retiene datos de las solicitudes y respuestas.
{: note}

## Solicitud de un análisis de tono
{: #request-tone}

Para analizar el tono con el punto final de finalidad general, debe efectuar una llamada a una de las dos versiones del método `tone` del servicio:

-   El método `POST /v3/tone` acepta contenido de entrada en JSON, texto sin formato o formato HTML mediante un cuerpo obligatorio de la solicitud. Utilice esta versión del método para textos más largos o para texto que ya no desea exponer en el URL.
-   El método `GET /v3/tone` acepta contenido de entrada a través de su parámetro de consulta obligatorio `text`. Utilice esta versión del método de texto sencillo que se acomode fácilmente en el URL.

Los métodos aceptan los parámetros siguientes.

<table>
  <caption>Tabla 1. Parámetros de los métodos <code>/v3/tone</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Parámetro</th>
    <th style="text-align:center; width:12%">Tipo</th>
    <th style="text-align:center; width:20%">Tipo de datos</th>
    <th style="text-align:left">Descripción</th>
  </tr>
  <tr>
    <td><code>Cuerpo</code><br/><em>Obligatorio para <code>POST</code></em></td>
    <td style="text-align:center">Cuerpo</td>
    <td style="text-align:center">Objeto JSON | Serie</td>
    <td>
      Entrada JSON, texto sin formato o HTML con el contenido que se
      va a analizar. Para la entrada JSON, especifique un objeto de tipo
      <code>ToneInput</code>. Para obtener más información, consulte
      [Cómo especificar entrada JSON](#JSONinput). <em>No recibe soporte para solicitudes <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Obligatorio para <code>GET</code></em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Serie</td>
    <td>
      Entrada en texto sin formato con el contenido que se va a analizar. Debe codificar
      la entrada en URL. <em>No recibe soporte para solicitudes <code>POST</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>Obligatorio para <code>POST</code></em></td>
    <td style="text-align:center">Cabecera</td>
    <td style="text-align:center">Serie</td>
    <td>
      El tipo de contenido de la solicitud.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> para texto sin formato
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> para texto en HTML (el servicio elimina los códigos
            HTML y solo analiza el contenido textual)
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> para texto en formato JSON
        </li>
      </ul>
    <em>Omitir para solicitudes <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obligatorio</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Serie</td>
    <td>
      La versión de la API que desea utilizar como una fecha en formato
      <code>AAAA-MM-DD</code>; por ejemplo, especifique <code>2017-09-21</code>
      para indicar el 21 de septiembre de 2017 (la última versión). Para obtener más información acerca de
      todas las versiones disponibles, consulte las
      [Notas del release](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Opcional</em></td>
    <td style="text-align:center">Cabecera</td>
    <td style="text-align:center">Serie</td>
    <td>
      El idioma del contenido de la entrada.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (inglés, valor predeterminado)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (francés)
        </li>
      </ul>
      Las variantes regionales se tratan como su idioma padre; por ejemplo,
      <code>en-US</code> se interpreta como <code>en</code>. El contenido de la entrada
      debe coincidir con el idioma especificado. No envíe contenido que contenga
      ambos idiomas. Puede utilizar diferentes idiomas para la entrada y la respuesta.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Opcional</em></td>
    <td style="text-align:center">Cabecera</td>
    <td style="text-align:center">Serie</td>
    <td>
      El idioma solicitado de la respuesta.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code> (árabe)
        </li>
        <li style="margin:0px; padding:0px">
          <code>de</code> (alemán)
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code> (inglés, valor predeterminado)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code> (español)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (francés)
        </li>
        <li style="margin:0px; padding:0px">
          <code>it</code> (italiano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code> (japonés)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code> (coreano)
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code> (portugués de Brasil)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code> (chino simplificado)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code> (chino tradicional)
        </li>
      </ul>
      Para los argumentos de dos caracteres, las variantes regionales se tratan como su idioma padre; por ejemplo, <code>en-US</code> se interpreta como <code>en</code>. Puede utilizar diferentes idiomas para la entrada y la respuesta.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>Opcional</em></td>
    <td style="text-align:center">Consulta</td>
    <td style="text-align:center">Booleano</td>
    <td>
      Indica si el servicio debe devolver un análisis de cada frase individual, además de su análisis del documento completo.
      Si tiene el valor <code>true</code> (valor predeterminado), el servicio devuelve resultados para cada frase.
    </td>
  </tr>
</table>

No envíe más de 128 KB de contenido total de entrada y no más de 1000 frases individuales. El servicio analiza las 1000 primeras frases para el análisis a nivel de documento y solo las 100 primeras frases para el análisis a nivel de frase. Devuelve un campo `warning` como parte de su respuesta si supera alguno de los límites; la solicitud se ejecuta correctamente con el código de respuesta de HTTP 200.

### Solicitudes de ejemplo
{: #exampleRequests}

El siguiente mandato `curl` de ejemplo utiliza el método de solicitud `POST` de HTTP para llamar al punto final de finalidad general con el archivo de entrada <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a> y una versión de `2017-09-21`. El ejemplo solicita un análisis del documento completo y de las frases individuales.

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

El siguiente mandato de ejemplo es equivalente al ejemplo anterior, pero utiliza el método de solicitud `GET` de HTTP:

```bash
curl -X GET -u "apikey:{apikey}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

Para ver más ejemplos, consulte la [Guía de aprendizaje de iniciación](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted).

### Cómo especificar el juego de caracteres
{: #charset}

De forma predeterminada, el servicio utiliza los siguientes juegos de caracteres para el contenido de entrada:

-   *Para texto sin formato y contenido HTML,* el servicio utiliza el juego de caracteres International Standards Organization (ISO)-8859-1 (en realidad, el juego de caracteres ASCII) de la especificación HTTP versión 1.1.
-   *Para contenido JSON,* el servicio en realidad utiliza siempre el juego de caracteres Unicode Transformation Format (UTF)-8 según la sección 8.1 de International Engineering Task Force (IETF) [Request for Comment (RFC) 7159 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

Cuando envíe texto sin formato o contenido HTML, incluya el parámetro `charset` con la cabecera `Content-Type` para indicar la codificación de caracteres del texto de entrada. En el ejemplo siguiente se especifica la codificación de caracteres UTF-8 para la entrada de texto sin formato:

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

Al utilizar el parámetro `charset`, puede evitar posibles problemas asociados con caracteres no ASCII o no imprimibles. Si pasa datos UTF-8 sin especificar el juego de caracteres, los caracteres especiales pueden dar lugar a resultados incorrectos o de nivel 400- o 500 de HTTP.

Para evitar errores similares al utilizar el mandato `curl`, pase siempre el contenido mediante la opción `--data-binary` del mandato `curl` para conservar la codificación UTF-8 del contenido. Si utiliza la opción `--data` para pasar el contenido como ASCII, el mandato puede procesar la entrada, lo que puede provocar problemas para los datos codificados en UTF-8.

## Cómo especificar entrada JSON
{: #JSONinput}

Para analizar entrada JSON con el método de solicitud `POST`, pase al método un objeto JSON `ToneInput` con el siguiente formato simple:

```javascript
{
  "text": ""
}
```
{: codeblock}

En el ejemplo siguiente se muestra el contenido del archivo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a> que se utiliza en los ejemplos de la [Guía de aprendizaje de iniciación](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted). El archivo incluye un solo párrafo de texto escrito por una persona. (El texto siguiente incluye saltos de página para facilitar su lectura; no los incluya en la entrada real.)

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## Contenido de la respuesta JSON
{: #JSONresponse-tone}

El servicio devuelve un objeto JSON `ToneAnalysis` que siempre contiene un campo `document_tone`. Este campo contiene un objeto `DocumentAnalysis` que proporciona el análisis del documento de entrada completo. Contiene un solo campo, `tones`, que proporciona los resultados del análisis de cada tono del documento que califica.

Si se omite el parámetro `sentences` de la solicitud o se establece en `true`, la respuesta también incluye un campo `sentences_tone`. Este campo contiene una matriz de objetos `SentenceAnalysis`, cada uno de las cuales proporciona la siguiente información para una frase diferente del contenido de la entrada:

-   `sentence_id` (integer) proporciona el identificador exclusivo de la frase. La primera frase tiene el ID 0, y el ID de cada frase siguiente se incrementa en uno.
-   `text` (string) proporciona el texto de la frase.
-   `tones` proporciona los resultados del análisis para cada tono de la frase que califica.

En el ejemplo siguiente se muestra la estructura general del objeto `ToneAnalysis`:

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

### Tono y resultados de la puntuación
{: #uttsr}

Los campos `tones` que se devuelven para análisis tanto a nivel de documento como de frase contienen una matriz de objetos `ToneScore` que proporciona resultados para los tonos dominantes. Estos tonos tienen puntuaciones de al menos 0.5. La matriz está vacía si ningún tono tiene una puntuación que cumpla este umbral. Cada objeto `ToneScore` proporciona la información siguiente sobre un tono que califica:

-   `score` (double) es la puntuación correspondiente al tono comprendido entre 0.5 y 1. Una puntuación mayor que 0.75 indica una alta probabilidad de que el tono se perciba en el contenido.
-   `tone_id` (string) es el identificador exclusivo y no localizado del tono; para ver descripciones de los tonos, consulte [Tonos de finalidad general](#tones-tone).
-   `tone_name` (string) es el nombre del tono localizado que ve el usuario.

En el ejemplo siguiente se muestra la estructura del objeto `ToneScore`:

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

### Respuesta de ejemplo
{: #exampleResponse-tone}

Se devuelve la siguiente salida para las [Solicitudes de ejemplo](#exampleRequests). (Se devuelve la misma salida para el primer ejemplo de la [Guía de aprendizaje de iniciación](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted)). La respuesta incluye resultados correspondientes a todo el documento y a cada frase individual. Todos los tonos notificados tienen una puntuación de al menos 0.5. Los tonos con una puntuación de al menos 0.75 tienen una alta probabilidad de ser percibidos en el contenido.

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

## Tonos de finalidad general
{: #tones-tone}

En la tabla siguiente se describen los tonos de finalidad general que puede devolver el servicio. Los tonos con una puntuación inferior a 0.5 se omiten, lo que indica que es poco probable que la emoción se perciba en el contenido. Una puntuación superior a 0.75 indica una alta probabilidad de que el tono se perciba.

<table>
  <caption>Tabla 2. Tonos de finalidad general</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Tono / ID</th>
    <th style="text-align:left">Descripción</th>
  </tr>
  <tr>
    <td>Ira<br/><code>anger</code></td>
    <td>
      Se evoca la ira con una injusticia, un conflicto, una humillación, una negligencia o una traición. Si la ira está activa, el individuo ataca al objetivo, de forma verbal o física. Si ira es pasiva, la persona se enoja de forma silenciosa y siente tensión y hostilidad. (Un tono emocional.)
    </td>
  </tr>
  <tr>
    <td>Miedo<br/><code>fear</code></td>
    <td>
      El miedo es una respuesta a un peligro inminente. Es un mecanismo de supervivencia que se activa como reacción a un estímulo negativo. El miedo puede ser una advertencia leve o una fobia extrema. (Un tono emocional.)
    </td>
  </tr>
  <tr>
    <td>Alegría<br/><code>joy</code></td>
    <td>
      La alegría (o felicidad) tiene matices de disfrute, satisfacción y placer.
      La alegría aporta una sensación de bienestar, paz interior, amor, seguridad y satisfacción. (Un tono emocional.)
    </td>
  </tr>
  <tr>
    <td>Tristeza<br/><code>sadness</code></td>
    <td>
      La tristeza indica un sentimiento de pérdida y desventaja. Cuando una persona está callada o menos enérgica o se muestra introvertida, se puede inferir que siente tristeza. (Un tono emocional.)
    </td>
  </tr>
  <tr>
    <td>Analítico<br/><code>analytical</code></td>
    <td>
      Un tono analítico indica el razonamiento y la actitud analítica de una persona frente a temas. Una persona analítica podría percibirse como intelectual, racional, sistemática, insensible o impersonal. (Un tono del lenguaje.)
    </td>
  </tr>
  <tr>
    <td>Seguro de uno mismo<br/><code>confident</code></td>
    <td>
      Un tono de autoconfianza indica el grado de seguridad de una persona. Una persona segura podría percibirse como segura, serena, optimista o egoísta.
      (Un tono del lenguaje.)
    </td>
  </tr>
  <tr>
    <td>Indecisión<br/><code>tentative</code></td>
    <td>
      Un tono indeciso indica el grado de inhibición de la persona. Una persona indecisa podría percibirse como cuestionable, dubitativa o discutible. (Un tono del lenguaje.)
    </td>
  </tr>
</table>
