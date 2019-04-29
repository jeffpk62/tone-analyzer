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

# Tutoriel d'initiation
{: #gettingStarted}

Le service {{site.data.keyword.toneanalyzershort}} analyse le ton du contenu en entrée. Ce tutoriel illustre des commandes qui analysent des échantillons de contenu différents. Les exemples illustrent à la fois les noeuds finaux génériques et les noeuds finaux d'interaction avec les clients.
{: shortdesc}

Le tutoriel utilise les clés d'API {{site.data.keyword.cloud}} Identity et Access Management (IAM) pour l'authentification. Les anciennes instances de service peuvent continuer à utiliser les `{username}` et `{password}` de leurs données d'identification de service Cloud Foundry existantes pour l'authentification. Authentifiez-vous en utilisant l'approche qui convient à votre instance de service. Pour plus d'informations sur l'utilisation de l'authentification IAM par le service, voir les [Notes sur l'édition](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
{: important}

## Avant de commencer
{: #prerequisites}

- {: hide-dashboard}  Créez une instance du service :
    1.  {: hide-dashboard} Accédez à la page [{{site.data.keyword.toneanalyzershort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/tone-analyzer){: new_window} du catalogue {{site.data.keyword.cloud_notm}}.
    1.  {: hide-dashboard} Inscrivez-vous pour un compte {{site.data.keyword.cloud_notm}} gratuit ou connectez-vous.
    1.  {: hide-dashboard}Cliquez sur **Créer**. 
-   Copiez les données d'identification pour vous authentifier auprès de votre instance de service :
    1.  {: hide-dashboard} Dans le [tableau de bord {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/dashboard/apps){: new_window}, cliquez sur votre instance de service {{site.data.keyword.toneanalyzershort}} pour accéder à la page du tableau de bord du service {{site.data.keyword.toneanalyzershort}}.
    1.  Sur la page **Gérer**, cliquez sur **Afficher** pour afficher vos données d'identification.
    1.  Copiez les valeurs des zones `Clé d'API` et `URL`.
-   Vérifiez que vous disposez de la commande `curl`.
    -   Les exemples utilisent la commande `curl` pour appeler des méthodes de l'interface HTTP. Installez la version correspondant à votre système d'exploitation à partir du site [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Installez la version qui prend en charge le protocole SSL (Secure Sockets Layer). Prenez soin d'inclure le fichier binaire installé dans votre variable d'environnement `PATH`.

Lorsque vous entrez une commande, remplacez `{apikey}` et `{url}` par votre clé d’API et votre URL. Omettez les accolades de la commande car elles indiquent une valeur de variable. Une valeur réelle ressemble à l'exemple suivant :
{: hide-dashboard}

```bash
curl -X POST -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x"
. . .
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{:pre}
{: hide-dashboard}

## Etape 1 : Utilisation du noeud final générique via la méthode de demande POST
{: #generalPurposePost}

Les commandes suivantes appellent la méthode `POST /v3/tone` pour analyser le contenu du fichier `tone.json`. Le fichier inclut un seul paragraphe de texte brut rédigé par une seule personne. Les exemples illustrent les paramètres de requête `sentences` de la méthode.

1.  Téléchargez l'exemple de fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>.
1.  Exécutez la commande suivante pour analyser le ton du contenu global et de chaque phrase.
    -   {: hide-dashboard} Remplacez `{apikey}` et `{url}` par vos données.
    -   Modifiez `{path_to_file}` (chemin de fichier) en spécifiant l'emplacement du fichier `tone.json`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21"{: url}
    ```
    {: pre}

1.  Exécutez la commande suivante pour analyser uniquement le ton du contenu global en affectant au paramètre `sentences` la valeur `false`.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "{url}/v3/tone?version=2017-09-21&sentences=false"{: url} \
    ```
    {: pre}

Pour consulter un exemple de la sortie de la méthode, voir [Exemple de réponse](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe#exampleResponse-tone).

## Etape 2 : Utilisation du noeud final générique via la méthode de demande GET
{: #generalPurposeGet}

L'interface propose également une méthode `GET /v3/tone`. La méthode `GET` offre les mêmes fonctionnalités et génère les mêmes résultats que la méthode `POST`, mais vous devez utiliser le paramètre de requête `text` de la méthode pour spécifier le contenu à analyser. La méthode n'accepte qu'une entrée en texte brut.

1.  L'exemple suivant spécifie le texte du fichier `tone.json` via le paramètre `text` ; comme illustré, vous devez utiliser le codage d'URL pour le texte. La commande omet le paramètre `sentences` et renvoie donc la même sortie que le premier exemple `POST` présenté plus haut. (L'exemple ci-après comprend des retours à la ligne à des fins de lisibilité ; ne les incluez pas dans une commande concrète).

    ```bash
    curl -X GET -u "apikey:{apikey}"{: apikey} \
    "{url}/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"{: url}
    ```
    {: pre}

## Etape 3 : Utilisation du noeud final d'interaction avec les clients
{: #customerEngagement}

La commande suivante appelle la méthode `POST /v3/tone_chat` pour analyser le contenu du fichier `tone-chat.json`. Le fichier contient un bref échange entre deux personnes, un <code>client</code> et un <code>agent</code>.

1.  Téléchargez l'exemple de fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>.
1.  Exécutez la commande suivante pour analyser le ton de l'échange dans l'exemple de fichier.

    ```bash
    curl -X POST -u "apikey:{apikey}"{: apikey} \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "{url}/v3/tone_chat?version=2017-09-21"{: url}
    ```
    {: pre}

La réponse du service indique les tons prédominants détectés pour chaque énoncé de l'entrée. Pour consulter le contenu de la réponse pour cette demande, voir [Exemple de réponse](/docs/services/tone-analyzer?topic=tone-analyzer-utco#exampleResponse-tone-chat).

## Etapes suivantes
{: #gsns}

-   Pour plus d'informations sur la méthode `/v3/tone`, voir [Utilisation du noeud final de service générique](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe).
-   Pour plus d'informations sur la méthode `/v3/tone_chat`, voir [Utilisation du noeud final d'interaction avec les clients](/docs/services/tone-analyzer?topic=tone-analyzer-utco).
-   Pour plus d'informations sur les méthodes de l'interface du service, reportez-vous à la [Référence d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
