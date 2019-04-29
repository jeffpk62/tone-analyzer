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
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Guía de aprendizaje de iniciación
{: #gettingStarted}

El servicio {{site.data.keyword.toneanalyzershort}} analiza el tono del contenido de las entradas. En esta guía de aprendizaje se muestran los mandatos que analizan distinto contenido de ejemplo. Se muestran ejemplos del punto final de finalidad general y del punto final de fidelización del cliente.
{: shortdesc}

La guía de aprendizaje utiliza las teclas de API de {{site.data.keyword.cloud}} Identity and Access Management (IAM) para la autenticación. Las instancias de servicio más antiguas pueden seguir utilizando `{username}` y `{password}` de sus credenciales de servicio de Cloud Foundry existentes para la autenticación. Realice la autenticación utilizando el método correcto para su instancia de servicio. Para obtener más información sobre el uso del servicio de autenticación de IAM, consulte las [Notas del release](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
{: important}

## Antes de empezar
{: #prerequisites}

- {: hide-dashboard}  Cree una instancia del servicio:
    1.  {: hide-dashboard} Vaya a la página [{{site.data.keyword.toneanalyzershort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} en el catálogo de {{site.data.keyword.cloud_notm}}.
    1.  {: hide-dashboard} Regístrese para obtener una cuenta de {{site.data.keyword.cloud_notm}} gratuita o inicie sesión.
    1.  {: hide-dashboard} Pulse **Crear**.
-   Copie las credenciales para autenticarse en la instancia de servicio:
    1.  {: hide-dashboard} En el panel de control de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/dashboard/apps){: new_window}, pulse en la instancia de servicio de {{site.data.keyword.toneanalyzershort}} para ir a la página de panel de control del servicio {{site.data.keyword.toneanalyzershort}}.
    1.  En la página **Gestionar**, pulse **Mostrar** para visualizar las credenciales.
    1.  Copie los valores de `Clave de API` y `URL`.
-   Asegúrese de tener el mandato `curl`.
    -   Los ejemplos utilizan el mandato `curl` para llamar a métodos de la interfaz HTTP. Instale la versión correspondiente a su sistema operativo desde [curl.haxx.se ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://curl.haxx.se/){: new_window}. Instale la versión que da soporte al protocolo SSL (Secure Sockets Layer). Asegúrese de incluir el archivo binario instalado en la variable de entorno `PATH`.

Cuando especifique un mandato, sustituya `{apikey}` y `{url}` por la clave de API y el URL reales. Omita las llaves, que indican un valor variable, en el mandato. Un valor real se asemeja al ejemplo siguiente:
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## Paso 1: Uso del punto final de finalidad general mediante el método de solicitud POST
{: #generalPurposePost}

Los siguientes mandatos llaman al método `POST /v3/tone` para analizar el contenido del archivo `tone.json`. El archivo incluye un solo párrafo de texto sin formato escrito por una persona. En los ejemplos se muestran los parámetros de consulta `sentences` del método.

1.  Descargue el archivo de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>.
1.  Emita el mandato siguiente para analizar el tono del contenido general y de cada frase individual.
    -   {: hide-dashboard} Sustituya `{apikey}` y `{url}` por su información.
    -   Modifique `{path_to_file}` para especificar la ubicación del archivo `tone.json`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  Emita el mandato siguiente para analizar el tono del contenido general estableciendo solo el parámetro `sentences` en `false`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

Para ver un ejemplo del resultado del método, consulte [Respuesta de ejemplo](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone).

## Paso 2: Uso del punto final de finalidad general mediante el método de solicitud GET
{: #generalPurposeGet}

La interfaz también ofrece un método `GET /v3/tone`. El método `GET` proporciona la misma funcionalidad y produce los mismos resultados que el método `POST`, pero se utiliza el parámetro de consulta `text` del método para especificar el contenido que se va a analizar. El método solo acepta entrada de texto sin formato.

1.  El siguiente ejemplo especifica el texto del archivo `tone.json` mediante el parámetro `text`; tal como se muestra, debe codificar el texto en URL. El mandato omite el parámetro `sentences`, de modo que devuelve el mismo resultado que el primer ejemplo de `POST` mostrado anteriormente. (El ejemplo incluye saltos de página para facilitar su lectura; no los incluya en el mandato real.)

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## Paso 3: Uso del punto final de fidelización del cliente
{: #customerEngagement}

El siguiente mandato llama al método `POST /v3/tone_chat` para analizar el contenido del archivo `tone-chat.json`. El archivo incluye un breve intercambio de mensajes entre dos personas, un cliente (<code>customer</code>) y un agente (<code>agent</code>).

1.  Descargue el archivo de ejemplo <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icono de enlace externo" title="Icono de enlace externo"></a>.
1.  Emita el mandato siguiente para analizar el tono del intercambio en el archivo de ejemplo.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

La respuesta del servicio indica los tonos más frecuentes detectados para cada expresión de la entrada. Para ver el contenido de la respuesta correspondiente a esta solicitud, consulte la [Respuesta de ejemplo](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat).

## Siguientes pasos
{: #gsns}

-   Para obtener más información sobre el método `/v3/tone`, consulte [Utilización del punto final de finalidad general](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe).
-   Para obtener más información sobre el método `/v3/tone_chat`, consulte [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco).
-   Para obtener más información sobre los métodos de la interfaz del servicio, consulte la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
