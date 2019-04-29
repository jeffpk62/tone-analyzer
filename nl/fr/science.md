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

# Disciplines scientifiques sous-jacentes au service
{: #ssbts}

Le service {{site.data.keyword.toneanalyzerfull}} repose sur la théorie de la psycholinguistique, un secteur de recherche qui explore la relation entre le comportement linguistique et les théories de la psychologie. Le service utilise l'analyse linguistique et la corrélation entre les caractéristiques linguistiques du texte écrit et les tons émotionnels et du langage pour développer des scores pour chaque dimension de ton.
{: shortdesc}

Les chercheurs en psycholinguistique cherchent à comprendre si les mots que l'on utilise dans sa vie quotidienne reflètent son identité, ce qu’on ressent et ce qu’on pense. Après plusieurs décennies de recherche dans ce domaine, la psychologie, le marketing et d'autres disciplines conviennent que le langage reflète plus que ce que l'on désire exprimer. La fréquence à laquelle on utilise certains types de mots peut fournir des indications sur sa personnalité, son style de pensée, ses connexions sociales et ses états émotionnels.

Par exemple, les utilisateurs exposent divers tons dans leurs communications quotidiennes : joyeux ou triste, ouvert ou réservé, analytique ou informel ([Gou et coll., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gou) et [Jian et coll., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-jian)). Ces tons peuvent avoir une incidence sur la perception d'une personne en ligne et sur l'efficacité de leurs communications dans différents contextes.

Par ailleurs, dans les communications commerciales par e-mail, les gens sont enclins à percevoir avec une plus grande intensité les émotions négatives que les émotions positives ([Byron, 2008](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-byron)). Et, dans les médias sociaux, les gens présentent des identités en ligne différentes, qui affectent l'impression qu'ils laissent sur les autres ([DiMicco et Millen, 2007](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-dimicco)).

De nombreuses personnes lisent naturellement un message et jugent les tons transmis par l'expéditeur. Mais un ordinateur est-il capable de détecter avec précision et automatiquement les tons divulgués par un message ? Cette question est l'un des nombreux défis auxquels les chercheurs en intelligence artificielle et en sciences cognitives cherchent à trouver des réponses. Tout d'abord avec le service {{site.data.keyword.personalityinsightsshort}} et maintenant avec le service {{site.data.keyword.toneanalyzershort}}, IBM répond à cette question.

## Présentation de la recherche associée
{: #sorr}

La recherche démontre une corrélation forte et significative entre le choix de mots et la personnalité, les émotions, les besoins intrinsèques et les processus mentaux. Plusieurs chercheurs ont constaté que la fréquence d'utilisation de certaines catégories de mots varie d'une personne à l'autre pour les blogs, les essais et les tweets. Les chercheurs ont découvert que ces moyens de communication peuvent aider à prévoir différents aspects de la personnalité : 

-   [Fast et Funder (2008)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-fast)
-   [Gill et coll. (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gill)
-   [Golbeck et coll. (2011)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-golbeck)
-   [Hirsh et Peterson (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-yarkoni)

La plupart de ces travaux antérieurs se basaient sur la recherche de catégories de mots significatives sur le plan psychologique à partir de l'utilisation de mots à l'écrit. Cette recherche sert de base aux travaux d'IBM sur le service {{site.data.keyword.toneanalyzershort}}. En s'appuyant sur les résultats scientifiques de la recherche en psycholinguistique, IBM tente de dégager des caractéristiques de la personnalité des individus, leurs styles de pensée et d'écriture, leurs émotions et leurs besoins et valeurs intrinsèques à partir des mots qu'ils utilisent à l'écrit. IBM utilise des modèles d'apprentissage automatique pour évaluer ces caractéristiques en étudiant divers aspects de l'écriture d'une personne.

## Modèle générique
{: #analysis}

Le noeud final générique analyse le contenu écrit d'un ensemble de tons applicable à une grande variété d'utilisations. Le service {{site.data.keyword.toneanalyzershort}} calcule une fiche de score incluant les tons suivants :

-   Le **ton émotionnel** est dérivé des travaux IBM sur l'analyse des émotions, laquelle est une structure d'ensemble qui déduit des émotions à partir d'un texte. Pour dériver des scores d'émotion à partir du texte, IBM utilise une structure d'ensemble pyramidale basée généralisation ; la généralisation pyramidale utilise un modèle de haut niveau pour combiner les modèles en-dessous afin d'aboutir à une plus grande précision des prédictions. Les éléments tels que n-grammes (unigrammes, bigrammes et trigrammes), la ponctuation, émoticônes, les jurons, les formules de politesse (comme "bonjour", "hello" ou "merci"), et la polarité des sentiments sont introduits dans des algorithmes d'apprentissage automatique pour classifier les catégories d'émotions.
-   Le **ton du langage** est calculé à partir de l'analyse linguistique basée sur les traits révélés.

### Mesure de la qualité du service
{: #smqs}

IBM a mesuré la qualité du service {{site.data.keyword.toneanalyzershort}}, ainsi que les dimensions de ton mentionnées dans la section précédente :

-   Les catégories de *ton émotionnel* ont été mesurées vis à vis de jeux de données d'émotion standard tels que ISEAR et SEMEVAL. Les résultats indiquent que les performances moyennes du modèle d'ensemble (score F1 de macro-moyenne de l'ordre de 41 % et 68 %, pour les deux jeux de données) sont statistiquement meilleures que la précision optimale relevée pour les modèles de pointe (dont les scores F1 de macro-moyenne avoisinent 37 et 63 %).
-   Le *ton du langage* a été évalué dans une étude approfondie de plus de 200000 phrases collectées à partir de sources diverses telles que forums de discussion, discours, et médias sociaux. Parmi ces phrases, IBM en a sélectionné aléatoirement 1330 pour ton analytique, 1000 pour ton assuré et 1000 autres pour ton indécis. IBM a ensuite soumis ces phrases au service {{site.data.keyword.toneanalyzershort}} en demandant également à des personnes de les analyser.

    Pour l'analyse humaine, IBM a utilisé une plateforme de crowdsourcing dénommée [CrowdFlower ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.crowdflower.com/){: new_window} pour annoter les phrases sélectionnées avec différents labels. Seuls les évaluateurs avec des taux d'approbation au-dessus de 85 % ont été retenus pour participer à la tâche d'annotation. Cinq annotateurs ont libellé chaque phrase, IBM utilisant le résultat annoté prédominant par les cinq pour déterminer les libellés finals.
    -   Pour *ton analytique*, les personnes ont libellé 915 des 1330 phrases comme analytiques, 411 comme non analytiques et 4 comme non compréhensibles. En comparant le libellé anticipé avec ces libellés empiriques, IBM a constaté que la détection de ton analytique recevait un score F1 de 0,7518.
    -   Pour *ton indécis*, les personnes ont libellé 292 des 1000 phrases comme indécises, 706 comme non indécises et 2 comme non compréhensibles. En comparant le libellé anticipé avec ces libellés empiriques, IBM a constaté que la détection de ton indécis recevait un score F1 de 0,6369.
    -   Pour *ton assuré*, les personnes ont libellé 623 des 1000 phrases comme assurées, 374 comme non assurées et 3 comme non compréhensibles. En comparant le libellé anticipé avec ces libellés empiriques, IBM a constaté que la détection de ton assuré recevait un score F1 de 0,7288.

Globalement, les différences entre les libellés anticipés et les libellés empiriques ne sont pas statistiquement significatives. Ce résultat indique que le service fonctionne correctement.

## Modèle d'interaction avec les clients
{: #scem}

Le noeud final d'interaction avec les clients identifie des tons depuis le domaine de l'assistance clients. Pour sélectionner les tons à évaluer avec le modèle d'interaction avec les clients, IBM a d'abord réalisé une étude pour déterminer quelles dimensions de ton sont perçues comme importantes dans ce domaine :

1.  IBM a sélectionné un groupe de 53 tons dans les dimensions utilisées en marketing, celles utilisées pour décrire des styles d'écriture et des échelles d'émotion et de personnalité empruntées à la psychologie.
1.  IBM a demandé aux employés CrowdFlower d'évaluer le degré auquel les 53 attributs de ton décrivent une déclaration spécifique dans 1000 conversations avec l'assistance clients. Pour simplifier la tâche d'évaluation dans le contexte de crowdsourcing, IBM a divisé les 53 tons en quatre sous-ensembles. Les annotateurs humains n'avaient à évaluer qu'un sous-ensemble des tons. IBM a déterminé ensuite l'évaluation de tous les tons en agrégeant les résultats.
1.  IBM a effectué une analyse factorielle sur une matrice de corrélation de 53 par 53 et identifié au moins sept facteurs significatifs (dimensions). IBM a déterminé les noms des facteurs de sorte à représenter les concepts les plus importants reflétés par chacune des dimensions.

Ces étapes ont identifié sept dimensions de ton importantes pour le domaine de l'assistance clients : frustration, satisfaction, excitation, politesse, impolitesse, tristesse et sympathie.

### Collecte de données
{: #sdc}

IBM a utilisé les forums de support clients de Twitter comme source de données de conversation pour son analyse du ton dans le domaine de l'assistance clients. De nombreuses entreprises utilisent Twitter comme canal pour assurer le support de leurs clients. Des agents sont recrutés et formés pour suivre les tweets qui mentionnent la société, pour aiguiller les demandes d'aide et offrir une assistance rapide pour répondre aux besoins des clients.

Pour collecter autant de conversations que possible, IBM a sélectionné 62 marques disposant de comptes dédié au service clients sur Twitter. IBM a choisi ces marques de sorte à couvrir une grande diversité de secteurs, d'emplacements géographiques et de taille d'organisation. Globalement, IBM a collecté 2,6 millions de demandes utilisateur entre le 1er juin et le 1er août 2016.

### Annotation des données
{: #sda}

IBM a passé au crible les données collectées pour ne conserver que les conversations ayant reçu au moins une réponse et n'impliquant qu'un seul client et un seul agent. IBM a également supprimé du jeu de données toutes les conversations dans une langue autre que l'anglais et celles contenant des demandes ou des réponses comprenant des images. Pour préserver la confidentialité des utilisateurs et des entreprises, IBM a remplacé tous les éléments *@mentions* dans les conversations par *@customer*, *@[industry]_company* (par exemple, *@ecommerce_company* ou *@telecommunication_company*), *@competitor_company* ou *@other_users*.

Ce processus de sélection a identifié environ 96000 énoncés à annoter par les agents CrowdFlower. Pour promouvoir une meilleure compréhension du contexte d'annotation, IBM a demandé aux agents d'effectuer une annotation au niveau de la conversation, en libellant chaque énoncé impliqué dans une conversation. La nature subjective de certains des tons proposés pourrait conduire à des perceptions incohérentes. IBM a donc demandé aux annotateurs d'évaluer sur une échelle de Likert à quatre points allant de "Très fort" à "Pas du tout" à quel degré les énoncés illustraient le ton en question. Une échelle de Likert est préférable à une échelle binaire simple de type oui/non puisqu'elle permet une plus grande tolérance des perceptions diverses et génère des labels moins denses.

Cinq annotateurs différents ont libellé chaque conversation. IBM a utilisé uniquement des annotateurs basés aux Etats-Unis avec un niveau de performance acceptable dans des tâches d'annotation antérieures. IBM leur a également demandé de répondre correctement à cinq questions de formation avant de passer aux tâches d'annotation réelles. Les questions de formation avaient pour but de s'assurer que les annotateurs aient une notion de ce que chaque ton signifie dans le contexte de l'assistance clients. IBM a également intégré des questions de validation dans les tâches réelles pour confirmer la qualité des libellés des annotateurs.

IBM a utilisé la moyenne des scores des cinq annotateurs comme libellé final de chaque énoncé. IBM a ensuite utilisé un score de 1 comme seuil pour convertir les libellés en valeurs binaires. IBM a choisi 1 comme seuil sur la base d'observations des distributions des libellés et de la performance des modèles avec des seuils différents. Le résultat final a débouché sur la distribution suivante des énoncés : 9536 frustrés, 10806 satisfaits, 6107 excités, 63853 polis, 1688 impolis, 24954 tristes et 10475 compréhensifs.

### Apprentissage des modèles de ton
{: #sltm}

Sur la base de ces conversations en interaction avec les clients, IBM a éduqué un modèle d'apprentissage automatique reposant sur le modèle SVM (Support Vector Machine) pour prédire le ton des nouveaux énoncés d'assistance clients. Pour le modèle d’apprentissage automatique, IBM a exploité plusieurs catégories de fonctionnalités : 

-   Fonctions N-gram
-   Fonctions lexicales de différents dictionnaires 
-   L'existence de références à la deuxième personne dans la conversation 
-   Certaines fonctions spécifiques au dialogue, telles que les remerciements ou les excuses 
-   Plusieurs fonctions de niveau supérieur telles que l'existence de points d'interrogation ou d'exclamation consécutifs 

IBM a constaté qu'environ 30 % des échantillons étaient associés à plusieurs tons. IBM a donc opté pour l'élaboration d'une classification multi-labels plutôt que multi-classes. Pour chaque ton, IBM é éduqué le modèle indépendamment en utilisant un paradigme OVR (One-vs-Rest - Un contre tous). Le paradigme a utilisé les énoncés pour chaque classe en tant qu'échantillons positifs et tous les autres énoncés comme échantillons négatifs. IBM a identifié les tons prédits avec une probabilité d'au moins 0,5 comme tons finals. Pour certains tons, les données d'apprentissage étaient fortement déséquilibrées ; IBM a par conséquent identifié le poids optimal dans la fonction de coût pour chaque ton lors de l'apprentissage.

IBM a utilisé des scores de précision, de renvoi et le score F pour évaluer la précision de son modèle de classification. Le modèle fait preuve d'une grande précision comparé à un jeu de données de référence.
