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

# Fallstudien

Lesen Sie diese Fallstudien zur Inspiration für die Aufgaben, die Sie mit dem Service {{site.data.keyword.toneanalyzerfull}} ausführen können. In den Studien wird die Korrelation zwischen berichteten Tönen und erwarteten Ergebnissen beschrieben. Die Korrelation kann positiv oder negativ sein und umfasst einen Bereich von -1,0 bis 1,0.
{: shortdesc}

## Kundenzufriedenheit in Unterstützungsforen vorhersagen

IBM analysierte Kundenunterstützungsforen bei einem Softwareanbieter, der mehrere Branchen im Fokus hat. Das Unternehmen verfasst aktiv Beiträge in Kundenunterstützungsforen. Benutzer können *Kudos* für Antworten vergeben, die sie hilfreich finden.

### Ziele

Sagen Sie die Kundenzufriedenheit aus dem Ton der Frage und Antwort vorher. IBM nahm an, dass eine Antwort mit Kudos bedeutete, dass der Benutzer zufrieden war.

### Aktionen

-   Die 1000 neuesten Threads in mehreren Foren wurden durchlaufen, um sicherzustellen, dass die gleiche Anzahl von Antworten mit und ohne Kudos einbezogen wurde.
-   Sowohl die Fragen als auch die Antworten wurden analysiert.
-   Es wurden mehrere technologisch ausgereifte Klassifikationsmerkmale wie Naive Bayes, Support Vector Machine (SVM) und Random Forest angewendet, um vorherzusagen, ob eine Antwort Kudos bekommen würde.

### Ergebnisse

Der Service kann Kudos mit einer Genauigkeit von 66 Prozent vorhersagen. IBM ermittelte folgende Korrelationen zwischen den Tönen einer Antwort im Forum und der Vergabe von Kudos für diese Antwort:

-   Je zuversichtlicher eine Antwort ist, desto größer ist die Wahrscheinlichkeit, dass sie Kudos bekommt (Korrelation von 0,23 zwischen einem hohen Wert für Zuversicht und Kudos).
-   Je zögernder eine Antwort ist, desto geringer ist die Wahrscheinlichkeit, dass sie Kudos bekommt (negative Korrelation von -0,27 zwischen einem hohen Wert für "zögernd" und Kudos).

## Kundenzufriedenheit in Twitterantworten vorhersagen

Viele Unternehmen stellen ihre Kundenunterstützung auf Twitter um. Bei Twitter können Antworten in Echtzeit erfolgen. Das trägt dazu bei, dass die Marke als Marke mit echten Menschen wahrgenommen wird, die sich um ihre Kunden kümmern.

IBM analysierte 333 Konversationen der Kundenunterstützung auf Twitter. Die Kunden waren mit 240 Konversationen zufrieden und mit 93 Interaktionen nicht zufrieden. Zur Messung der Zufriedenheit las IBM die Konversationen und markierte sie. Wenn Antworten das Problem lösten und der Kunde zufrieden schien, wurden sie mit "Kunde zufrieden" markiert. Wurde das Problem nicht zur Zufriedenheit des Kunden gelöst, wurden sie mit "Kunde nicht zufrieden" markiert.

### Ziele

Überprüfen Sie, ob der Ton von Konversationen zwischen dem Mitarbeiter und dem Kunden eine Auswirkung auf die Kundenzufriedenheit insgesamt hatte. Ermitteln Sie außerdem die Tonmerkmale, die eine erhebliche Auswirkung auf die Kundenzufriedenheit haben.

### Aktionen

-   Aus den Tweets wurden die Interpunktion sowie Erwähnungen und Links entfernt.
-   Jede Interaktion wurde in Kundentweets und Unterstützungstweets aufgeteilt.
-   Alle an der Konversation Beteiligten wurden mit dem Service {{site.data.keyword.toneanalyzershort}} analysiert und die Ergebnisse wurden verglichen, um Korrelationen zu finden.

### Ergebnisse

Der Service kann die Kundenzufriedenheit aus dem Ton der Antwort mit einer Genauigkeit von 67 Prozent vorhersagen. IBM ermittelte die folgende Korrelation zwischen dem Ton von Kundentweets und der Zufriedenheit des Kunden mit der Antwort:

-   Je verärgerter Kunden sind, desto geringer ist die Wahrscheinlichkeit, dass sie mit der Antwort zufrieden sind (negative Korrelation von -0,198 zwischen einem hohen Wert für Ärger in einem Kundentweet und der Kundenzufriedenheit).

## Applaus bei TED Talk vorhersagen

TED ist eine Organisation ohne Gewinnstreben, die globale Konferenzen mit dem Slogan "Ideas worth spreading" (Ideen, die es wert sind, verbreitet zu werden) ausrichtet. Redner bei TED Talk können in 18 Minuten mithilfe innovativer und fesselnder Erzählkunst eine Vielzahl von Themen aus den forschungsbezogenen und praktischen Bereichen von Wissenschaft und Kultur ansprechen. Nicht alle TED Talks kommen gut an und ein Verfahren zur Messung der Zufriedenheit der Zuhörer mit einem Vortrag besteht in der Messung der erhaltenen Applausmenge.

