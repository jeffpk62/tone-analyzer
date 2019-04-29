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

# Alta disponibilità e ripristino di emergenza
{: #ha-dr}

Il servizio {{site.data.keyword.toneanalyzerfull}} è altamente disponibile in qualsiasi ubicazione di {{site.data.keyword.cloud_notm}}. Non ha alcun requisito di backup e ripristino per il ripristino di emergenza.
{: shortdesc}

## Alta disponibilità
{: #high-availability}

Il servizio {{site.data.keyword.toneanalyzershort}} è altamente disponibile senza un singolo punto di errore in qualsiasi ubicazione {{site.data.keyword.cloud_notm}} (ad esempio, Dallas o Washington, DC). Il servizio raggiunge l'alta disponibilità in modo automatico e trasparente mediante la funzione MZR (multi-zone region) fornita da {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} abilita più zone che non condividono un singolo punto di errore all'interno di una singola ubicazione. Fornisce anche il bilanciamento del carico automatico tra le zone all'interno di una regione.

## Ripristino di emergenza
{: #disaster-recovery}

Il servizio {{site.data.keyword.toneanalyzershort}} è senza stato. Non memorizza dati utente su {{site.data.keyword.cloud_notm}}. In caso di un errore catastrofico in una regione, completa la seguente procedura:

1.  Crea una nuova istanza del servizio {{site.data.keyword.toneanalyzershort}} in un'altra regione.
1.  Modifica la tua applicazione per utilizzare l'URL e le credenziali per la nuova istanza del servizio.
