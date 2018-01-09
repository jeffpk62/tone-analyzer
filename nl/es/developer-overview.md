---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-09"

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

# Visión general para los desarrolladores
{: #overviewDevelopers}

Puede acceder a las prestaciones del servicio {{site.data.keyword.toneanalyzershort}} a través de una API REST (Representational State Transfer) HTTP. También dispone de varios SDK (Software Development Kits) para simplificar el desarrollo de aplicaciones en diversos lenguajes y entornos. En las secciones siguientes se proporciona una visión general del desarrollo de aplicaciones con el servicio.
{: shortdesc}

## Programación con el servicio
{: #programming}

Para analizar el tono del texto de un individuo, debe pasar el texto de entrada al servicio mediante `GET` o `POST /v3/tone`. Para analizar los intercambios en una conversación, puede pasar la entrada al servicio mediante el método `POST /v3/tone_chat`. En ambos casos, el servicio devuelve su análisis en formato JSON.

Para obtener más información, consulte [Utilización del punto final de finalidad general](/docs/services/tone-analyzer/using-tone.html) y [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer/using-tone-chat.html).

## Utilización de los SDK (Software Development Kits)
{: #sdks}

El servicio {{site.data.keyword.toneanalyzershort}} da soporte a varios SDK para simplificar el desarrollo de aplicaciones. Los SDK están disponibles para varios lenguajes y plataformas ampliamente utilizados, que incluyen Node.js, Java, Python y Apple&reg; iOS. Para ver una lista completa de los SDK e información sobre cómo utilizarlos, consulte [SDK de {{site.data.keyword.watson}}](/docs/services/watson/getting-started-sdks.html). Todos los SDK están disponibles en el [espacio de nombres watson-developer-cloud![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud){: new_window} en GitHub.

Para el desarrollo móvil, consulte [SDK de {{site.data.keyword.watson}} Developer Cloud Swift![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}. Todos los SDK permiten la autenticación mediante sus credenciales de servicio o mediante una señal de autenticación.

## Más información sobre el desarrollo de aplicaciones
{: #learn}

El servicio {{site.data.keyword.toneanalyzershort}} da soporte a dos modelos de programación típicos: *Interacción directa*, en el que el cliente se comunica directamente con el servicio, y *comunicación mediante un proxy*, en el que el cliente y el servicio intercambian todos los datos (solicitudes y resultados) a través de una aplicación de proxy que reside en {{site.data.keyword.Bluemix_short}}.

Para obtener más información sobre cómo trabajar con los servicios de {{site.data.keyword.watson}} Developer Cloud y {{site.data.keyword.Bluemix_notm}}, consulte lo siguiente:

-   Para ver una introducción en la que se explica cómo trabajar con servicios {{site.data.keyword.watson}} y {{site.data.keyword.Bluemix_notm}}, consulte [Iniciación a {{site.data.keyword.watson}} y {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   Para ver una introducción independiente del lenguaje para desarrollar aplicaciones de servicios {{site.data.keyword.watson}} en {{site.data.keyword.Bluemix_notm}}, consulte [Enfoques sobre el desarrollo en {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/getting-started-bluemix.html).
-   Para obtener información sobre los dos modelos de programación disponibles para desarrollar aplicaciones {{site.data.keyword.watson}}, consulte [Modelos de programación para servicios {{site.data.keyword.watson}}](/docs/services/watson/getting-started-develop.html):
    -   Con el sistema de comunicación mediante un proxy, el cliente se basa en un servidor proxy que reside en {{site.data.keyword.Bluemix_notm}} para comunicarse con el servicio; pasa todas las solicitudes a través de la aplicación proxy. La comunicación de solicitudes a través de un proxy se basa solo en las credenciales del servicio para autenticarse con el servicio; consulte [Credenciales de servicio para los servicios {{site.data.keyword.watson}}](/docs/services/watson/getting-started-credentials.html).
    -   Con la interacción directa, el cliente solo utiliza la aplicación proxy de {{site.data.keyword.Bluemix_notm}} para obtener una señal de autenticación para el servicio, tras lo cual se comunica directamente con el servicio. La interacción directa utiliza las credenciales de servicio solo para obtener una señal; consulte [Señales de autenticación](/docs/services/watson/getting-started-tokens.html).
-   Para obtener información sobre cómo controlar el registro predeterminado de solicitudes que se realiza para todos los servicios {{site.data.keyword.watson}}, consulte [Control del registro de solicitudes para los servicios {{site.data.keyword.watson}}](/docs/services/watson/getting-started-logging.html).
