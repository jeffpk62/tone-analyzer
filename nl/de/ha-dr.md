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

# Hochverfügbarkeit und Wiederherstellung nach Stör-/Katastrophenfall
{: #ha-dr}

Der Service {{site.data.keyword.toneanalyzerfull}} verfügt an allen {{site.data.keyword.cloud_notm}}-Standorten über Hochverfügbarkeit. Für die Wiederherstellung nach einem Stör-/Katastrophenfall bestehen keine Anforderungen in Bezug auf die Sicherung und Wiederherstellung.
{: shortdesc}

## Hochverfügbarkeit
{: #high-availability}

Der Service {{site.data.keyword.toneanalyzershort}} ist hoch verfügbar, sodass an keinem {{site.data.keyword.cloud_notm}}-Standort (z. B. Dallas oder Washington, DC) eine Single Point of Failure-Situation auftreten kann. Der Service erreicht die Hochverfügbarkeit automatisch und transparent mithilfe der MZR-Funktion (MZR = Multi-Zone Region; Mehrzonenregion), die von {{site.data.keyword.cloud_notm}} bereitgestellt wird.

{{site.data.keyword.cloud_notm}} ermöglicht den Einsatz mehrerer Zonen, die keinen gemeinsamen Single Point of Failure in Bezug auf einen bestimmten Standort haben. Außerdem stellt das Produkt zonenübergreifend den automatischen Lastausgleich innerhalb einer Region bereit.

## Wiederherstellung nach Stör-/Katastrophenfall
{: #disaster-recovery}

Bei {{site.data.keyword.toneanalyzershort}} handelt es sich um einen statusunabhängigen Service. Es werden keine Benutzerdaten in {{site.data.keyword.cloud_notm}} gespeichert. Wenn in einer Region ein Fehler aufgrund eines Stör- oder Katatrophenfalls auftritt, müssen Sie die folgenden Schritte ausführen:

1.  Erstellen Sie in einer anderen Region eine neue Instanz des Service {{site.data.keyword.toneanalyzershort}}.
1.  Ändern Sie Ihre Anwendung so, dass die URL und die Berechtigungsnachweise der neuen Serviceinstanz verwendet werden.
