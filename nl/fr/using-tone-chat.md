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

# Utilisation du noeud final d'interaction avec les clients
{: #utco}

Le noeud final d'interaction avec les clients de {{site.data.keyword.toneanalyzershort}} analyse le ton des conversations avec le service client et le support. Il peut vous aider à mieux comprendre les interactions avec vos clients et à améliorer votre communication en général ou avec des clients spécifiques. Pour plus d'informations sur l'interface, y-compris sur les SDK Node.js, Java et Python disponibles pour appeler le service, reportez-vous à la [Référence d'API![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.
{: shortdesc}

La consignation des demandes est désactivée pour le service {{site.data.keyword.toneanalyzershort}}. Que vous définissiez ou non l'en-tête de requête `X-Watson-Learning-Opt-Out`, le service ne consigne pas et ne conserve pas les données des demandes et des réponses.
{: note}

## Demande d'une analyse des tons
{: #request-tone-chat}

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
    <td style="text-align:center">Corps</td>
    <td style="text-align:center">Objet JSON</td>
    <td>
      Objet JSON <code>ToneChatInput</code> hébergeant le contenu
      à analyser. Pour plus d'informations, voir
      [Spécification d'entrée JSON](#JSONrequest).
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obligatoire</em></td>
    <td style="text-align:center">Requête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Version de l'API que vous souhaitez utiliser comme date au format
      <code>AAAAY-MM-JJ</code> ; par exemple, spécifiez <code>2017-09-21</code>
       pour le 21 septembre 2017 (la dernière version). Pour plus d'informations sur toutes les versions disponibles, voir les
[Notes sur l'édition](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn).
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Facultatif</em></td>
    <td style="text-align:center">En-tête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Langue du contenu en entrée.
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>en</code> (anglais, valeur par défaut)
        </li>
        <li style="margin:0px; padding:0px">
            <code>fr</code> (français)
        </li>
      </ul>
      Les variantes régionales sont traitées comme la langue parent. Par exemple,
      <code>en-US</code> est interprété comme <code>en</code>. Le contenu en entrée doit correspondre
      à la langue spécifiée. Ne soumettez pas de contenu
      utilisant les deux langues. Vous pouvez utiliser des langues différentes pour
      l'entrée et la réponse.
    </td>
  </tr>
  <tr>
    <td><code>Accept-Language</code><br/><em>Facultatif</em></td>
    <td style="text-align:center">En-tête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
         Langue demandée de la réponse. <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>ar</code> (arabe)
</li>
        <li style="margin:0px; padding:0px">
          <code>de</code> (allemand)
        </li>
        <li style="margin:0px; padding:0px">
          <code>en</code> (anglais, valeur par défaut)
        </li>
        <li style="margin:0px; padding:0px">
          <code>es</code> (espagnol)
        </li>
        <li style="margin:0px; padding:0px">
          <code>fr</code> (français)
        </li>
        <li style="margin:0px; padding:0px">
          <code>it</code> (italien)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ja</code> (japonais)
        </li>
        <li style="margin:0px; padding:0px">
          <code>ko</code> (coréen)
        </li>
        <li style="margin:0px; padding:0px">
          <code>pt-br</code> (portugais brésilien)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-cn</code> (chinois simplifié)
        </li>
        <li style="margin:0px; padding:0px">
          <code>zh-tw</code> (chinois traditionnel)
        </li>
      </ul>
      Pour les arguments à deux caractères, les variantes régionales sont traitées
      comme la langue parent. Par exemple, <code>en-US</code> est interprété comme
      <code>en</code>. Vous pouvez utiliser des langues différentes pour
      l'entrée et la réponse.
    </td>
  </tr>
</table>

Si vous soumettez plus de 50 énoncés, le service renvoie une zone `warning` (avertissement) pour le contenu global au niveau `utterances_tone` de sa réponse et n'analyse que les 50 premiers énoncés. Si vous soumettez un énoncé unique contenant plus de 500 caractères, le service renvoie une zone `error` pour cet énoncé et ne l'analyse pas. Dans les deux cas, la demande aboutit néanmoins avec le code de réponse HTTP 200.

Le service renvoie un code réponse 400 si tous les énoncés dans l'entrée comportent plus de 500 caractères.
{: note}

### Exemple de demande
{: #exampleRequest}

L'exemple de commande `curl` suivant appelle le noeud final d'interaction avec les clients avec le fichier d'entrée <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a> et la version `2017-09-21`:

```bash
curl -X POST -u "apikey:{apikey}"
--header "Content-Type: application/json"
--data-binary @./tone-chat.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone_chat?version=2017-09-21"
```
{: pre}

## Spécification d'entrée JSON
{: #JSONrequest}

Vous devez transmettre à la méthode un objet JSON `ToneChatInput` avec le format suivant. La zone `utterances` fournit un tableau d'objets `utterance`. La zone `text` est une chaîne requise qui fournit un énoncé qui a été ajouté par un utilisateur à la conversation à analyser. La zone `user` est une chaîne facultative qui identifie l'utilisateur qui a contribué à l'énoncé. 

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

L'exemple suivant illustre le contenu du fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone-chat.json" download="tone-chat.json">tone-chat.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe"></a>. Le fichier contient un bref échange entre un <code>client</code> et un <code>agent</code>.

```javascript
{
  "utterances": [
    {
      "text": "Bonjour, j'ai un problème avec votre produit.",
      "user": "customer"
    },
    {
      "text": "Très bien. Dites-moi ce qui se passe, s'il vous plaît.",
      "user": "agent"
    },
    {
      "text": "Eh bien, rien ne fonctionne :(",
      "user": "customer"
    },
    {
      "text": "J'en suis désolé.",
      "user": "agent"
    }
  ]
}
```
{: codeblock}

## Contenu de la réponse JSON
{: #JSONresponse-tone-chat}

Le service renvoie un objet JSON `UtteranceAnalyses` contenant une seule zone, `utterances_tone`. Cette zone contient un tableau d'objets `UtteranceAnalysis`, chacun fournissant les informations suivantes pour un énoncé du contenu en entrée :

-   `utterance_id` (entier) fournit l'identificateur unique de l'énoncé. Le premier énoncé est associé à ID 0, et l'ID de chaque énoncé ultérieur est incrémenté d'une unité.
-   `utterance_text` (chaîne) fournit le texte de l'énoncé.
-   `tones` est un tableau d'objets `ToneChatScore` qui fournit les résultats sur les tons dominants. Ces tons ont un score d'au moins 0,5. Le tableau est vide si l'énoncé ne comporte aucun ton avec un score atteignant ce seuil.

Chaque objet `ToneChatScore` fournit les informations suivantes sur un ton se qualifiant :

-   `score` (double) correspond au score du ton sur la plage 0,5 à 1. Un score supérieur à 0,75 indique une forte probabilité que le ton soit perçu dans l'énoncé.
-   `tone_id` (chaîne) correspond à l'identificateur unique, non localisé, du ton. Pour les descriptions des tons, voir [Tons d'interaction avec les clients](#tones-tone-chat).
-   `tone_name` (chaîne) correspond au nom visible par l'utilisateur et localisé du ton.

L'exemple suivant illustre la structure de l'objet `UtteranceAnalyses` :

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
{: #exampleResponse-tone-chat}

La sortie suivante est renvoyée pour l'[exemple de demande](#exampleRequest). (La même sortie est renvoyée pour l'exemple dans le [tutoriel Initiation](/docs/services/tone-analyzer?topic=tone-analyzer-gettingStarted#customerEngagement)). Tous les tons signalés ont un score d'au moins 0,5. Les tons ayant un score d'au moins 0,75 ont une forte probabilité d'être perçus par les participants à la conversation.

```javascript
{
  "utterances_tone": [
    {
      "utterance_id": 0,
      "utterance_text": "Bonjour, j'ai un problème avec votre produit.",
      "tones": [
        {
          "score": 0.686361,
          "tone_id": "polite",
          "tone_name": "Poli"
        }
      ]
    },
    {
      "utterance_id": 1,
      "utterance_text": "Très bien. Dites-moi ce qui se passe, s'il vous plaît.",
      "tones": [
        {
          "score": 0.92724,
          "tone_id": "polite",
          "tone_name": "Poli"
        }
      ]
    },
    {
      "utterance_id": 2,
      "utterance_text": "Eh bien, rien ne fonctionne :(",
      "tones": [
        {
          "score": 0.997795,
          "tone_id": "sad",
          "tone_name": "Triste"
        }
      ]
    },
    {
      "utterance_id": 3,
      "utterance_text": "J'en suis désolé.",
      "tones": [
        {
          "score": 0.730982,
          "tone_id": "polite",
          "tone_name": "Poli"
        },
        {
          "score": 0.672499,
          "tone_id": "sympathetic",
          "tone_name": "Compréhensif"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Tons d'interaction avec les clients
{: #tones-tone-chat}

Le service peut renvoyer des scores pour les sept tons suivants.

<table style="width:90%">
  <caption>Tableau 2. Tons d'interaction avec les clients</caption>
  <tr>
    <th style="text-align:left; width:20%">Ton / ID</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td>Enthousiaste<br/><code>excited</code></td>
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
