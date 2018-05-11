---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-28"

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

# Produktinformation

> **Serviceaktualisierung:** *Der Service {{site.data.keyword.toneanalyzershort}} wurde am 25. und 28. September 2017 aktualisiert. Beim Endpunkt für allgemeine Zwecke wurden die Anforderungsparameter und der Antwortinhalt geändert. Außerdem gibt der Endpunkt jetzt nicht mehr soziale Töne oder den Ton "Ekel" zurück und akzeptiert Eingaben auf Französisch. Weitere Änderungen umfassen die Grenzwerte für Eingabe und Regulierung sowie die Schnittstellenversion. Der Service akzeptiert jetzt auch eine teilweise korrekte Eingabe und gibt nicht mehr einen Fehler für die gesamte Eingabe zurück. Weitere Informationen zu diesen und anderen Änderungen finden Sie in den [Releaseinformationen](/docs/services/tone-analyzer/release-notes.html).*

Der Service {{site.data.keyword.toneanalyzerfull}} verwendet linguistische Analysefunktionen, um emotionale und Sprachtöne in schriftlichen Texten zu erkennen. Der Service kann Töne auf Dokument- und Satzebene analysieren. Sie können mithilfe des Service verstehen, wie Ihre schriftliche Kommunikation wahrgenommen wird, und dann den Ton Ihrer Kommunikation verbessern. Unternehmen können mithilfe des Service den Ton der Kommunikation ihrer jeweiligen Kunden erlernen und jedem Kunden in der entsprechenden Weise antworten oder generell die Konversation mit ihren Kunden verstehen und verbessern.
{: shortdesc}

Sie übergeben an den Service Eingaben in JSON, Klartext oder HTML, die Ihren schriftlichen Inhalt enthalten. Der Service akzeptiert bis zu 128 KB Text. Das entspricht etwa 1000 Sätzen. Der Service gibt JSON-Ergebnisse zurück, die den Ton Ihrer Eingabe dokumentieren. Sie können aufgrund dieser Ergebnisse die Wahrnehmung und Effektivität Ihrer Kommunikation verbessern und dadurch sicherstellen, dass Ihre schriftlichen Äußerungen den für Ihre Zielgruppe gewünschten Ton und Stil aufweisen. Nachstehend finden Sie ein Diagramm mit den grundlegenden Abläufen von Aufrufen des Service.

![Übergeben Sie den Inhalt an den Service Tone Analyzer und verbessern Sie mit den Ergebnissen Ihre Kommunikation.](images/tone-analyzer.png)

## Endpunkte von Tone Analyzer

Der Service bietet zwei Endpunkte:

