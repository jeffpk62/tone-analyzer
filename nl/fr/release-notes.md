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

# Notes sur l'édition
{: #rnrn}

Les sections ci-après décrivent les nouvelles fonctions et les modifications introduites dans chaque version du service {{site.data.keyword.toneanalyzershort}}. Les modifications ne perturbent pas le code existant.
{: shortdesc}

Les notes sur l'édition documentent la *version du service* et la *version d'interface* pour chaque mise à jour. Spécifiez la *version d'interface* avec le paramètre de requête `version` pour utiliser les nouvelles fonctions et fonctionnalités rendues disponibles avec cette mise à jour. Le service renvoie les deux versions avec l'en-tête de réponse `X-Service-Api-Version`.
{: note}

## 22 février 2019 
{: #February2019}

**Version du service** - `3.5.9`<br/> **Version d'interface** - `2017-09-21`

-   Le service {{site.data.keyword.toneanalyzershort}} sur le site {{site.data.keyword.cloud}} de Francfort (**eu-de**) utilise désormais une authentification IAM (Identity and Access Management) basée sur des jetons. Toutes les nouvelles instances de service que vous créez sur ce site ou sur tout autre site utilisent l'authentification IAM.
-   Le service a également été mis à jour pour intégrer les modifications et améliorations internes. 

## 18 novembre 2018 
{: #November2018b}

**Version du service** - `3.5.4`<br/> **Version d'interface** - `2017-09-21`

Le service {{site.data.keyword.toneanalyzershort}} est maintenant disponible sur le site {{site.data.keyword.cloud_notm}} de Londres (**eu-gb**). Comme tous les sites, Londres utilise une authentification IAM basée sur des jetons. Toutes les nouvelles instances de service que vous créez à cet emplacement utilisent l'authentification IAM.

## 7 novembre 2018 
{: #November2018a}

**Version du service** - `3.5.4`<br/> **Version d'interface** - `2017-09-21`

Le service {{site.data.keyword.toneanalyzershort}} est maintenant disponible sur le site {{site.data.keyword.cloud_notm}} de Tokyo (**jp-tok**). Comme tous les sites, Tokyo utilise une authentification IAM basée sur des jetons. Toutes les nouvelles instances de service que vous créez à cet emplacement utilisent l'authentification IAM.

## Editions antérieures
{: #rnor}

  - [30 octobre 2018](#30-october-2018)
  - [11 juin 2018](#11-june-2018)
  - [25 mai 2018](#25-may-2018)
  - [13 mars 2018](#13-march-2018)
  - [28 septembre 2017](#28-september-2017)
  - [25 septembre 2017](#25-september-2017)
  - [6 juillet 2017](#6-july-2017)
  - [1 juillet 2017](#1-july-2017)
  - [8 mai 2017](#8-may-2017)
  - [17 avril 2017](#17-april-2017)
  - [15 mars 2017](#15-march-2017)
  - [1 décembre 2016](#1-december-2016)
  - [18 octobre 2016](#18-october-2016)
  - [3 octobre 2016](#3-october-2016)
  - [19 mai 2016](#19-may-2016)

### 30 octobre 2018
{: #October2018}

**Version du service** - `3.5.4`<br/> **Version d'interface** - `2017-09-21`

Le service {{site.data.keyword.toneanalyzershort}} a migré vers une authentification IAM basée sur des jetons pour tous les sites. Tous les services {{site.data.keyword.cloud_notm}} utilisent maintenant l'authentification IAM. Le service {{site.data.keyword.toneanalyzershort}} a migré vers chaque site aux dates suivantes : 

-   Dallas (**us-south**) : 30 octobre 2018
-   Francfort (**eu-de**) : en cours
-   Washington, DC (**us-east**) : 11 juin 2018
-   Sydney (**au-syd**) : 25 mai 2018

Le service continue d'utiliser les données d'identification du service Cloud Foundry pour l'authentification sur le site de Francfort. Cet emplacement va migrer vers l'authentification IAM dès que possible.
{: important}

La migration vers l'authentification IAM affecte différemment les nouvelles instances de service et celles existantes :

-   *Toutes les nouvelles instances de service que vous créez sur n’importe quel site* utilisent désormais l’authentification IAM pour accéder au service. Vous pouvez transmettre un jeton bearer ou une clé d'API : les jetons prennent en charge les demandes authentifiées sans incorporer les données d'identification du service dans chaque appel. Les clés d'PI utilisent l'authentification de base HTTP. Lorsque vous utilisez l'un des logiciels SDK de {{site.data.keyword.watson}}, vous pouvez transmettre la clé d'API et laisser le SDK gérer le cycle de vie des jetons.
-   *Les instances de service existantes que vous avez créées sur un site avant la date de migration indiquée* continuent d'utiliser les `{username}` et `{password}` de leurs données d'identification de service Cloud Foundry précédentes pour l'authentification jusqu'à ce que vous les mettiez à jour pour utiliser l'authentification IAM. Le service {{site.data.keyword.toneanalyzershort}} étant sans état, vous pouvez effectuer les étapes suivantes pour convertir une instance de service existante afin qu'elle utilise l'authentification IAM : 

    1.  Supprimez et recréez l'instance de service. 
    1.  Modifiez le code de votre application pour utiliser l'authentification IAM. 

Pour plus d'informations, voir la documentation suivante :

-   Pour connaître le mécanisme d’authentification utilisé par votre instance de service, affichez vos données d’identification de service en cliquant sur l’instance du [tableau de bord {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/dashboard/apps){: new_window}.
-   Pour plus d'informations sur l'utilisation de jetons IAM avec des services Watson, voir [Authentification avec des jetons IAM](/docs/services/watson?topic=watson-iam).
-   Pour plus d'informations sur l'utilisation de clés d'API IAM avec des services Watson, voir [Clés d'API de service IAM](/docs/services/watson?topic=watson-api-key-bp).
-   Pour consulter des exemples utilisant l’authentification IAM, voir la [Référence d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

### 11 juin 2018
{: #June2018}

**Version du service** - `3.5.4`<br/> **Version d'interface** - `2017-09-21`

Pour les instances de service et les applications hébergées à Washington, DC (**us east**), le service prend désormais en charge un nouveau processus d'authentification par API. Pour plus d'informations, voir la [Mise à jour du service du 30 octobre 2018](#October2018).

### 25 mai 2018
{: #May2018}

**Version du service** - `3.5.4`<br/> **Version d'interface** - `2017-09-21`

Pour les instances de service et les applications hébergées à Sydney (**au-syd**), le service prend désormais en charge un nouveau processus d'authentification par API. Pour plus d'informations, voir la [Mise à jour du service du 30 octobre 2018](#October2018).

### 13 mars 2018 
{: #March2018}

**Version du service** - `3.5.3`<br/> **Version d'interface** - `2017-09-21`

Le service a été mis à jour pour ajouter du contenu d'entrée français (`fr`) en plus de l'anglais pour le noeud final d'interaction avec les clients, `/v3/tone_chat`. Utilisez l'en-tête de demande `Content-Language` pour spécifier une langue ; la langue par défaut est l'anglais américain.

### 28 septembre 2017
{: #September2017b}

**Version du service** - `3.4.1`<br/> **Version d'interface** - `2017-09-21`

Le nombre maximal de demandes qu'un nom d'utilisateur {{site.data.keyword.cloud_notm}} individuel peut soumettre a été porté à 1200 demandes par minute. Le service renvoie le code réponse HTTP 429 *Nombre de demandes trop élevé* si un utilisateur dépasse cette limite.

### 25 septembre 2017
{: #September2017a}

**Version du service** - `3.4.1`<br/> **Version d'interface** - `2017-09-21`

-   Le noeud final générique (méthode `/v3/tone`) a été modifié. 

    -   Prise en charge du français (`fr`) dans le contenu en entrée, en plus de l'anglais.
    -   Les tons sociaux ne sont plus renvoyés.
    -   `disgust` (dégoût) n'est plus renvoyé avec les tons d'émotion.
    -   Omission de tous les tons dont le score est inférieur à `0,5`. Cette qualification correspond à la réponse de la méthode `/v3/tone_chat`.
    - Les catégories de ton (zone `tone_categories`) ne sont plus renvoyées dans le cadre de sa sortie. Tous les tons respectant le seuil de qualification sont renvoyés dans le cadre d'un objet `tones` unique. Comme avant, les tons sont toujours renvoyés par défaut pour le document complet et pour chaque phrase individuelle.
    - Le paramètre de requête `tones` n'est plus accepté pour limiter la sortie à des tons spécifiques. Tous les tons se qualifiant sont renvoyés pour chaque demande. L'inclusion de ce paramètre avec une demande ne génère pas une erreur, mais est sans effet sur la réponse.
    - Les zones `input_from` et `input_to` ne sont plus renvoyées pour des phrases individuelles. En plus des résultats de son analyse, la méthode ne renvoie à présent que l'ID et le texte de chaque phrase.

-   Le service renvoie dorénavant un code réponse HTTP 200 au lieu du code 400 pour les entrées partiellement correctes dans les cas suivants :

    -   Pour la méthode `/v3/tone`, si vous soumettez plus de 128 Ko ou 1000 phrases de contenu en entrée, le service renvoie une zone `warning` (avertissement) dans sa réponse. Le service analyse les 1000 premières phrases pour l'analyse au niveau du document. Il analyse uniquement les 100 premières phrases pour l'analyse au niveau des phrases. Les versions antérieures du service renvoyaient le code réponse 400 pour la demande si vous dépassiez l'une de ces limites. En outre, le service analyse maintenant les phrases comportant moins de trois mots.
    -   Pour la méthode `/v3/tone_chat`, si vous soumettez plus de 50 énoncés, le service renvoie une zone `warning` (avertissement) sur tout le contenu au niveau `utterances_tone` de la réponse et n'analyse que les 50 premières. Si vous soumettez un énoncé unique contenant plus de 500 caractères, le service renvoie une zone `error` pour cet énoncé et ne l'analyse pas. Les versions antérieures du service renvoyaient le code réponse 400 si vous dépassiez l'une de ces limites. Si tous les énoncés de l'entrée comportent plus de 500 caractères, le service renvoie néanmoins le code 400 pour la demande.

-   Le service régule à présent le nombre de demandes qu'il accepte d'un seul utilisateur. Le service renvoie le code réponse HTTP 429 *Too many requests* (Nombre de demandes trop élevé) s'il reçoit plus de 600 demandes d'un utilisateur {{site.data.keyword.cloud_notm}}.

-   Les modifications suivantes s'appliquent au noeud final générique et au noeud final d'interaction avec les clients :

    -   La version d'interface spécifiée avec le paramètre `version` indique `2017-09-21` afin d'utiliser la version la plus récente du service.
    -   La documentation été mise à jour pour signaler que le service peut générer une sortie localisée en plusieurs langues. Utilisez l'en-tête de demande `Accept-Language` pour spécifier la langue.

### 6 juillet 2017
{: #July2017b}

**Version du service** - `3.3.6`<br/> **Version d'interface** - `2016-05-19`

Le service a été mis à jour avec un petit correctif d'incident concernant le noeud final d'interaction avec les clients.

### 1 juillet 2017
{: #July2017a}

**Version du service** - `3.3.5`<br/> **Version d'interface** - `2016-05-19`

Disponibilité générale (GA) du noeud final d'interaction avec les clients du service {{site.data.keyword.toneanalyzershort}}. Tous les appels au noeud final sont désormais facturés au même taux que les appels au noeud final générique.

### 8 mai 2017
{: #May2017}

**Version du service** - `3.3.4`<br/> **Version d'interface** - `2016-05-19`

IBM a mis à jour les modèles de ton d'émotion et d'interaction avec les clients en étoffant encore le jeu de données d'apprentissage. Les modèles font maintenant preuve d'une plus grande précision vis à vis du jeu de données de référence.

### 17 avril 2017
{: #April2017}

-   Un nouveau jeu de tons spécifique au domaine d'interaction avec les clients est à présent disponible : *frustré*, *satisfait*, *excité*, *poli*, *impoli*, *triste* et *compréhensif*. Le service détecte ces tons depuis le texte d'une conversation entre un client et un agent. Les tons sont actuellement une fonctionnalité bêta.
-   IBM a publié des mises à jour du modèle de score de ton d'émotion qui améliorent les résultats concernant ce ton.

### 15 mars 2017
{: #March2017}

IBM a mis à jour le modèle de score de ton d'émotion. Les données d'apprentissage ont été élargies. En résultat, les modèles font maintenant preuve d'une plus grande précision vis à vis du jeu de données de référence.

### 1 décembre 2016
{: #December2016}

IBM a mis à jour les scores de ton d'émotion dans le document. Le nouveau modèle utilise le profil d'émotion des phrases pour agrégation du score du document.

### 18 octobre 2016
{: #October2016b}

IBM a étendu le score social. Le service utilise à présent une technique open-source de vectorisation des mots nommée [GloVe ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://nlp.stanford.edu/projects/glove/){: new_window} afin de déduire des scores de ton social. Cette modification permet au service de couvrir un vocabulaire étendu lors du calcul de tons sociaux. Pour plus d'informations sur la déduction de tons sociaux, voir [Disciplines scientifiques derrière le service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) pour le service {{site.data.keyword.personalityinsightsshort}}.

### 3 octobre 2016
{: #October2016a}

IBM a amélioré la détection d'émotion au niveau de la phrase. Le service utilise de nouvelles données d'apprentissage, un nouveau processus de sélection de traits et des lexiques enrichis pour les mots, les émoticônes et l'argot. Ces modifications génèrent des scores d'émotion différents mais sensiblement améliorés au niveau de la phrase. L'API du service n'a pas été modifiée.

### 19 mai 2016
{: #May2016}

Disponibilité générale (GA) du service {{site.data.keyword.toneanalyzershort}} avec les nouvelles fonctions suivantes :

-   Les modèles du service utilisent une sensibilité améliorée du contexte pour interpréter le ton. Les modèles utilisent maintenant plus que des jetons lexicaux. Ils prennent dorénavant en compte d'autres aspects dont la ponctuation, les émoticônes, les paramètres de la langue comme la structure de la phrase, et la complexité de la phrase.
-   Le modèle de ton d'écriture a été renommé en ton du langage.
-   Les modèles de ton du langage et d'émotion peuvent à présent gérer les négations.
-   Le service ne renvoie plus de réponse pour les phrases comportant moins de trois mots.
-   Le service propose à présent une [démonstration![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")simplifiée et améliorée](https://tone-analyzer-demo.ng.bluemix.net){: new_window}.
