---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-19"

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

# Etudes de cas 

Lisez ces études de cas pour vous inspirer sur ce que vous pouvez faire avec le service {{site.data.keyword.toneanalyzerfull}}. Ces études de cas décrivent la corrélation entre les tons observés et les résultats attendus. La corrélation peut être positive ou négative, avec une plage allant de -1,0 à 1,0.
{: shortdesc}

## Prévision de la satisfaction de la clientèle dans les forums de support

IBM a analysé les forums de support à la clientèle d'une entreprise de logiciels axée sur plusieurs industries. L'entreprise contribue activement à des forums d'assistance à la clientèle. Les utilisateurs peuvent attribuer des *Kudos* aux réponses qu'ils trouvent utiles.

### Objectifs

Prévoir la satisfaction de la clientèle à partir du ton de la question et de la réponse. IBM a supposé qu'une réponse accompagnée de Kudos signifiait que le client était satisfait.

### Actions

-   Exploration des 1000 fils de discussion les plus récents sur divers forums, en prenant soin d'inclure le même nombre de réponses avec et sans Kudos.
-   Analyse des questions et des réponses.
-   Application de plusieurs classificateurs de pointe tels que naive Bayes, SVM (Support Vector Machine) et forêt aléatoire pour prévoir si une réponse recevrait des Kudos.

### Résultats

Le service peut prédire des Kudos avec une précision de 66 %. IBM a constaté les corrélations suivantes entre les tons renvoyés dans une réponse sur un forum et l'octroi ou non de Kudos à la réponse :

-   Plus assurée est la réponse et plus grande est la probabilité qu'elle reçoive des Kudos (corrélation de 0,23 entre un score d'aplomb élevé et l'attribution de Kudos).
-   Plus la réponse est indécise et plus faible est la probabilité qu'elle reçoive des Kudos (corrélation négative de -0,27 entre un score d'indécision élevé et l'attribution de Kudos).

## Prévision de la satisfaction de la clientèle dans les réponses sur Twitter

De nombreuses entreprises migrent leur support client vers Twitter. Twitter permet des réponses en temps réel, ce qui aide à positionner la marque comme concernée par l'opinion de ses clients et avec des interlocuteurs réels.

IBM a analysé 333 conversations avec le support client sur Twitter. Les clients étaient satisfaits dans 240 conversations et mécontents dans 93 des interactions. IBM a mesuré la satisfaction en parcourant les conversations et en leur affectant un libellé. Les réponses ont été libellées "client satisfait" lorsqu'elles résolvaient le problème et "client non satisfait" lorsque le traitement du problème ne satisfaisait pas le client.

### Objectifs

Vérifier si le ton des conversations entre l'agent et le client a un effet quelconque sur la satisfaction globale du client. Identifier également les caractéristiques de ton ayant un impact significatif sur la satisfaction du client.

### Actions

-   Elimination de la ponctuation, des mentions et des liens dans les tweets.
-   Décomposition de chaque interaction entre tweet client et tweet du support.
-   Analyse de chaque versant de la conversation avec le service {{site.data.keyword.toneanalyzershort}} et comparaison des résultats pour rechercher des corrélations.

### Résultats

Le service peut prévoir la satisfaction du client depuis le ton de réponse avec une précision de 67 %. IBM a découvert la corrélation suivante entre le ton des tweets clients et la satisfaction ou non du client par la réponse :

-   Plus en colère est le client et plus faible est la probabilité qu'il soit satisfait par la réponse (corrélation négative de -0,198 entre uns score de colère élevé et la satisfaction du client).

## Prévision d'applaudissement sur TED Talk

TED est un organisme sans but lucratif qui gère des conférences globales avec le slogan "Des idées dignes d'être répandues". Les conférenciers sur TED Talk disposent de 18 minutes pour exposer des récits innovants et captivants couvrant une large palette de sujets sur le thème de la recherche et de la pratique des sciences et de la culture. Les conférences TED Talks ne sont pas toutes populaires et une manière de jauger la satisfaction du public consiste à mesurer le volume d'applaudissements qu'elles reçoivent.

### Objectifs

