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

# Guía de aprendizaje de iniciación

El servicio {{site.data.keyword.toneanalyzershort}} analiza el tono del contenido de las entradas. En esta guía de aprendizaje se muestran los mandatos que analizan distinto contenido de ejemplo. Los ejemplos muestran puntos finales de finalidad general y de fidelización del cliente.
{: shortdesc}

## Antes de empezar
{: #prerequisites}

- Cree una instancia del servicio:
    - {: download} Si ve esto, significa que ha creado la instancia del servicio. Ahora obtenga sus credenciales.
    - Cree un proyecto a partir de un servicio:
        1.  Vaya a la consola del desarrollador de {{site.data.keyword.watson}}, a la página [Servicios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Seleccione {{site.data.keyword.toneanalyzershort}}, pulse **Añadir servicios** y regístrese para una cuenta gratuita de {{site.data.keyword.Bluemix_notm}} o inicie una sesión.
        1.  Escriba `tone-tutorial` como nombre del proyecto y pulse **Crear proyecto**.
- Copie las credenciales para autenticarse en la instancia del servicio:
    - {: download} En el panel de control del servicio (lo que está viendo):
        1.  Pulse el separador **Credenciales de servicio**.
        1.  Pulse **Ver credenciales** bajo **Acciones**.
        1.  Copie los valores de `username`, `password` y `url`.
        {: download}
    - En el proyecto **tone-tutorial** de la consola del desarrollador, copie los valores de `username`,  `password` y `url` correspondientes a `"tone_analyzer"` de la sección **Credenciales**.
- Asegúrese de que tiene cURL:
    - En los ejemplos se utiliza cURL para llamar a métodos de la interfaz HTTP. Instale la versión correspondiente a su sistema operativo desde [curl.haxx.se ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://curl.haxx.se/){: new_window}. Instale la versión que da soporte al protocolo SSL (Secure Sockets Layer). Asegúrese de incluir el archivo binario instalado en su variable de entorno `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si utiliza {{site.data.keyword.Bluemix_dedicated_notm}}, cree la instancia del servicio desde la página [{{site.data.keyword.toneanalyzershort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} en el catálogo. Para obtener más información sobre cómo encontrar las credenciales de servicio, consulte [Credenciales de servicio para servicios Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Paso 1: Utilizar el punto final de finalidad general mediante el método de solicitud POST
{: #generalPurposePost}

Los siguientes mandatos llaman al método `POST /v3/tone` para analizar el contenido del archivo `tone.json`. El archivo incluye un solo párrafo de texto sin formato escrito por una persona. En los ejemplos se muestran los parámetros de consulta `sentences` del método.

1.  Descargue el archivo de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Emita el mandato siguiente para analizar el tono del contenido general y de cada frase individual.
    -   Sustituya `{username}` y `{password}` por las credenciales de servicio del paso anterior.
    -   Modifique `{path_to_file}` para especificar la ubicación del archivo `tone.json`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Emita el mandato siguiente para analizar el tono del contenido general estableciendo solo el parámetro `sentences` en `false`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

Para ver un ejemplo del resultado del método, consulte [Respuesta de ejemplo](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Paso 2: Utilizar el punto final de finalidad general mediante el método de solicitud GET
{: #generalPurposeGet}

La interfaz también ofrece un método `GET /v3/tone`. El método `GET` proporciona la misma funcionalidad y produce los mismos resultados que el método `POST`, pero se utiliza el parámetro de consulta `text` del método para especificar el contenido que se va a analizar. El método solo acepta entrada de texto sin formato.

1.  El siguiente ejemplo especifica el texto del archivo `tone.json` mediante el parámetro `text`; tal como se muestra, debe codificar el texto en URL. El mandato omite el parámetro `sentences`, de modo que devuelve el mismo resultado que el primer ejemplo de `POST` mostrado anteriormente. (El ejemplo incluye saltos de página para facilitar su lectura; no los incluya en el mandato real.)

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Paso 3: Utilizar el punto final de fidelización del cliente
{: #customerEngagement}

El siguiente mandato llama al método `POST /v3/tone_chat` para analizar el contenido del archivo `tone-chat.json`. El archivo incluye un breve intercambio de mensajes entre dos personas, un cliente (<code>customer</code>) y un agente (<code>agent</code>).

1.  Descargue el archivo de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo" class="style-scope doc-content"></a>.
1.  Emita el mandato siguiente para analizar el tono del intercambio en el archivo de ejemplo.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

La respuesta del servicio indica los tonos más frecuentes detectados para cada expresión de la entrada. Para ver el contenido de la respuesta correspondiente a esta solicitud, consulte la [Respuesta de ejemplo](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Siguientes pasos

-   Para obtener más información sobre el método `/v3/tone`, consulte [Utilización del punto final de finalidad general](/docs/services/tone-analyzer/using-tone.html).
-   Para obtener más información sobre el método `/v3/tone_chat`, consulte [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer/using-tone-chat.html).
-   Para ver más información sobre los métodos de la interfaz del servicio, revise la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Puede interactuar con la API en el [Explorador de API![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}.