### Ziele

Ermitteln Sie, welche Tonmuster in TED Talks Applaus auslösen und welche nicht. Sagen Sie außerdem den Applaus auf der Basis des Tons eines Satzes voraus.

### Aktionen

Sätze, die Applaus erhielten, wurden im Dataset bereits mit Tags versehen.

-   Es wurden 1931 TED Talks geprüft.
-   Ein mit dem Tag "Applaus" versehener Satz wurde als "Applaustext" kategorisiert. Außerdem wurden die drei Sätze vor dem Satz mit dem Tag "Applaustext" und die drei Sätze nach dem Satz mit dem Tag "Nichtapplaustext" versehen.
-   Sowohl der Applaustext als auch der Nichtapplaustext wurden mit dem Service {{site.data.keyword.toneanalyzershort}} analysiert.
-   Auf Basis der gefundenen Korrelationen wurden Klassifikationsmerkmale erstellt, um den Applaus in anderen TED Talks auf Basis ihres Tons vorherzusagen.

### Ergebnisse

Der Service kann Applaus mit einer Genauigkeit von 75 Prozent vorhersagen. IBM ermittelte folgende Korrelationen zwischen dem Ton der einzelnen Satzgruppen und dem Spenden von Applaus für diese Sätze:

-   Je mehr Traurigkeit ein Redner ausdrückt, desto geringer ist die Wahrscheinlichkeit, dass er Applaus bekommt (negative Korrelation von -0,055 zwischen einem hohen Wert für Traurigkeit und Applaus).
-   Je emotionsloser oder unpersönlicher ein Redner wirkt, desto geringer ist die Wahrscheinlichkeit, dass er Applaus bekommt (negative Korrelation von -0,29 zwischen einem hohen Wert für "analytisch" und Applaus).
-   Je froher, glücklicher und zufriedener ein Redner wirkt, desto größer ist die Wahrscheinlichkeit, dass er Applaus bekommt (Korrelation von 0,21 zwischen einem hohen Wert für Freude und Applaus).

## Retweets und Likes bei Twitter vorhersagen

Eine Marke auf Twitter zu etablieren, wird zunehmend eine Voraussetzung für den Erfolg von Unternehmen. Um Sie oder Ihr Unternehmen so darzustellen, dass Follower Sie als wertvoll wahrnehmen, müssen Sie unbedingt Tweets erstellen, die viele Likes und Retweets generieren.

### Ziele

Suchen Sie Korrelationen zwischen dem Ton eines Tweets und dem Vorhandensein von Likes oder Retweets zu diesem Tweet.

### Aktionen

-   5881 Tweets verschiedener Geschäftskonten auf Twitter wurden durchlaufen.
-   Aus den Tweets wurden die Interpunktion sowie Erwähnungen und Links entfernt.
-   Alle Tweets wurden mit dem Service {{site.data.keyword.toneanalyzershort}} analysiert und die Ergebnisse wurden verglichen, um Korrelationen zu finden.

### Ergebnisse

IBM fand Korrelationen zwischen dem Ton eines Tweets und dem Vorhandensein von Likes dazu sowie zwischen dem Ton eines Tweets und dem Vorhandensein von Retweets dazu.

## Übereinstimmungen bei Onlinepartnersuche vorhersagen

Millionen Menschen auf der Welt nutzen die Onlinepartnersuche, um einen passenden Partner zu finden. Menschen verwenden die Onlinepartnersuche, um andere Menschen zu finden, die viele Gemeinsamkeiten mit ihnen aufweisen, und um sich als potenzielle Partner darzustellen.

### Ziele

Korrelieren Sie den Ton des Profils eines Menschen mit dem Ton des Profils eines potenziellen Partners. Ermitteln Sie außerdem, ob diese Korrelation einen Erfolg bei der Partnersuche vorhersagen würde.

### Aktionen

-   Etwa 50.000 Benutzerprofile wurden durchlaufen.
-   Alle Profile wurden mit dem Service {{site.data.keyword.toneanalyzershort}} analysiert.
-   Als potenzielle Partner wurden Personen definiert, die über die Site miteinander kommunizierten.
-   Die Tonanalyse potenzieller Partner wurde verglichen, um Korrelationen zu finden.
-   Aus der Tonähnlichkeit der Profile wurde ein statistisches Modell entwickelt, um vorherzusagen, ob zwei Benutzer miteinander kommunizieren würden. Dann wurde das Modell mit mehreren Vergleichsdaten verglichen, die andere Attribute wie Demografie berücksichtigen.

### Ergebnisse

Die Tonähnlichkeit zwischen Profilen kann im Vergleich zu Vorhersagefunktionen, die normalerweise von Websites zur Partnersuche verwendet werden, eine 45-prozentige Verbesserung bei der Vorhersage bewirken, ob zwei Benutzer miteinander kommunizieren. IBM ermittelte eine enge Gesamtkorrelation zwischen der Tonähnlichkeit und der Anzahl der ausgetauschten Nachrichten, wie in der folgenden Abbildung dargestellt.

![Enge Korrelation zwischen den analysierten Tönen und der Anzahl der ausgetauschten Nachrichten.](images/case-study.png)
