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

# Présentation pour les développeurs
{: #overviewDevelopers}

Vous pouvez accéder aux fonctionnalités du service {{site.data.keyword.toneanalyzershort}} via une API HTTP REST (Representational State Transfer). Plusieurs kits de développement de logiciels (SDK) sont également disponibles pour simplifier le développement d'applications dans divers langages. Les sections suivantes donnent un aperçu du développement d'application avec le service.
{: shortdesc}

## Programmation à l'aide du service
{: #programming}

Pour analyser le ton du texte d'un individu, transmettez au service le texte en entrée via la méthode `GET` ou `POST /v3/tone`. Pour analyser les échanges au sein d'une conversation, transmettez au service l'entrée via la méthode `POST /v3/tone_chat`. Dans les deux cas, le service renvoie son analyse au format JSON. Pour plus d'informations, voir 

-   [Utilisation du noeud final générique](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [Utilisation du noeud final d'interaction avec les clients](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Utilisation de kits de développement de logiciels (SDK)
{: #sdks}

Des SDK sont disponibles pour le service {{site.data.keyword.toneanalyzershort}} afin de simplifier le développement d'applications. Les logiciels SDK {{site.data.keyword.ibmwatson}} sont disponibles pour de nombreux langages de programmation et plateformes populaires.

-   Pour obtenir une liste complète des logiciels SDK et des liens vers les logiciels SDK de GitHub, voir [Utilisation de logiciels SDK](/docs/services/watson?topic=watson-using-sdks).
-   Pour des informations détaillées sur toutes les méthodes des SDK Node, Java, Python, Ruby et Go pour le service {{site.data.keyword.toneanalyzershort}}, voir la [Référence d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/tone-analyzer){: new_window}. 

## En savoir plus sur le développement d'applications
{: #learn}

Pour plus d'informations sur l'utilisation des services {{site.data.keyword.watson}} et {{site.data.keyword.cloud}}, reportez-vous aux pages suivantes :

-   Pour une introduction à l'utilisation des services {{site.data.keyword.watson}} avec {{site.data.keyword.cloud_notm}}, voir [Initiation à {{site.data.keyword.watson}} et {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about).
-   Toutes les nouvelles instances de service utilisent {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) pour l'authentification. Les anciennes instances de service peuvent continuer à utiliser les `{username}` et `{password}` de leurs données d'identification de service Cloud Foundry existantes pour l'authentification. Pour plus d'informations sur l'authentification auprès du service, voir la [mise à jour du service du 30 octobre 2018](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018) dans les notes sur l'édition.
-   La consignation des demandes est désactivée pour le service {{site.data.keyword.toneanalyzershort}}. Le service ne consigne pas et ne conserve pas les données des demandes et des réponses, que l'en-tête de requête `X-Watson-Learning-Opt-Out` soit défini ou non. 
