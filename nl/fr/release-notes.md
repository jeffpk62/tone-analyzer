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

# Notes sur l'édition

Les sections ci-après décrivent les nouvelles fonctions et les modifications introduites dans chaque version du service {{site.data.keyword.toneanalyzershort}}. Les modifications ne perturbent pas le code existant.
{: shortdesc}

> **Remarque :** les notes sur l'édition documentent la *version du service* et la *version d'interface* pour chaque mise à jour. Spécifiez la *version d'interface* via le paramètre de requête `version` pour utiliser les nouvelles fonctions et fonctionnalités rendues disponibles avec cette mise à jour. Le service renvoie les deux versions avec l'en-tête de réponse `X-Service-Api-Version`.

## 28 septembre 2017
{: #September2017b}

**Version du service :** `3.4.1`<br/> **Version d'interface :** `2017-09-21`

-   Le nombre maximal de requêtes qu'un nom d'utilisateur {{site.data.keyword.Bluemix_notm}} individuel peut soumettre a été porté à 1200 requêtes par minute. Le service renvoie le code réponse HTTP 429 *Requêtes trop nombreuses* si un utilisateur dépasse cette limite.

## 25 septembre 2017
{: #September2017a}

**Version du service :** `3.4.1`<br/> **Version d'interface :** `2017-09-21`

-   Le noeud final générique (méthode `/v3/tone`) a été modifié comme suit :

    -   Prise en charge du français (`fr`) dans le contenu en entrée, en plus de l'anglais.
    -   Les tons sociaux ne sont plus renvoyés.
    -   `disgust` (dégoût) n'est plus renvoyé avec les tons d'émotion.
    -   Omission de tous les tons dont le score est inférieur à `0,5`. Cette qualification correspond à la réponse de la méthode `/v3/tone_chat`.
    - Les catégories de ton (zone `tone_categories`) ne sont plus renvoyées dans le cadre de sa sortie. Tous les tons respectant le seuil de qualification sont renvoyés dans le cadre d'un objet `tones` unique. Comme avant, les tons sont toujours renvoyés par défaut pour le document complet et pour chaque phrase individuelle.
    - Le paramètre de requête `tones` n'est plus accepté pour limiter la sortie à des tons spécifiques. Tous les tons se qualifiant sont renvoyés pour chaque requête. L'inclusion de ce paramètre avec une requête ne génère pas une erreur, mais est sans effet sur la réponse.
    - Les zones `input_from` et `input_to` ne sont plus renvoyées pour des phrases individuelles. En plus des résultats de son analyse, la méthode ne renvoie à présent que l'ID et le texte de chaque phrase.

-   Le service renvoie dorénavant un code réponse HTTP 200 au lieu du code 400 pour les entrées partiellement correctes dans les cas suivants :

    -   Pour la méthode `/v3/tone`, si vous soumettez plus de 128 Ko ou 1000 phrases de contenu en entrée, le service renvoie une zone `warning` (avertissement) dans sa réponse. Le service analyse les 1000 premières phrases au niveau du document et, actuellement, seulement les 100 premières phrases au niveau de la phrase. Les versions antérieures du service renvoyaient le code réponse 400 pour la requête si vous dépassiez l'une de ces limites. Notez aussi que le service analyse maintenant les phrases comportant moins de trois mots.
    -   Pour la méthode `/v3/tone_chat`, si vous soumettez plus de 50 énoncés, le service renvoie une zone `warning` (avertissement) sur tout le contenu au niveau `utterances_tone` de la réponse et n'analyse que les 50 premières. Si vous soumettez un énoncé unique contenant plus de 500 caractères, le service renvoie une zone `error` pour cet énoncé et ne l'analyse pas. Les versions antérieures du service renvoyaient le code réponse 400 si vous dépassiez l'une de ces limites. Notez que si tous les énoncés de l'entrée comportent plus de 500 caractères, le service renvoie néanmoins le code 400 pour la requête.

-   Le service régule à présent le nombre de requêtes qu'il accepte d'un seul utilisateur. Le service renvoie le code réponse HTTP 429 *Too many requests* ((Requêtes trop nombreuses) s'il reçoit plus de 600 requêtes d'un utilisateur {{site.data.keyword.Bluemix_notm}}.

-   Les modifications suivantes s'appliquent au noeud final générique et au noeud final d'interaction avec les clients :

    -   La version d'interface spécifiée avec le paramètre `version` indique `2017-09-21` afin d'utiliser la version la plus récente du service.
    -   La documentation a été mise à jour pour signaler que le service peut générer une sortie localisée dans plusieurs langues. Utilisez l'en-tête de requête `Accept-Language` pour spécifier la langue souhaitée.

## 6 juillet 2017
{: #July2017b}

**Version du service :** `3.3.6`<br/> **Version d'interface :** `2016-05-19`

Le service a été mis à jour avec un petit correctif d'incident concernant le noeud final d'interaction avec les clients.

## Versions plus anciennes

-   [1 juillet 2017](#July2017a)
-   [8 mai 2017](#May2017)
-   [17 avril 2017](#April2017)
-   [15 mars 2017](#March2017)
-   [1 décembre 2016](#December2016)
-   [18 octobre 2016](#October2016b)
-   [3 octobre 2016](#October2016a)
-   [19 mai 2016](#May2016)

### 1 juillet 2017
{: #July2017a}

**Version du service :** `3.3.5`<br/> **Version d'interface :** `2016-05-19`

Disponibilité générale (GA) du noeud final d'interaction avec les clients du service {{site.data.keyword.toneanalyzershort}}. Tous les appels au noeud final sont désormais facturés au même taux que les appels au noeud final générique.

### 8 mai 2017
{: #May2017}

**Version du service :** `3.3.4`<br/> **Version d'interface :** `2016-05-19`

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

IBM a mis à jour les scores de ton d'émotion dans le document. Le nouveau modèle prend en compte le profil d'émotion des phrases pour agrégation du score du document.

### 18 octobre 2016
{: #October2016b}

IBM a étendu le score social. Le service utilise à présent une technique open-source de vectorisation des mots nommée [GloVe ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://nlp.stanford.edu/projects/glove/){: new_window} afin de déduire des scores de ton social. Cette modification permet au service de couvrir un vocabulaire étendu lors du calcul de tons sociaux. Pour plus d'informations sur la déduction de tons sociaux, voir [Disciplines scientifiques derrière le service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) pour le service {{site.data.keyword.personalityinsightsshort}}.

### 3 octobre 2016
{: #October2016a}

IBM a amélioré la détection d'émotion au niveau de la phrase. Le service utilise de nouvelles données d'apprentissage, un nouveau processus de sélection de traits et des lexiques enrichis pour les mots, les émoticônes et l'argot. Ces modifications génèrent des scores d'émotion différents mais sensiblement améliorés au niveau de la phrase. L'API du service n'a pas été modifiée.

### 19 mai 2016
{: #May2016}

Disponibilité générale (GA) du service {{site.data.keyword.toneanalyzershort}} avec les nouvelles fonctions suivantes :

-   Les modèles du service utilisent une sensibilité améliorée du contexte pour interpréter le ton. Les modèles n'utilisent plus simplement des jetons lexicaux. Ils prennent dorénavant en compte d'autres aspects dont la ponctuation, les émoticônes, les paramètres de la langue comme la structure de la phrase, et la complexité de la phrase.
-   Le modèle de ton d'écriture a été renommé en ton du langage.
-   Les modèles de ton du langage et d'émotion peuvent à présent gérer les négations.
-   Le service ne renvoie plus de réponse pour les phrases comportant moins de trois mots.
-   Le service propose à présent une [démonstration![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")simplifiée et améliorée](https://tone-analyzer-demo.mybluemix.net){: new_window}.
