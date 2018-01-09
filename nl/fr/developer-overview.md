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

# Présentation pour les développeurs
{: #overviewDevelopers}

Vous pouvez accéder aux fonctionnalités du service {{site.data.keyword.toneanalyzershort}} via une API HTTP REST (Representational State Transfer). Plusieurs kits de développement de logiciels (SDK) sont également disponibles pour simplifier le développement d'applications dans divers langages et environnements. Les sections suivantes donnent un aperçu du développement d'application avec le service.
{: shortdesc}

## Programmation avec le service
{: #programming}

Pour analyser le ton du texte d'un individu, transmettez au service le texte en entrée via la méthode `GET` ou `POST /v3/tone`. Pour analyser les échanges au sein d'une conversation, transmettez au service l'entrée via la méthode `POST /v3/tone_chat`. Dans les deux cas, le service renvoie son analyse au format JSON.

Pour plus d'informations, voir [Utilisation du noeud final générique](/docs/services/tone-analyzer/using-tone.html) et [Utilisation du noeud final d'interaction avec les clients](/docs/services/tone-analyzer/using-tone-chat.html).

## Utilisation de kits de développement de logiciels (SDK)
{: #sdks}

Le service {{site.data.keyword.toneanalyzershort}} prend en charge plusieurs SDK en vue de simplifier le développement d'application. Des SDK sont disponibles pour de nombreux langages de programmation et interfaces populaires, notamment Node.js, Java, Python et Apple&reg; iOS. Pour la liste complète de ces SDK et les informations relatives à leur utilisation, voir [SDK {{site.data.keyword.watson}}](/docs/services/watson/getting-started-sdks.html). Tous ces SDK sont disponibles sur le site GitHub [watson-developer-cloud namespace ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud){: new_window}.

Pour le développement destiné aux appareils mobiles, voir [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}. Tous les SDK prennent en charge l'authentification via vos données d'identification pour le service ou via un jeton d'authentification.

## En savoir plus sur le développement d'applications
{: #learn}

Le service {{site.data.keyword.toneanalyzershort}} prend en charge deux modèles de programmation courants : *Interaction directe*, dans lequel le client communique directement avec le service et *Relais via un proxy*, dans lequel le client et le service échangent toutes les données (requêtes et résultats) par le biais d'une application proxy résidant dans {{site.data.keyword.Bluemix_short}}.

Pour plus d'informations sur l'utilisation des services {{site.data.keyword.watson}} Developer Cloud avec {{site.data.keyword.Bluemix_notm}}, reportez-vous aux sources suivantes :

-   Pour une introduction à l'utilisation des services {{site.data.keyword.watson}} avec {{site.data.keyword.Bluemix_notm}}, voir [Initiation à {{site.data.keyword.watson}} et {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   Pour une introduction indépendante du langage au développement d'applications de services {{site.data.keyword.watson}} dans {{site.data.keyword.Bluemix_notm}}, voir [Approches de développement {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/getting-started-bluemix.html).
-   Pour plus d'informations sur les deux modèles de programmation disponibles pour les applications {{site.data.keyword.watson}}, voir [Modèles de programmation pour les services {{site.data.keyword.watson}}](/docs/services/watson/getting-started-develop.html):
    -   Lors d'un relais via un proxy, le client s'en remet à un serveur proxy résidant dans {{site.data.keyword.Bluemix_notm}} pour communiquer avec le service et transmet toutes ses requêtes via l'application proxy. Le relais de requêtes via un proxy s'appuie uniquement sur les données d'identification pour le service pour s'authentifier auprès du service. Voir [Données d'identification pour les services {{site.data.keyword.watson}}](/docs/services/watson/getting-started-credentials.html).
    -   En interaction directe, le client n'utilise l'application proxy dans {{site.data.keyword.Bluemix_notm}} que pour obtenir un jeton d'authentification pour le service, après quoi il communique directement avec le service. L'interaction directe n'utilise les données d'identification pour le service que pour obtenir un jeton. Voir [Jetons pour authentification](/docs/services/watson/getting-started-tokens.html).
-   Pour plus d'informations sur le contrôle de la journalisation par défaut des requêtes effectuée pour tous les services {{site.data.keyword.watson}}, voir [Contrôle de la journalisation des requêtes pour les services {{site.data.keyword.watson}}](/docs/services/watson/getting-started-logging.html).