-   **Endpunkt für allgemeine Zwecke** (`GET` oder `POST /v3/tone`)

    Mit dem Endpunkt für allgemeine Zwecke von {{site.data.keyword.toneanalyzershort}} können Sie kürzere Webdaten wie E-Mail-Nachrichten oder Tweets bzw. längere Dokumente wie Artikel oder Blogbeiträge analysieren. Sie können soziale Medien überwachen, um zu verstehen, wie sich Kunden über eine Marke äußern, und zu bestimmen, wem Sie personalisierte Nachrichten zukommen lassen wollen. Der Endpunkt akzeptiert Eingaben in JSON, Klartext oder HTML. Weitere Informationen zu der Methode und den von ihr zurückgegebenen Tönen finden Sie im Abschnitt [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer/using-tone.html).

    In der [Demo "Allgemeine Zwecke" ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://tone-analyzer-demo.ng.bluemix.net/){: new_window} können Sie den Inhalt zur Analyse an den Service übergeben. Der Service gibt die Gesamtanalyse sowie die Analyse des Tons des Inhalts auf Satzebene zurück.
-   **Endpunkt für Kundenengagement** (`POST /v3/tone_chat`)

    Mit dem Endpunkt für Kundenengagement von {{site.data.keyword.toneanalyzershort}} können Sie Konversationen des Kundenservice und der Kundenunterstützung überwachen. Sie können Konversationen mit Kunden eskalieren, wenn diese einen ungünstigen Verlauf nehmen, oder nach Möglichkeiten suchen, Scripts, Dialogstrategien und Customer Journeys des Kundenservice zu verbessern. Der Endpunkt akzeptiert JSON-Eingaben. Weitere Informationen zu der Methode und den von ihr zurückgegebenen Tönen finden Sie im Abschnitt [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer/using-tone-chat.html).

    In der [Demo "Kundenengagement" ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://customer-engagement-analytics.mybluemix.net/){: new_window} werden Konversationen zwischen Kunden und Kundendienstmitarbeitern analysiert. Der Service misst die Zufriedenheit des Kunden und dessen Probleme, beurteilt die Leistung des Mitarbeiters und lässt Sie einschätzen, wie sich die Interaktion weiterentwickelt.

Informationen zu den für den Service verfügbaren Preistarifen finden Sie im Service [{{site.data.keyword.toneanalyzershort}} im {{site.data.keyword.Bluemix_short}}-Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/catalog/services/tone-analyzer){: new_window}.

## Anwendungsfälle

Nachstehend finden Sie einige interessante Anwendungsfälle:

-   *Social Listening und Zielgruppenüberwachung:* Sie können soziale Medien in Echtzeit überwachen, um zu verstehen, wie sich Kunden über Ihre Marke äußern. Sie könnten beispielsweise feststellen, dass Ihre Kunden in München nach einer Niederlage der Bayern traurig und während des Oktoberfests glücklich sind. (Endpunkt für allgemeine Zwecke)
-   *Personalisiertes Marketing:* Sie können bestimmen, wann und wem Sie personalisierte Nachrichten übermitteln. Ein Reiseveranstalter beispielsweise könnte glücklichen Kunden Nachrichten vom Typ "Belohnen Sie sich mit ...", traurigen Kunden Nachrichten vom Typ "Lassen Sie ... hinter sich" und verärgerten Kunden Nachrichten vom Typ "Sehen Sie's locker" schicken. (Endpunkt für allgemeine Zwecke)
-   *Chatbots:* Sie können einen automatisierten Mitarbeiter befähigen, Töne von Kunden zu erkennen und passende Antworten zu generieren. Sie könnten beispielsweise auf Traurigkeit mit "Es tut mir leid, dass Sie sich über dieses Problem ärgern" antworten und auf Zufriedenheit mit "Ich freue mich, dass Sie mit unserem Service zufrieden sind". (Endpunkt für Kundenengagement)
-   *Überwachung von Kundenengagement und Qualitätssicherung:* Sie können den Gesamtton der Kommunikation zwischen Mitarbeitern und Kunden überwachen, Anomalien erkennen und Gelegenheiten zur Schulung von Mitarbeitern markieren, um deren Kommunikation zu verbessern. (Endpunkt für Kundenengagement)

Außerdem können Sie den Service {{site.data.keyword.toneanalyzershort}} mit zusätzlichen {{site.data.keyword.ibmwatson_notm}}-Services wie [{{site.data.keyword.conversationfull}}](https://console.bluemix.net/docs/services/conversation/index.html) oder [{{site.data.keyword.speechtotextfull}}](https://console.bluemix.net/docs/services/speech-to-text/index.html) kombinieren, um die Benutzereingabe zu analysieren. Die Anwendung [Conversation Food Coach ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://food-coach.mybluemix.net/){: new_window} beispielsweise schult mithilfe des Service {{site.data.keyword.conversationshort}} Nutzer auf der Basis ihrer Antworten bezüglich der Lebensmittel, die sie essen, beim Treffen gesundheitsorientierter Entscheidungen zu Lebensmitteln. Weitere Informationen dazu finden Sie im folgenden [Watson-Blog-Post ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/watson/blog/2016/10/17/creating-a-compassionate-conversational-agent-using-watson-tone-analyzer-and-watson-conversation-services/){: new_window}.

> **Hinweis:** Der Service {{site.data.keyword.toneanalyzershort}} berechnet mithilfe von Algorithmen den Ton von schriftlichen Texten. Er leitet nicht die Persönlichkeitsmerkmale des Verfassers des Texts ab. Informationen zum Abrufen eines Persönlichkeitsportraits finden Sie im Service [{{site.data.keyword.personalityinsightsfull}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/services/personality-insights/index.html){: new_window}.

## Sprachunterstützung
{: #languages}

Die Methode `/v3/tone` kann Inhalt auf Englisch (`en`) und Französisch (`fr`) analysieren. Die Methode `/v3/tone_chat` unterstützt nur Englisch. Beide Methoden können in einer Reihe von Sprachen mit lokalisiertem Inhalt antworten. Weitere Informationen finden Sie in den Abschnitten [Endpunkt für allgemeine Zwecke verwenden](/docs/services/tone-analyzer/using-tone.html) und [Endpunkt für Kundenengagement verwenden](/docs/services/tone-analyzer/using-tone-chat.html).
