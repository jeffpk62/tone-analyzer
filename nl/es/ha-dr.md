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

# Alta disponibilidad y recuperación tras desastre
{: #ha-dr}

El servicio {{site.data.keyword.toneanalyzerfull}} es altamente disponible en cualquier ubicación
de {{site.data.keyword.cloud_notm}}. No tiene requisitos de copia de seguridad y restauración para la recuperación tras desastre.
{: shortdesc}

## Alta disponibilidad
{: #high-availability}

El servicio {{site.data.keyword.toneanalyzershort}} está altamente disponible sin un solo punto de anomalía dentro de cualquier ubicación {{site.data.keyword.cloud_notm}} (por ejemplo, Dallas o Washington, DC). El servicio consigue una alta disponibilidad de forma automática y transparente mediante la característica de región multizona (MZR) proporcionada por {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} habilita varias zonas que no comparten un único punto de anomalía dentro de una única ubicación. También proporciona equilibrio de carga automático entre las zonas dentro de una región.

## Recuperación tras desastre
{: #disaster-recovery}

El servicio {{site.data.keyword.toneanalyzershort}} es sin estado. No almacena ningún dato de usuario en {{site.data.keyword.cloud_notm}}. En el caso de que se produzca un error catastrófico en una región, siga estos pasos:

1.  Cree una nueva instancia del servicio {{site.data.keyword.toneanalyzershort}} en una región distinta.
1.  Modifique la aplicación para que utilice el URL y las credenciales de la nueva instancia de servicio.
