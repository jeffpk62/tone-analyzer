---

copyright:
  years: 2019
lastupdated: "2019-03-19"

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

# Haute disponibilité et récupération après sinistre
{: #ha-dr}

Le service {{site.data.keyword.toneanalyzerfull}} offre la haute disponibilité dans n'importe quel emplacement {{site.data.keyword.cloud_notm}}. Il n'a pas d'exigences de sauvegarde et de restauration pour la récupération après sinistre.
{: shortdesc}

## Haute disponibilité
{: #high-availability}

Le service {{site.data.keyword.toneanalyzershort}} offre la haute disponibilité, sans point de défaillance unique, dans tous les emplacements {{site.data.keyword.cloud_notm}} (par exemple, Dallas ou Washington, DC). Le service atteint automatiquement et de manière transparente la haute disponibilité au moyen de la fonctionnalité de région multi-zones (MZR) fournie par {{site.data.keyword.cloud_notm}}. 

{{site.data.keyword.cloud_notm}} active plusieurs zones qui ne partagent pas un seul point de défaillance au sein d'un même emplacement. Il fournit également un équilibrage automatique de la charge entre les zones d'une région. 

## Reprise après incident 
{: #disaster-recovery}

Le service {{site.data.keyword.toneanalyzershort}} est sans état. Il ne stocke aucune donnée utilisateur sur {{site.data.keyword.cloud_notm}}. En cas de défaillance catastrophique dans une région, procédez comme suit : 

1.  Créez une nouvelle instance du service {{site.data.keyword.toneanalyzershort}} dans une région différente.
1.  Modifiez votre application pour qu'elle utilise l'URL et les données d'identification de la nouvelle instance de service. 
