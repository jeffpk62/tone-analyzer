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

# Übersicht für Entwickler
{: #overviewDevelopers}

Sie können über eine HTTP-REST-API (REST - Representational State Transfer) auf die Funktionen des Service {{site.data.keyword.toneanalyzershort}} zugreifen. Es sind auch mehrere Software-Development-Kits (SDKs) verfügbar, um die Anwendungsentwicklung in verschiedenen Sprachen zu vereinfachen. Die folgenden Abschnitte enthalten eine Übersicht über die Anwendungsentwicklung mit dem Service.
{: shortdesc}

## Mit dem Service programmieren
{: #programming}

Um den Ton des Texts einer Person zu analysieren, übergeben Sie den Eingabetext mit der Methode `GET` oder `POST /v3/tone` an den Service. Um die Beiträge in einer Konversation zu analysieren, übergeben Sie die Eingabe mit der Methode `POST /v3/tone_chat` an den Service. In beiden Fällen gibt der Service die Analyse im JSON-Format zurück. Weitere Informationen finden Sie in den folgenden Quellen:

-   [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer?topic=tone-analyzer-utgpe)
-   [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer?topic=tone-analyzer-utco)

## Software-Development-Kits verwenden
{: #sdks}

SDKs stehen für den Service {{site.data.keyword.toneanalyzershort}} zur Verfügung, um die Anwendungsentwicklung zu vereinfachen. Die {{site.data.keyword.ibmwatson}}-SDKs sind für viele gängige Programmiersprachen und Plattformen verfügbar.

-   Eine vollständige Liste der SDKs und Links zu den SDKs unter GitHub finden Sie unter [SDKs verwenden](/docs/services/watson?topic=watson-using-sdks).
-   Detaillierte Informationen zu allen Methoden der Node-, Java-, Python-, Ruby- und Go-SDKs für den Service {{site.data.keyword.toneanalyzershort}} finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

## Weitere Informationen zur Anwendungsentwicklung
{: #learn}

Weitere Informationen zur Arbeit mit den {{site.data.keyword.watson}}-Services und mit {{site.data.keyword.cloud}} finden Sie auf den folgenden Seiten:

-   Eine Einführung in die Arbeit mit {{site.data.keyword.watson}}-Services und {{site.data.keyword.cloud_notm}} finden Sie im Abschnitt [Einführung in {{site.data.keyword.watson}} und {{site.data.keyword.cloud_notm}}](/docs/services/watson?topic=watson-about).
-   Alle neuen Serviceinstanzen verwenden zur Authentifizierung {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). Ältere Serviceinstanzen verwenden möglicherweise weiterhin die Angaben für `{username}` und `{password}` aus den vorhandenen Cloud Foundry-Serviceberechtigungsnachweisen für die Authentifizierung. Weitere Informationen zur Authentifizierung beim Service finden Sie in den Releaseinformationen im Abschnitt zur [Serviceaktualisierung vom 30. Oktober 2018](/docs/services/tone-analyzer?topic=tone-analyzer-rnrn#October2018).
-   Die Anforderungsprotokollierung ist für den Service {{site.data.keyword.toneanalyzershort}} inaktiviert. Der Service führt keine Protokollierung der Anforderungen und Antworten durch und bewahrt die entsprechenden Daten auch nicht auf. Dabei spielt es keine Rolle, ob der Anforderungsheader `X-Watson-Learning-Opt-Out` definiert wurde.
