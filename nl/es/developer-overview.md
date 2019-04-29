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

# Visión general para desarrolladores
{: #overviewDevelopers}

Puede acceder a las prestaciones del servicio {{site.data.keyword.toneanalyzershort}} a través de una API REST (Representational State Transfer) HTTP. También hay disponibles varios kits de desarrollo de software (SDK) para simplificar el desarrollo de aplicaciones en varios idiomas. En las secciones siguientes se proporciona una visión general del desarrollo de aplicaciones con el servicio.
{: shortdesc}

## Programación con el servicio
{: #programming}

Para analizar el tono del texto de un individuo, debe pasar el texto de entrada al servicio mediante `GET` o `POST /v3/tone`. Para analizar los intercambios en una conversación, puede pasar la entrada al servicio mediante el método `POST /v3/tone_chat`. En ambos casos, el servicio devuelve su análisis en formato JSON. Para obtener más información, consulte

-   [Utilización del punto final de finalidad general](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [Utilización del punto final de fidelización del cliente](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Utilización de kits de desarrollo de software (SDK)
{: #sdks}

Hay SDK disponibles para el servicio {{site.data.keyword.toneanalyzershort}} para simplificar el desarrollo de aplicaciones. Hay SDK de {{site.data.keyword.ibmwatson}} disponibles para muchos lenguajes de programación y plataformas ampliamente utilizados.

-   Para obtener una lista completa de los SDK y los enlaces a los SDK de GitHub, consulte [Utilización de SDK](/docs/services/watson?topic=watson-using-sdks).
-   Para obtener información detallada sobre todos los métodos de los SDK de Node, Java, Python, Ruby y Go para el servicio {{site.data.keyword.toneanalyzershort}}, consulte la [referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

## Más información sobre el desarrollo de aplicaciones
{: #learn}

Para obtener más información sobre cómo trabajar con los servicios de {{site.data.keyword.watson}} y {{site.data.keyword.cloud}}, consulte las páginas siguientes:

-   Para obtener una introducción de cómo trabajar con los servicios de {{site.data.keyword.watson}} y {{site.data.keyword.cloud_notm}}, consulte [Iniciación a {{site.data.keyword.watson}} y {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about).
-   Todas las instancias de servicio nuevas utilizan {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) para la autenticación. Las instancias de servicio más antiguas pueden seguir utilizando `{username}` y `{password}` de sus credenciales de servicio de Cloud Foundry existentes para la autenticación. Para obtener más información sobre cómo autenticarse para el servicio, consulte [actualización de servicio del 30 de octubre de 2018](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018) en las notas del release.
-   El registro de solicitudes está inhabilitado para el servicio {{site.data.keyword.toneanalyzershort}}. El servicio no registra ni retiene datos de solicitudes y respuestas, independientemente de si se ha establecido la cabecera de la solicitud `X-Watson-Learning-Opt-Out`.
