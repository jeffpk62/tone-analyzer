---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

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

# Notas del release

En las siguientes secciones se documentan las nuevas características y los cambios que se han incluido para cada release del servicio {{site.data.keyword.toneanalyzershort}}. Los cambios no modifican el código existente.
{: shortdesc}

> **Nota:** Ahora las notas del release documentan la *versión del servicio* y la *versión de la interfaz* para cada actualización. La *versión de la interfaz* se especifica con el parámetro de consulta `version` y sirve para utilizar las nuevas características y funciones disponibles con dicha actualización. El servicio devuelve ambas versiones con la cabecera de respuesta `X-Service-API-Version`.

## 28 de septiembre de 2017
{: #September2017b}

**Versión del servicio: ** `3.4.1`<br/> **Versión de la interfaz:** `2017-09-21`

-   El límite sobre el número máximo de solicitudes que puede enviar un nombre de usuario de {{site.data.keyword.Bluemix_notm}} individual se ha aumentado a 1200 solicitudes por minuto. El servicio devuelve el código de respuesta de HTTP 429 *Demasiadas solicitudes* si un usuario supera este límite.

## 25 de septiembre de 2017
{: #September2017a}

**Versión del servicio: ** `3.4.1`<br/> **Versión de la interfaz:** `2017-09-21`

-   El punto final de finalidad general (método `/v3/tone`) se ha modificado de la siguiente manera:

    -   Da soporte a contenido de entradas en francés (`fr`) además de en inglés.
    -   Ya no devuelve tonos sociales.
    -   Ya no devuelve `disgust` (repulsa) con tonos de emociones.
    -   Omite cualquier tono cuya puntuación es inferior a `0.5`. Esta calificación coincide con la respuesta del método `/v3/tone_chat`.
    - Ya no devuelve categorías de tonos (el campo `tone_categories`) como parte de su salida. Todos los tonos cuyos valores cumplan con el umbral de calificación se devuelven como parte de un solo objeto `tones`. Como antes, los tonos siempre se devuelve para el documento completo y para cada una de las frases individuales de forma predeterminada.
    - Ya no acepta un parámetro de consulta `tones` para limitar la salida a los tonos especificados. Para cada solicitud se devuelven todos los tonos que califican. La inclusión del parámetro con una solicitud no genera un error, pero no tiene ningún efecto en la respuesta.
    - Ya no devuelve los campos `input_from` y `input_to` para frases individuales. Además de los resultados de su análisis, ahora el método ahora solo devuelve un ID y el texto de cada frase.

-   Ahora el servicio devuelve el código de respuesta HTTP 200 en lugar de 400 si la entrada es parcialmente correcta en los casos siguientes:

    -   Para el método `/v3/tone`, si envía más de 128 KB o más de 1000 frases de contenido de entrada, el servicio devuelve un campo `warning` como parte de su respuesta. El servicio analiza las 1000 primeras frases para el análisis a nivel de documento y, tal como hace actualmente, solo las 100 primeras frases para el análisis a nivel de frase. Las versiones anteriores del servicio devolvían el código de respuesta 400 para la solicitud si se superaba alguno de estos límites. Tenga también en cuenta que ahora el servicio analiza las frases que tienen menos de tres palabras.
    -   Para el método `/v3/tone_chat`, si envía más de 50 expresiones, el servicio devuelve un campo `warning` para el contenido general a nivel de `utterances_tone` de la respuesta; solo analiza las 50 primeras expresiones. Si envía una sola expresión que contiene más de 500 caracteres, el servicio devuelve un campo `error` para dicha expresión y no la analiza. Las versiones anteriores del servicio devolvían el código de respuesta 400 si se superaba alguno de estos límites. Tenga en cuenta que si todas las expresiones de la entrada tienen más de 500 caracteres, el servicio sigue devolviendo el código de respuesta 400 para la solicitud.

-   Ahora el servicio regula el número de solicitudes que acepta de un solo usuario. El servicio devuelve el código de respuesta HTTP 429 *Demasiadas solicitudes* si recibe más de 600 solicitudes por minuto de un determinado nombre de usuario de {{site.data.keyword.Bluemix_notm}}.

-   Los cambios siguientes se aplican a los puntos finales tanto de finalidad general como de fidelización del cliente:

    -   La versión de la interfaz especificada con el parámetro `version` es `2017-09-21` para utilizar la última versión del servicio.
    -   La documentación se ha actualizado para señalar que el servicio puede producir salida traducida a diversos idiomas. Utilice la cabecera de solicitud `Accept-Language` para especificar el idioma deseado.

## 6 de julio de 2017
{: #July2017b}

**Versión del servicio: ** `3.3.6`<br/> **Versión de la interfaz:** `2016-05-19`

El servicio se ha actualizado para solucionar un pequeño defecto del punto final de fidelización del cliente.

## Releases anteriores

-   [1 de julio de 2017](#July2017a)
-   [8 de mayo de 2017](#May2017)
-   [17 de abril de 2017](#April2017)
-   [15 de marzo de 2017](#March2017)
-   [1 de diciembre de 2016](#December2016)
-   [18 de octubre de 2016](#October2016b)
-   [3 de octubre de 2016](#October2016a)
-   [19 de mayo de 2016](#May2016)

### 1 de julio de 2017
{: #July2017a}

**Versión del servicio: ** `3.3.5`<br/> **Versión de la interfaz:** `2016-05-19`

El punto final de fidelización del cliente del servicio {{site.data.keyword.toneanalyzershort}} está ahora disponible a nivel general (GA). Todas las llamadas al punto final se cargan a la misma velocidad que las llamadas al punto final de finalidad general.

### 8 de mayo de 2017
{: #May2017}

**Versión del servicio: ** `3.3.4`<br/> **Versión de la interfaz:** `2016-05-19`

IBM ha actualizado los modelos de puntuación del tono de las emociones y del tono de fidelización de asistencia al cliente para mejorar el conjunto de datos de formación. Ahora los modelos ofrecen una mayor precisión en el conjunto de datos de pruebas comparativas.

### 17 de abril de 2017
{: #April2017}

-   Ahora está disponible u n nuevo conjunto de tonos específicos del ámbito de fidelización del cliente: *frustrado*, *satisfecho*, *entusiasmado*, *cortés*, *descortés*, *triste* y *empático*. El servicio detecta estos tonos a partir del texto de una conversación entre un cliente y un agente. Los tonos son actualmente funciones beta.
-   IBM saca al mercado actualizaciones al modelo de puntuación del tono de las emociones que mejoren los resultados del análisis de emociones.

### 15 de marzo de 2017
{: #March2017}

IBM ha actualizado el modelo de puntuación del tono de las emociones. Se ha ampliado el conjunto de datos de formación. Como resultado, ahora los modelos ofrecen una mayor precisión en el conjunto de datos de pruebas comparativas.

### 1 de diciembre de 2016
{: #December2016}

IBM ha actualizado las puntuaciones del tono de las emociones de documentos. El nuevo modelo tiene en cuenta el perfil de emoción de las frases para sumar la puntuación de un documento.

### 18 de octubre de 2016
{: #October2016b}

IBM ha mejorado el tono social. Ahora el servicio utiliza una técnica de inclusión de palabras de código abierto denominada [GloVe ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://nlp.stanford.edu/projects/glove/){: new_window} para inferir puntuaciones del tono social. Este cambio permite que el servicio cubra un vocabulario de palabras más amplio cuando evalúa los tonos sociales. Para obtener más información sobre cómo se infiere un tono social, consulte [La ciencia subyacente al servicio](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) para el servicio {{site.data.keyword.personalityinsightsshort}}.

### 3 de octubre de 2016
{: #October2016a}

IBM ha mejorado la detección de emociones a nivel de frase. El servicio utiliza nuevos datos de formación, un nuevo proceso de selección de características y un mayor repertorio de palabras, emojis y de jerga. Estos cambios generan puntuaciones de las emociones distintas y significativamente mejores a nivel de frase. La API del servicio no se ha modificado.

### 19 de mayo de 2016
{: #May2016}

El release disponible a nivel general (GA) del servicio {{site.data.keyword.toneanalyzershort}} incluye estas nuevas características:

-   Los modelos del servicio tienen más en cuenta el contexto para interpretar un tono. Ahora los modelos utilizan algo más que solo señales léxicas. Ahora tienen en cuenta características adicionales, como la puntuación, los emoticonos y parámetros del lenguaje, como la estructura y la complejidad de las frases.
-   Se ha cambiado el nombre del modelo de tono de escritura por tono del lenguaje.
-   Ahora los modelos de lenguaje y de tono de emociones pueden gestionar negaciones.
-   El servicio ya no devuelve una respuesta para las frases con menos de tres palabras.
-   Ahora el servicio dispone de una [demo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://tone-analyzer-demo.mybluemix.net){: new_window} simplificada y mejorada.