Découvrir quels types de ton sur TED Talks mènent à des applaudissements et ceux qui n'y mènent pas. Prédire également les applaudissements d'après le ton d'une phrase.

### Actions

Les phrases ayant reçu des applaudissements avaient déjà été libellées dans le jeu de données.

-   1931 TED Talks ont été examinés.
-   Les phrases avec une balise "Applaudissement" ont été classées dans la catégorie "texte suivi d'applaudissement." Les trois phrases précédentes ont également reçu la balise "texte suivi d'applaudissement" et les trois suivantes la balise "texte non suivi d'applaudissement."
-   Analyse du texte suivi d'applaudissement et du texte non suivi d'applaudissement avec le service {{site.data.keyword.toneanalyzershort}}.
-   Compte tenu des corrélations détectées, des classificateurs ont été créés pour prédire les applaudissements dans d'autres sessions TED Talks d'après leur ton.

### Résultats

Le service peut prédire les applaudissements avec une précision de 75 %. IBM a détecté les corrélations suivantes entre le ton de chaque ensemble de phrases et le déclenchement ou non d'applaudissements :

-   Plus un conférencier exprime de la tristesse et plus faible est la probabilité qu'il reçoive des applaudissements (corrélation négative de -0,055 entre un score de tristesse élevé et l'applaudissement).
-   Plus le conférencier semble détaché ou impersonnel et plus faible est la probabilité qu'il reçoive des applaudissements (corrélation négative de -0,29 entre un score de ton analytique élevé et l'applaudissement).
-   Plus le conférencier semble joyeux, content et satisfait, et plus grande est la probabilité qu'il reçoive des applaudissements (corrélation de 0,21 entre un score de joie élevé et l'applaudissement).

## Prévision de diffusion de tweets et de notations J'aime

La présence d'une marque sur Twitter devient incontournable pour la réussite d'une entreprise. Un élément essentiel pour inciter le public à vous suivre ou à suivre votre entreprise repose sur la création de tweets suscitant de nombreuses notations J'aime et de retweets.

### Objectifs

Identifier des corrélations entre le ton d'un tweet et une notation J'aime ou un retweet.

### Actions

-   Exploration de 5881 tweets de divers comptes d'entreprise sur Twitter.
-   Elimination de la ponctuation, des mentions et des liens dans les tweets.
-   Analyse de chaque tweet avec le service {{site.data.keyword.toneanalyzershort}} et comparaison des résultats pour identifier des corrélations.

### Résultats

IBM a identifié des corrélations entre le ton d'un tweet et une notation J'aime et entre le ton d'un tweet et son retweet.

## Prédiction de rencontres en ligne compatibles

Des millions de personnes dans le monde utilisent les rencontres en ligne pour rechercher cette personne spéciale. Les gens utilisent les rencontres en ligne pour trouver d'autres personnes avec beaucoup de points communs et pour se faire valoir comme partenaires potentiels.

### Objectifs

Etablir la corrélation entre le ton du profil d'un individu avec celui d'une personne potentiellement compatible. Etablir également si cette corrélation peut prédire une affinité avec une autre personne.

### Actions

-   Exploration d'environ 50000 profils utilisateur.
-   Analyse de chaque profil avec le service {{site.data.keyword.toneanalyzershort}}.
-   Définition de correspondances potentielles comme ceux ayant communiqué via le site.
-   Comparaison de l'analyse du ton des correspondances potentielles pour identifier des corrélations.
-   Développement d'un modèle statistique à partir des similarités de ton dans les profils pour prédire si deux utilisateurs sont susceptibles de communiquer. Puis comparaison du modèle avec plusieurs modèles de référence prenant en compte d'autres attributs tels que les données démographiques.

### Résultats

La similarité de ton entre les profils peut apporter une amélioration de 45 % dans la prévision de contact entre deux utilisateurs comparé aux prédicteurs utilisés d'ordinaire par les sites Web de rencontres. IBM a identifié une corrélation globale forte entre la similarité de ton et le nombre de messages échangés, comme illustré dans l'image suivante.

![Forte corrélation entre les tons analysés et le nombre de messages échangés.](images/case-study.png)
