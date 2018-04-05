---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Tutoriel Initiation
{: #gettingStarted}

Le service {{site.data.keyword.toneanalyzershort}} analyse le ton du contenu en entrée. Ce tutoriel illustre des commandes qui analysent des échantillons de contenu différents. Les exemples décrivent le noeud final générique ainsi que le noeud final d'interaction avec les clients.
{: shortdesc}

## Avant de commancer
{: #prerequisites}

- Créez une instance du service :
    - {: download} Si vous voyez ce message, vous avez créé votre instance de service. Procurez-vous maintenant vos données d'identification.
    - Créez un projet depuis un service :
        1.  Accédez à la page {{site.data.keyword.watson}} Developer Console [Services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Sélectionnez {{site.data.keyword.toneanalyzershort}}, cliquez sur **Add Services** et inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
        1.  Entrez `tone-tutorial` comme nom de projet et cliquez sur **Create Project**.
- Copiez les données d'identification pour authentification auprès de votre instance de service :
    - {: download} Depuis le tableau de bord du service (lequel est affiché) :
        1.  Cliquez sur l'onglet **Données d'identification pour le service**.
        1.  Cliquez sur **Afficher les données d'identification** sous **Actions**.
        1.  Copy the `username` (nom utilisateur), `password` (mot de passe) et `url`.
        {: download}
    - Depuis votre projet **tone-tutorial** dans la console Developer Console, copiez les valeurs de `username`,  `password` et `url` pour `"tone_analyzer"` depuis la section **Credentials**.
- Vérifiez que cURL est bien installé :
    - Les exemples utilisent cURL pour appeler des méthodes de l'interface HTTP. Installez la version correspondant à votre système d'exploitation depuis le site [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Installez la version qui prend en charge le protocole SSL (Secure Sockets Layer). Prenez soin d'inclure le fichier binaire installé dans votre variable d'environnement `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si vous utilisez {{site.data.keyword.Bluemix_dedicated_notm}}, créez votre instance de service depuis la page [{{site.data.keyword.toneanalyzershort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/catalog/services/tone-analyzer/){: new_window} dans le catalogue. Pour plus de détails sur l'identification de vos données d'identification pour le service, voir [Données d'identification pour les services Watson ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etape 1 : Utilisez le noeud final générique via la méthode de requête POST
{: #generalPurposePost}

Les commandes suivantes appellent la méthode `POST /v3/tone` pour analyser le contenu du fichier `tone.json`. Le fichier comporte un seul paragraphe de texte brut rédigé par une seule personne. Les exemples illustrent les paramètres de requête `sentences` de la méthode.

1.  Téléchargez l'exemple de fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Exécutez la commande suivante pour analyser le ton du contenu global et de chaque phrase.
    -   Remplacez `{username}` (nom utilisateur) et `{password}` (mot de passe) par vos données d'identification pour le service obtenues à l'étape précédente.
    -   Modifiez `{path_to_file}` (chemin de fichier) en spécifiant l'emplacement du fichier `tone.json`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
    ```
    {: pre}

1.  Exécutez la commande suivante pour analyser uniquement le ton du contenu global en affectant au paramètre `sentences` la valeur `false`.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&sentences=false" \
    ```
    {: pre}

Pour consulter un exemple de la sortie de la méthode, voir [Exemple de réponse](/docs/services/tone-analyzer/using-tone.html#exampleResponse).

## Etape 2 : Utilisez le noeud final générique via la méthode de requête GET
{: #generalPurposeGet}

L'interface propose également une méthode `GET /v3/tone`. La méthode `GET` offre les mêmes fonctionnalités et génère les mêmes résultats que la méthode `POST`, mais vous devez utiliser le paramètre de requête `text` de la méthode pour spécifier le contenu à analyser. La méthode n'accepte qu'une entrée en texte brut.

1.  L'exemple suivant spécifie le texte du fichier `tone.json` via le paramètre `text` ; comme illustré, vous devez utiliser le codage d'URL pour le texte. La commande omet le paramètre `sentences` et renvoie donc la même sortie que le premier exemple `POST` présenté plus haut. (L'exemple ci-après comprend des retours à la ligne à des fins de lisibilité ; ne les incluez pas dans une commande concrète).

    ```bash
    curl -X GET --user "{username}":"{password}" \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21
    &text=Team%2C%20I%20know%20that%20times%20are%20tough%21%20Product%20sales%20have
    %20been%20disappointing%20for%20the%20past%20three%20quarters.%20We%20have%20a%20
    competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20
    selling%20it%21"
    ```
    {: pre}

## Etape 3 : Utilisez le noeud final d'interaction avec les clients
{: #customerEngagement}

La commande suivante appelle la méthode `POST /v3/tone_chat` pour analyser le contenu du fichier `tone-chat.json`. Le fichier contient un bref échange entre deux personnes, un <code>client</code> et un <code>agent</code>.

1.  Téléchargez l'exemple de fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>.
1.  Exécutez la commande suivante pour analyser le ton de l'échange dans l'exemple de fichier.

    ```bash
    curl -X POST --user "{username}":"{password}" \
    --header "Content-Type: application/json" \
    --data-binary @{path_to_file}tone-chat.json \
    "https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
    ```
    {: pre}

La réponse du service indique les tons prédominants détectés pour chaque énoncé de l'entrée. Pour consulter le contenu de la réponse pour cette requête, voir [Exemple de réponse](/docs/services/tone-analyzer/using-tone-chat.html#exampleResponse).

## Etapes suivantes

-   Pour plus d'informations sur la méthode `/v3/tone`, voir [Utilisation du noeud final de service générique](/docs/services/tone-analyzer/using-tone.html).
-   Pour plus d'informations sur la méthode `/v3/tone_chat`, voir [Utilisation du noeud final d'interaction avec les clients](/docs/services/tone-analyzer/using-tone-chat.html).
-   Pour des informations détaillées sur les méthodes de l'interface du service, reportez-vous à la [Référence d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
-   Interagissez avec l'API dans l'[Explorateur d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-api-explorer.mybluemix.net/apis/tone-analyzer-v3){: new_window}.
