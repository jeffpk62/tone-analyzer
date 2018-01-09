---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-28"

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

# Utilisation du noeud final d'interaction avec les clients

Le noeud final d'interaction avec les clients de {{site.data.keyword.toneanalyzershort}} analyse le ton des conversations avec le service client et le support. Il peut vous aider à mieux comprendre les interactions avec vos clients et à améliorer votre communication en général ou avec des clients spécifiques. Pour des informations détaillées sur l'interface, y-compris sur les SDK Node.js, Java et Python disponibles pour appeler le service, reportez-vous à la [Référence d'API![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Demande d'une analyse des tons
{: #request}

Pour analyser le ton à l'aide du noeud final d'interaction avec les clients, appelez la méthode `POST /v3/tone_chat` avec les paramètres suivants.

<table>
  <caption>Tableau 1. Paramètres de la méthode <code>POST /v3/tone_chat</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Paramètre</th>
    <th style="text-align:center; width:12%">Type</th>
    <th style="text-align:center; width:20%">Type de données</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Obligatoire</em></td>
    <td style="text-align:center">Body</td>
    <td style="text-align:center">Objet JSON</td>
    <td>
      Objet JSON <code>ToneChatInput</code> hébergeant le contenu
      à analyser. Voir <a href="#JSONrequest">Spécification d'entrée JSON</a>.
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obligatoire</em></td>
    <td style="text-align:center">Requête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Version demandée de l'interface sous forme de date au format
      <code>AAAAY-MM-JJ</code>. Spécifiez, par exemple, <code>2017-09-21</code>
      pour le 21 septembre 2017.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Facultatif</em></td>
    <td style="text-align:center">En-tête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Langue désirée pour la réponse :
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          ar (arabe)
        </li>
        <li style="margin:0px; padding:0px">
          de (allemand)
        </li>
        <li style="margin:0px; padding:0px">
          en (anglais, valeur par défaut)
        </li>
        <li style="margin:0px; padding:0px">
          es (espagnol)
        </li>
        <li style="margin:0px; padding:0px">
          fr (français)
        </li>
        <li style="margin:0px; padding:0px">
          it (italien)
        </li>
        <li style="margin:0px; padding:0px">
          ja (japonais)
        </li>
        <li style="margin:0px; padding:0px">
          ko (coréen)
        </li>
        <li style="margin:0px; padding:0px">
          pt-br (portugais brésilien)
        </li>
        <li style="margin:0px; padding:0px">
          zh-cn (chinois simplifié)
        </li>
        <li style="margin:0px; padding:0px">
          zh-tw (chinois traditionnel)
        </li>
      </ul>
    </td>
  </tr>
</table>

Si vous soumettez plus de 50 énoncés, le service renvoie une zone `warning` (avertissement) pour le contenu global au niveau `utterances_tone` de sa réponse et n'analyse que les 50 premiers énoncés. Si vous soumettez un énoncé unique contenant plus de 500 caractères, le service renvoie une zone `error` pour cet énoncé et ne l'analyse pas. Dans les deux cas, la demande aboutit néanmoins avec le code de réponse HTTP 200.

> **Remarque :** le service renvoie un code réponse 400 si tous les énoncés dans l'entrée comportent plus de 500 caractères.

### Exemple de requête
{: #exampleRequest}

L'exemple de commande cURL suivant appelle le noeud final d'interaction avec les clients avec le fichier d'entrée <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> et la version `2017-09-21`:

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Spécification d'entrée JSON
{: #JSONrequest}

Vous devez transmettre à la méthode un objet JSON `ToneChatInput` avec le format suivant. La zone `utterances` fournit un tableau d'objets `utterance` (énoncé), où `text` est une chaîne obligatoire qui fournit un énoncé contribué par un utilisateur à la conversation à analyser et `user` correspond à une chaîne facultative qui identifie l'utilisateur ayant contribué l'énoncé.

```javascript
{
  "utterances": [
    {
      "text": "",
      "user": ""
    },
    . . .
  ]
}
```
{: codeblock}

L'exemple suivant illustre le contenu du fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a>. Le fichier contient un bref échange entre un <code>client</code> et un <code>agent</code>.

```javascript
{
  "utterances": [
    {
      "text": "Hello, I'm having a problem with your product.",
      "user": "customer"
    },
    {
      "text": "OK, let me know what's going on, please.",
      "user": "agent"
    },
    {
      "text": "Well, nothing is working :(",
      "user": "customer"
    },
    {
      "text": "Sorry to hear that.",
      "user": "agent"
    }
  ]
}
```
{: codeblock}

## Contenu de la réponse JSON
{: #JSONresponse}

Le service renvoie un objet JSON `UtteranceAnalyses` contenant une seule zone, `utterances_tone`. Cette zone contient un tableau d'objets `UtteranceAnalysis`, chacun fournissant les informations suivantes pour un énoncé du contenu en entrée : 

-   `utterance_id` (entier) fournit l'identificateur unique de l'énoncé. Le premier énoncé est associé à ID 0, et l'ID de chaque énoncé ultérieur est incrémenté d'une unité.
-   `utterance_text` (chaîne) fournit le texte de l'énoncé.
-   `tones` est un tableau d'objets `ToneChatScore` qui fournit les résultats sur les tons dominants, à savoir ceux avec un score d'au moins 0,5. Le tableau est vide si l'énoncé ne comporte aucun ton avec un score atteignant ce seuil. 

Chaque objet `ToneChatScore` fournit les informations suivantes sur un ton se qualifiant :

-   `score` (double) correspond au score du ton sur la plage 0,5 à 1. Un score supérieur à 0,75 indique une forte probabilité que le ton soit perçu dans l'énoncé.
-   `tone_id` (chaîne) correspond à l'identificateur unique, non localisé, du ton. Pour les descriptions des tons, voir [Tons d'interaction avec les clients](#tones).
-   `tone_name` (chaîne) correspond au nom visible par l'utilisateur et localisé du ton.

L'exemple suivant illustre la structure de l'objet `UtterancesAnalyses` :

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": {integer},
      "utterance_text": "{string}",
      "tones": [
        {
          "score": {double},
          "tone_id": "{string",
          "tone_name": "{string}"
        }
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### Exemple de réponse
{: #exampleResponse}

La sortie suivante est renvoyée pour l'[exemple de requête](#exampleRequest). (La même sortie est renvoyée pour l'exemple dans le [tutoriel Initiation](/docs/services/tone-analyzer/getting-started.html#customerEngagement)). Tous les tons signalés ont un score d'au moins 0,5 ; ceux avec un score d'au moins 0,75 ont une forte probabilité d'être perçus par les participants à la conversation.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Hello, I'm having a problem with your product.",
      "tones": [
        {
          "score": 0.718352,
          "tone_id": "polite",
          "tone_name": "Polite"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "OK, let me know what's going on, please.",
      "tones": []
    },
    {
      "utterance_id": 2,
      "utterance_text": "Well, nothing is working :(",
      "tones": [
        {
          "score": 0.997149,
          "tone_id": "sad",
          "tone_name": "sad"
        }
      ]
    },
    {
      "utterance_id": 3,
      "utterance_text": "Sorry to hear that.",
      "tones": [
        {
          "score": 0.689109,
          "tone_id": "polite",
          "tone_name": "Polite"
        },
        {
          "score": 0.663203,
          "tone_id": "sympathetic",
          "tone_name": "Sympathetic"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Tons d'interaction avec les clients
{: #tones}

Le service peut renvoyer des scores pour les sept tons suivants.

<table style="width:90%">
  <caption>Tableau 2. Tons d'interaction avec les clients</caption>
  <tr>
    <th style="text-align:left; width:20%">Ton / ID</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td>Excité<br/><code>excited</code></td>
    <td>
      Affiche de l'enthousiasme et un intérêt personnel
    </td>
  </tr>
  <tr>
    <td>Frustré<br/><code>frustrated</code></td>
    <td>
      Défini comme se sentant ennuyé et irritable
    </td>
  </tr>
  <tr>
    <td>Impoli<br/><code>impolite</code></td>
    <td>
      Irrespectueux et grossier
    </td>
  </tr>
  <tr>
    <td>Poli<br/><code>polite</code></td>
    <td>
      Défini comme ayant un comportement rationnel, orienté objectif
    </td>
  </tr>
  <tr>
    <td>Triste<br/><code>sad</code></td>
    <td>
      Considérée comme une émotion passive désagréable
    </td>
  </tr>
  <tr>
    <td>Satisfait<br/><code>satisfied</code></td>
    <td>
      Réponse affective à la qualité de service perçue
    </td>
  </tr>
  <tr>
    <td>Compréhensif<br/><code>sympathetic</code></td>
    <td>
      Mode affectif de compréhension qui implique une résonance émotionnelle
    </td>
  </tr>
</table>
