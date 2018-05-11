---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-09"

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

# Übersicht für Entwickler
{: #overviewDevelopers}

Sie können über eine HTTP-REST-API (REST - Representational State Transfer) auf die Funktionen des Service {{site.data.keyword.toneanalyzershort}} zugreifen. Es sind auch mehrere Software-Development-Kits (SDKs) verfügbar, um die Anwendungsentwicklung in verschiedenen Sprachen und Umgebungen zu vereinfachen. Die folgenden Abschnitte enthalten eine Übersicht über die Anwendungsentwicklung mit dem Service.
{: shortdesc}

## Mit dem Service programmieren
{: #programming}

Um den Ton des Texts einer Person zu analysieren, übergeben Sie den Eingabetext mit der Methode `GET` oder `POST /v3/tone` an den Service. Um die Beiträge in einer Konversation zu analysieren, übergeben Sie die Eingabe mit der Methode `POST /v3/tone_chat` an den Service. In beiden Fällen gibt der Service die Analyse im JSON-Format zurück.

Weitere Informationen finden Sie in den Abschnitten [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer/using-tone.html) und [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer/using-tone-chat.html).

## Software-Development-Kits verwenden
{: #sdks}

Der Service {{site.data.keyword.toneanalyzershort}} unterstützt eine Reihe von SDKs zur einfacheren Anwendungsentwicklung. Die SDKs sind für viele gängige Programmiersprachen und Plattformen wie Node.js, Java, Python und Apple&reg; iOS verfügbar. Eine vollständige Liste der SDKs und Informationen zu deren Verwendung finden Sie unter [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html). Alle SDKs sind unter GitHub über den [Namensbereich "watson-developer-cloud" ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud){: new_window} verfügbar.

Informationen zur mobilen Entwicklung finden Sie unter [{{site.data.keyword.watson}} Developer Cloud Swift SDK ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}. Alle SDKs unterstützen die Authentifizierung mithilfe Ihrer Serviceberechtigungsnachweise oder eines Authentifizierungstokens.

## Weitere Informationen zur Anwendungsentwicklung
{: #learn}

Der Service {{site.data.keyword.toneanalyzershort}} unterstützt zwei typische Programmiermodelle: *Direkte Interaktion*, bei der der Kunde direkt mit dem Service kommuniziert, und *Relay über einen Proxy*, wobei der Kunde und der Service alle Daten (Anforderungen und Ergebnisse) über eine in {{site.data.keyword.Bluemix_short}} befindliche Proxyanwendung austauschen.

Weitere Informationen zur Arbeit mit {{site.data.keyword.watson}} Developer Cloud-Services und mit {{site.data.keyword.Bluemix_notm}} finden Sie in den folgenden Dokumenten:

-   Eine Einführung in die Arbeit mit {{site.data.keyword.watson}}-Services und {{site.data.keyword.Bluemix_notm}} finden Sie im Abschnitt [Einführung in {{site.data.keyword.watson}} und {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   Eine sprachunabhängige Einführung in die Entwicklung von {{site.data.keyword.watson}}-Serviceanwendungen in {{site.data.keyword.Bluemix_notm}} finden Sie im Abschnitt [{{site.data.keyword.Bluemix_notm}}-Entwicklungsansätze](/docs/services/watson/getting-started-bluemix.html).
-   Informationen zu den beiden Programmiermodellen, die für die Entwicklung von {{site.data.keyword.watson}}-Anwendungen verfügbar sind, finden Sie im Abschnitt [Programmiermodelle für {{site.data.keyword.watson}}-Services](/docs/services/watson/getting-started-develop.html):
    -   Beim Relay über einen Proxy kommuniziert der Kunde über einen in {{site.data.keyword.Bluemix_notm}} befindlichen Proxy-Server mit dem Service. Er übergibt alle Anforderungen über die Proxyanwendung. Ein Relay von Anforderungen über einen Proxy erfordert nur Serviceberechtigungsnachweise für die Authentifizierung bei dem Service. Weitere Informationen finden Sie im Abschnitt [Serviceberechtigungsnachweise für {{site.data.keyword.watson}}-Services](/docs/services/watson/getting-started-credentials.html).
    -   Bei direkter Interaktion verwendet der Kunde die Proxyanwendung in {{site.data.keyword.Bluemix_notm}} nur zum Abrufen eines Authentifizierungstokens für den Service. Danach kommuniziert er direkt mit dem Service. Bei direkter Interaktion werden Serviceberechtigungsnachweise nur zum Abrufen eines Tokens verwendet. Weitere Informationen finden Sie im Abschnitt [Tokens zur Authentifizierung](/docs/services/watson/getting-started-tokens.html).
-   Informationen zur Steuerung der standardmäßigen Protokollierung von Anforderungen, die für alle {{site.data.keyword.watson}}-Services ausgeführt wird, finden Sie im Abschnitt [Anforderungsprotokollierung für {{site.data.keyword.watson}}-Services steuern](/docs/services/watson/getting-started-logging.html).
