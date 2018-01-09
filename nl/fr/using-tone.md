---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-21"

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

# Utilisation du noeud final générique

Le noeud final générique de {{site.data.keyword.toneanalyzershort}} analyse le ton des communications écrites, des messages brefs par courrier électronique et jusqu'aux documents plus longs. Il peut vous aider à comprendre les tons émotionnels et du langage de vos communications. Pour des informations détaillées sur l'interface, y-compris sur les SDK Node.js, Java et Python disponibles pour appeler le service, reportez-vous à la [Référence d'API![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/tone-analyzer/api/v3/){: new_window}.
{: shortdesc}

## Demande d'une analyse des tons
{: #request}

Pour analyser les tons avec le noeud final générique, appelez l'une des deux versions de la méthode `tone` du service :

-   La méthode `POST /v3/tone` accepte un contenu en entrée au format JSON, texte brut ou HTML via le corps obligatoire de la demande. Utilisez cette méthode pour un texte plus long ou pour un texte que vous ne désirez pas exposer dans l'URL.
-   La méthode `GET /v3/tone` accepte un contenu en entrée via son paramètre de requête obligatoire `text`. Utilisez cette version de la méthode pour du texte simple facilement insérable dans l'URL.

La méthode accepte les paramètres suivants.

<table>
  <caption>Tableau 1. Paramètres des méthodes <code>/v3/tone</code></caption>
  <tr>
    <th style="text-align:left; width:20%">Paramètre</th>
    <th style="text-align:center; width:12%">Type</th>
    <th style="text-align:center; width:20%">Type de données</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td><code>Body</code><br/><em>Obligatoire pour la méthode <code>POST</code></em></td>
    <td style="text-align:center">Body</td>
    <td style="text-align:center">Objet JSON | chaîne</td>
    <td>
      JSON, texte brut ou entrée HTML hébergeant le contenu à analyser. Pour une entrée JSON, soumettez un objet du type <code>ToneInput</code> (voir <a href="#JSONinput">Spécification d'une entrée JSON</a>. <em>Non pris en charge pour les requêtes <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>text</code><br/><em>Obligatoire pour la méthode <code>GET</code></em></td>
    <td style="text-align:center">Requête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Entrée en texte brut hébergeant le contenu à analyser. Vous devez utiliser le codage d'URL pour l'entrée. <em>Non pris en charge pour les requêtes <code>POST</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>Content-Type</code><br/><em>Obligatoire pour la méthode <code>POST</code></em></td>
    <td style="text-align:center">En-tête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Type de contenu de la requête :
      <ul style="margin:0px 0px 0px 20px; padding:0px">
        <li style="margin:0px; padding:0px">
          <code>text/plain</code> pour du texte brut
        </li>
        <li style="margin:0px; padding:0px">
            <code>text/html</code> pour du texte HTML (le service supprime les balises
            HTML et n'analyse que le contenu textuel)
        </li>
        <li style="margin:0px; padding:0px">
          <code>application/json</code> pour du texte au format JSON
        </li>
      </ul>
    <em>A omettre pour les requêtes <code>GET</code>.</em>
    </td>
  </tr>
  <tr>
    <td><code>version</code><br/><em>Obligatoire</em></td>
    <td style="text-align:center">Requête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Version demandée de la réponse sous forme de date au format
      <code>AAAAY-MM-JJ</code>. Spécifiez, par exemple, <code>2017-09-21</code>
      pour le 21 septembre 2017.
    </td>
  </tr>
  <tr>
    <td><code>Content-Language</code><br/><em>Facultatif</em></td>
    <td style="text-align:center">En-tête</td>
    <td style="text-align:center">Chaîne</td>
    <td>
      Langue du contenu en entrée :
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
      Pour les arguments à deux caractères, les variantes régionales sont traitées
      comme la langue parent. Par exemple, <code>en-US</code> est interprété comme
      <code>en</code>. Vous pouvez utiliser des langues différentes pour
      l'entrée et la réponse.
    </td>
  </tr>
  <tr>
    <td><code>sentences</code><br/><em>Facultatif</em></td>
    <td style="text-align:center">Requête</td>
    <td style="text-align:center">Booléen</td>
    <td>
      Indique si le service doit renvoyer une analyse de chaque
      phrase individuelle en plus de son analyse du document complet.
      Si sa valeur indique <code>true</code> (valeur par défaut), le service renvoie des résultats pour
      chaque phrase.
    </td>
  </tr>
</table>

Ne soumettez pas plus de 128 Ko au total pour le contenu en entrée et pas plus de 1000 phrases individuelles. Le service analyse les 1000 premières phrases pour l'analyse au niveau du document et seulement les 100 premières phrases pour l'analyse au niveau des phrases. Il renvoie une zone `warning` (avertissement) dans le cadre de la réponse si vous dépassez l'une de ces limites. La requête aboutit toutefois avec un code de réponse HTTP 200.

### Exemples de requêtes
{: #exampleRequests}

L'exemple de commande cURL suivant utilise la méthode de requête HTTP `POST` pour appeler le noeud final générique avec le fichier d'entrée <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> et la version `2017-09-21`. L'exemple demande une analyse tant du document complet que des phrases individuelles.

```bash
curl -X POST --user "{username}":"{password}"
--header "Content-Type: application/json"
--data-binary @./tone.json
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21"
```
{: pre}

L'exemple de commande suivant est équivalent au précédent mais utilise la méthode de requête HTTP `GET` :

```bash
curl -X GET --user "{username}":"{password}"
"https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2017-09-21&text=Team%2C%20I%20know%20that
%20times%20are%20tough%21%20Product%20sales%20have%20been%20disappointing%20for%20the%20past%20three%20quarters.
%20We%20have%20a%20competitive%20product%2C%20but%20we%20need%20to%20do%20a%20better%20job%20of%20selling%20it%21"
```
{: pre}

Pour d'autres exemples, reportez-vous au [tutoriel Initiation](/docs/services/tone-analyzer/getting-started.html).

### Spécification du jeu de caractères
{: #charset}

Par défaut, le service utilise les jeux de caractères suivants pour le contenu en entrée :

-   *Pour le texte brut et le contenu HTML,* le service utilise le jeu de caractères ISO (International Standards OrganizationSO) 8859-1 (lequel correspond au jeu de caractères ASCII) d'après la spécification HTTP version 1.1.
-   *Pour le contenu JSON,* le service utilise systématiquement le jeu de caractères UTF (Unicode Transformation Format) 8, conformément à la Section 8.1 de l'organisme IETF (International Engineering Task Force) : [RFC (Request for Comment - Demande de changement) 7159 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://tools.ietf.org/html/rfc7159#section-8.1){: new_window}.

Lors d'une soumission de texte brut ou de contenu HTML, incluez le paramètre `charset` avec l'en-tête `Content-Type` pour indiquer le codage de caractères du texte en entrée. L'exemple ci-après stipule le codage de caractères UTF-8 pour entrée de texte brut :

```
Content-Type: text/plain;charset=utf-8
```
{: codeblock}

En utilisant le paramètre `charset`, vous pouvez éviter des problèmes potentiels associés à des caractères non -ASCII ou non imprimables. Si vous transmettez des données UTF-8 sans spécifier le jeu de caractères, les caractères spéciaux peuvent générer des résultats incorrects ou des erreurs HTTP 4*nn* ou 5*nn*.

Pour éviter des erreurs similaires lors de l'utilisation de commande cURL, transmettez toujours le contenu via l'option `--data-binary` de la commande `curl` pour préserver un éventuel codage UTF-8 du contenu. Si vous utilisez l'option `--data` pour le transmettre en tant que contenu ASCII, la commande peut traiter l'entrée, ce qui peut entraîner des problèmes pour les données codées en UTF-8.

## Spécification d'entrée JSON
{: #JSONinput}

Pour analyser une entrée JSON avec la méthode de requête `POST`, transmettez à la méthode un objet JSON `ToneInput` sous le format simple suivant :

```javascript
{
  "text": ""
}
```
{: codeblock}

L'exemple suivant illustre le contenu du fichier <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/tone-analyzer/tone.json" download="tone.json">tone.json <img src="../../icons/launch-glyph.svg" alt="Icône de lien externe" title="Icône de lien externe" class="style-scope doc-content"></a> utilisé dans les exemples du [tutoriel Initiation](/docs/services/tone-analyzer/getting-started.html). Le fichier inclut un seul paragraphe de texte rédigé par une seule personne. (Le texte ci-après comprend des retours à la ligne à des fins de lisibilité ; ne les incluez pas dans l'entrée concrète).

```javascript
{
  "text": "Team, I know that times are tough! Product sales have been
  disappointing for the past three quarters. We have a competitive
  product, but we need to do a better job of selling it!"
}
```
{: codeblock}

## Contenu de la réponse JSON
{: #JSONresponse}

Le service renvoie un objet JSON `ToneAnalysis` comprenant toujours une zone `document_tone`. Cette zone contient un objet `DocumentAnalysis` qui fournit l'analyse du document d'entrée complet. Il contient une seule zone, `tones`, qui fournit les résultats de l'analyse pour chaque ton qualifié dans le document.

Si le paramètre `sentences` est omis dans la requête ou reçoit la valeur `true`, la réponse inclut également une zone `sentences_tone`. Cette zone contient un tableau d'objets `SentenceAnalysis`, chacun fournissant les informations suivantes pour une phrase différente du contenu en entrée :

-   `sentence_id` (entier) fournit l'identificateur unique de la phrase. La première est associée à ID 0, et l'ID de chaque phrase ultérieure est incrémenté d'une unité.
-   `text` (chaîne) fournit le texte de la phrase.
-   `tones` fournit le résultat de l'analyse pour chaque ton qualifié dans la phrase.

L'exemple suivant illustre la structure de haut niveau de l'objet `ToneAnalysis` :

```javascript
{
  "document_tone": {
    "tones": [
      . . .
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": {integer},
      "text": "{string}",
      "tones": [
        . . .
      ]
    },
    . . .
  ]
}
```
{: codeblock}

### Ton et résultats du score

Les zones `tones` renvoyées pour les analyses tant au niveau du document que des phrases contiennent un tableau d'objets `ToneScore` qui fournissent les résultats sur les tons dominants, à savoir ceux avec un score au moins égal à 0,5. Le tableau est vide si aucun ton n'a un score atteignant ce seuil. Chaque objet `ToneScore` fournit les informations suivantes sur un ton se qualifiant :

-   `score` (double) correspond au score du ton sur la plage 0,5 à 1. Un score supérieur à 0,75 indique une forte probabilité que le ton soit perçu dans le contenu.
-   `tone_id` (chaîne) correspond à l'identificateur unique, non localisé, du ton. Pour les descriptions des tons, voir [Tons génériques](#tones).
-   `tone_name` (chaîne) correspond au nom visible par l'utilisateur et localisé du ton.

L'exemple suivant illustre la structure de l'objet `ToneScore` :

```javascript
{
  "tones": [
    {
      "score": {double},
      "tone_id": "{string}",
      "tone_name": "{string}"
    },
    . . .
  ]
}
```
{: codeblock}

### Exemple de réponse
{: #exampleResponse}

La sortie suivante est renvoyée pour les [Exemples de requêtes](#exampleRequests). (La même sortie est renvoyée pour le premier exemple dans le [tutoriel Initiation](/docs/services/tone-analyzer/getting-started.html)). La réponse inclut les résultats pour le document complet et pour chaque phrase. Tous les tons signalés ont un score d'au moins 0,5 ; ceux avec un score d'au moins 0,75 ont une forte probabilité d'être perçus dans le contenu.

```javascript
{
  "document_tone": {
    "tones": [
      {
        "score": 0.6165,
        "tone_id": "sadness",
        "tone_name": "Sadness"
      },
      {
        "score": 0.829888,
        "tone_id": "analytical",
        "tone_name": "Analytical"
      }
    ]
  },
  "sentences_tone": [
    {
      "sentence_id": 0,
      "text": "Team, I know that times are tough!",
      "tones": [
        {
          "score": 0.801827,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 1,
      "text": "Product sales have been disappointing for the past three quarters.",
      "tones": [
        {
          "score": 0.771241,
          "tone_id": "sadness",
          "tone_name": "Sadness"
        },
        {
          "score": 0.687768,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    },
    {
      "sentence_id": 2,
      "text": "We have a competitive product, but we need to do a better job of selling it!",
      "tones": [
        {
          "score": 0.506763,
          "tone_id": "analytical",
          "tone_name": "Analytical"
        }
      ]
    }
  ]
}
```
{: codeblock}

## Tons génériques
{: #tones}

Le tableau suivant décrit les tons génériques pouvant être renvoyés par le service. Un ton avec un score inférieur à 0,5 est omis, ce qui dénote que l'émotion est peu susceptible d'être perçue dans le contenu. Un score supérieur à 0,75 indique une forte probabilité que le ton soit perçu.

<table>
  <caption>Tableau 2. Tons génériques</caption>
  <tr>
    <th style="text-align:left; vertical-align:bottom; width:20%">Ton / ID</th>
    <th style="text-align:left">Description</th>
  </tr>
  <tr>
    <td>Colère<br/><code>anger</code></td>
    <td>
      La colère est évoquée suite à une injustice, un conflit, une humiliation, une négligence,
      ou une trahison. Si la colère est active, l'individu attaque la cible,
      verbalement ou physiquement. Si la colère est passive, l'individu renâcle en silence et ressent de la tension et de l'hostilité. (Ton émotionnel.)
    </td>
  </tr>
  <tr>
    <td>Peur<br/><code>fear</code></td>
    <td>
      La peur est une réponse à un danger imminent. Il s'agit d'un mécanisme de survie déclenché en
     réaction à un stimulus négatif. La peur peut se traduire par une prudence modérée ou une phobie extrême. (Ton émotionnel.)
    </td>
  </tr>
  <tr>
    <td>Joie<br/><code>joy</code></td>
    <td>
      La joie (ou le bonheur) a des teintes de contentement, de satisfaction et de plaisir.
      La joie apporte une sensation de bien-être, de paix intérieure, d'amour, de sécurité et de
      contentement. (Ton émotionnel.)
    </td>
  </tr>
  <tr>
    <td>Tristesse<br/><code>sadness</code></td>
    <td>
      La tristesse indique une sensation de perte et de spoliation. Lorsqu'une personne est
      taciturne, moins énergique et renfermée, on déduit parfois qu'elle éprouve de la
      tristesse. (Ton émotionnel.)
    </td>
  </tr>
  <tr>
    <td>Analytique<br/><code>analytical</code></td>
    <td>
      Un ton analytique indique une attitude cartésienne et analytique d'une personne
      vis à vis des choses. Une personne analytique peut être perçue comme intellectuelle,
      rationnelle, systématique, dépourvue d'émotions ou impersonnelle. (Ton de langage).
    </td>
  </tr>
  <tr>
    <td>Confiant<br/><code>confident</code></td>
    <td>
      Un ton confiant indique le degré d'assurance d'une personne. Une personne confiante peut être perçue comme
      sûre d'elle-même, maître de soi, optimiste ou égotiste.
      (Ton de langage).
    </td>
  </tr>
  <tr>
    <td>Indécis<br/><code>tentative</code></td>
    <td>
      Un ton indécis indique un degré d'inhibition de la personne. Une personne
      indécise peut être perçue comme évasive, dubitative ou argumentative. (Ton de langage).
    </td>
  </tr>
</table>
