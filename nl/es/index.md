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

# Acerca de

> **Actualización del servicio:** *El servicio{{site.data.keyword.toneanalyzershort}} se ha actualizado el 25 y el 28 de septiembre de 2017. Para el punto final de finalidad propósito general, se ha modificado tanto los parámetros de solicitud como contenido de la respuesta; además, el punto final ya no devuelve los tonos sociales o el tono de repulsión, y ahora acepta entradas en francés. Los límites de entrada y de limitación se han modificado para ambos puntos finales, al igual que la versión de la interfaz. Ahora el servicio acepta una entrada parcialmente correcta en lugar de devolver un error para la solicitud general. Para obtener más información sobre estos y otros cambios, consulte las [Notas del release](/docs/services/tone-analyzer/release-notes.html).*

El servicio {{site.data.keyword.toneanalyzerfull}} utiliza el análisis lingüístico para detectar tonos emocionales y de lenguaje en texto escrito. El servicio puede analizar el tono a nivel de documento y de frase. Puede utilizar el servicio para comprender cómo se perciben sus comunicaciones por escrito y mejorar el tono de sus comunicaciones. Las empresas pueden utilizar el servicio para obtener el tono de las comunicaciones de sus clientes y responder a cada cliente adecuadamente, o para comprender y mejorar las conversaciones con los cliente en general.
{: shortdesc}

Se envía al servicio entrada JSON, de texto sin formato o HTML con el contenido escrito. El servicio acepta hasta 128 KB de texto, lo que equivale a unas 1000 frases. El servicio devuelve resultados JSON que indican el tono de la entrada. Puede utilizar estos resultados para mejorar la percepción y la eficacia de sus comunicaciones, asegurándose de que sus escritos se ajustan al tono y al estilo que desea para el público al que va destinado. En el diagrama siguiente se muestra el flujo básico de llamadas al servicio.

![Envíe contenido al servicio Tone Analyzer y utilice los resultados para mejorar sus comunicaciones.](images/tone-analyzer.png)

## Puntos finales de Tone Analyzer

El servicio ofrece dos puntos finales:

-   **Punto final de finalidad general** (`GET` o `POST /v3/tone`)

    Utilice el punto final de finalidad general de {{site.data.keyword.toneanalyzershort}} para analizar datos web breves, como mensajes de correo electrónico o tweets, o documentos más largos, como artículos o publicaciones de blogs. Supervise las redes sociales para comprender lo que dicen los clientes sobre una marca y para determinar a quién debe dirigir un tipo determinado de mensajes. El punto final acepta entradas JSON, en texto sin formato o HTML. Para obtener más información sobre el método y los tonos que devuelve, consulte [Utilización del punto final de finalidad general](/docs/services/tone-analyzer/using-tone.html).

    La [demo de finalidad general ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://tone-analyzer-demo.ng.bluemix.net/){: new_window} le permite enviar contenido al servicio para que lo analice. El servicio devuelve un análisis general y a nivel de frase del tono del contenido.
-   **Punto final de fidelización del cliente** (`POST /v3/tone_chat`)

    Utilice el punto final de fidelización del cliente de {{site.data.keyword.toneanalyzershort}} para analizar el servicio al cliente y las conversaciones de soporte. Puede transferir las conversaciones del cliente a otro nivel cuando el tono se vuelve más agrio o buscar oportunidades para mejorar los scripts del servicio de soporte, las estrategias de diálogo y la ruta de navegación del cliente. El punto final acepta entradas JSON. Para obtener más información sobre el método y los tonos que devuelve, consulte [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer/using-tone-chat.html).

    La [demo de fidelización del cliente ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://customer-engagement-analytics.mybluemix.net/){: new_window} analiza conversaciones entre cliente y agentes del servicio al cliente. El servicio evalúa el nivel de satisfacción del cliente y sus preocupaciones y el rendimiento de los agentes y permite ver la evolución de la interacción.

Para obtener información sobre los planes de precios disponibles para el servicio, consulte el servicio [{{site.data.keyword.toneanalyzershort}} en el Catálogo de {{site.data.keyword.Bluemix_short}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/catalog/services/tone-analyzer){: new_window}.

## Casos prácticos

A continuación se muestran algunos casos prácticos interesantes del servicio:

-   *Supervisión de redes sociales y de audiencia:* Supervise las redes sociales para comprender lo que dicen los clientes sobre su marca en tiempo real. Por ejemplo, puede determinar que los clientes de Chicago están tristes después de que pierdan los Bulls o contentos durante el festival Taste of Chicago. (Punto final de finalidad general)
-   *Marketing personalizado:* Determine a quién y cuándo dirigir mensajes personalizados. Por ejemplo, una agencia de viajes puede dirigir a los clientes contentos el mensaje "mímese", a los clientes tristes el mensaje "escápese" y a los clientes enfadados el mensaje "relájese". (Punto final de finalidad general)
-   *Bots de chat: * Permite que un agente automático detecte tonos de los clientes y genere respuestas adecuadas. Por ejemplo, puede responder ante un tono triste con el mensaje "Sentimos que se haya producido este" o ante un tono de satisfacción con el mensaje "Nos alegramos de que esté satisfecho con nuestro servicio". (Punto final de fidelización del cliente)
-   *Supervisión de la fidelización del cliente y garantía de servicio:* Supervise el tono general de las comunicaciones entre un agente y un cliente, detecte anomalías y descubra oportunidades para formar a sus agentes para que mejoren su comunicación. (Punto final de fidelización del cliente)

También puede utilizar el servicio {{site.data.keyword.toneanalyzershort}} con otros servicios {{site.data.keyword.ibmwatson_notm}}, como [{{site.data.keyword.conversationfull}}](https://console.bluemix.net/docs/services/conversation/index.html) o [{{site.data.keyword.speechtotextfull}}](https://console.bluemix.net/docs/services/speech-to-text/index.html), para analizar las entradas de los usuarios. Por ejemplo, la aplicación [Conversation Food Coach ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://food-coach.mybluemix.net/){: new_window} utiliza el servicio {{site.data.keyword.conversationshort}} para asesorar a los usuarios para que elijan alimentos saludables en sus respuestas sobre su tipo de alimentación. Para obtener más información, consulte esta [publicación del blog de Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/watson/blog/2016/10/17/creating-a-compassionate-conversational-agent-using-watson-tone-analyzer-and-watson-conversation-services/){: new_window}.

> **Nota:** El servicio {{site.data.keyword.toneanalyzershort}} calcula el tono del texto escrito utilizando un algoritmo. No saca ninguna conclusión sobre la personalidad del autor del texto. Para obtener un perfil de personalidad, consulte el servicio [{{site.data.keyword.personalityinsightsfull}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/services/personality-insights/index.html){: new_window}.

## Soporte de idiomas
{: #languages}

el método `/v3/tone` puede analizar contenido en inglés (`en`) y en francés (`fr`); el método `/v3/tone_chat` solo da soporte al inglés. Ambos métodos pueden responder con contenido traducido a diversos idiomas. Para obtener más información, consulte [Utilización del punto final de finalidad general](/docs/services/tone-analyzer/using-tone.html) y [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer/using-tone-chat.html).
