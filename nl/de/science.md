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

# Wissenschaft hinter dem Service
{: #ssbts}

Der Service {{site.data.keyword.toneanalyzerfull}} basiert auf der Theorie der Psycholinguistik, einem Forschungsgebiet, das die Beziehung zwischen sprachlichem Verhalten und psychologischen Theorien untersucht. Der Service entwickelt mithilfe linguistischer Analysen und der Korrelation zwischen Merkmalen von schriftlichem Text sowie emotionalen und Sprachtönen Bewertungen für jede dieser Tondimensionen.
{: shortdesc}

In der Psycholinguistik werden Forschungen zur Untersuchung der Frage angestellt, ob die Wörter, die von Personen im Alltag benutzt werden, Aufschluss über deren Persönlichkeit, über ihr emotionales Befinden sowie über ihre Denkweise geben können. Nach mehreren Jahrzehnten der Forschung gilt es heute in der Psychologie, im Marketing und in anderen Disziplinen als gesichert, dass Sprache mehr ausdrückt als die reine Bedeutung des gesprochenen Wortes. Die Häufigkeit, mit der Personen bestimmte Arten von Wörtern benutzen, kann Hinweise auf ihre Persönlichkeit, ihre Denkweise, auf ihre sozialen Verbindungen und ihre emotionale Befindlichkeit geben.

Menschen können beispielsweise in ihrer Alltagskommunikation verschiedene Töne verwenden: froh oder traurig, offen oder konservativ, analytisch oder informell ([Gou et al., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gou) und [Jian et al., 2014](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-jian)). Diese Töne können sich auf die Wahrnehmung der Onlineidentität einer Person und auf die Effektivität ihrer Kommunikation in unterschiedlichen Kontexten auswirken.

Zudem nehmen Menschen in geschäftlichen E-Mail-Kommunikationen negative Emotionen tendenziell intensiver wahr als positive Emotionen ([Byron, 2008](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-byron)). Und in sozialen Medien zeigen Menschen verschiedene Onlineidentitäten, die sich auf den Eindruck auswirken, den andere von ihnen haben ([DiMicco and Millen, 2007](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-dimicco)).

Viele Menschen lesen eine Nachricht und beurteilen die vom Absender übertragenen Töne ganz natürlich. Aber kann ein Computer die von einer Nachricht offenbarten Töne präzise und automatisch erkennen? Dies ist eine von vielen spannenden Fragen, auf die Forscher auf den Gebieten der künstlichen Intelligenz und der Kognitionswissenschaften Antworten suchen. IBM arbeitet an der Beantwortung dieser Frage - zuerst mit dem Service {{site.data.keyword.personalityinsightsshort}} und jetzt mit dem Service {{site.data.keyword.toneanalyzershort}}.

## Übersicht über die zugehörige Forschung
{: #sorr}

Die Forschung zeigt eine starke und statistisch signifikante Korrelation zwischen der Wortwahl und der Persönlichkeit, Emotionen, Haltungen, intrinsischen Bedürfnissen, Werten und Denkprozessen auf. Mehrere Forscher haben herausgefunden, dass Menschen bestimmte Wortkategorien unterschiedlich oft benutzen, wenn sie Blogs, Essays und Tweets schreiben. Außerdem wurde von den Forschern festgestellt, dass diese Kommunikationsmedien dabei helfen können, verschiedene Aspekte der Persönlichkeit vorherzusagen:

-   [Fast und Funder (2008)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-fast)
-   [Gill et al. (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-gill)
-   [Golbeck et al. (2011)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-golbeck)
-   [Hirsh und Peterson (2009)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-hirsh)
-   [Yarkoni (2010)](/docs/services/tone-analyzer?topic=tone-analyzer-references#bib-yarkoni)

Viele dieser früheren Arbeiten basieren auf der Suche nach psychologisch aussagekräftigen Wortkategorien aus der Verwendung von Wörtern in schriftlichen Texten. Diese Forschung dient IBM als Basis für die Arbeit am Service {{site.data.keyword.toneanalyzershort}}. IBM arbeitet auf der Grundlage wissenschaftlicher Erkenntnisse aus der psycholinguistischen Forschung daran, Persönlichkeitsmerkmale von Menschen, ihre Denk- und Schreibstile, ihre Emotionen sowie ihre intrinsischen Bedürfnisse und Werte aus den Wörtern abzuleiten, die sie schreiben. IBM wertet diese Merkmale mithilfe seiner Modelle für maschinelles Lernen aus, indem verschiedene Merkmale von schriftlichen Texten eines Menschen beurteilt werden.

## Modell für allgemeine Zwecke
{: #analysis}

Der Endpunkt für allgemeine Zwecke analysiert schriftlichen Inhalt in Bezug auf eine Gruppe von Tönen, die für ein breites Anwendungsspektrum gelten. Der Service {{site.data.keyword.toneanalyzershort}} berechnet eine Bewertungsliste, die die folgenden Töne umfasst:

-   **Emotionaler Ton:** wird aus der Arbeit von IBM zur Emotionsanalyse abgeleitet, die ein Ensembleframework darstellt, das Emotionen aus einem Text ableitet. Um Emotionsbewertungen aus einem Text abzuleiten, verwendet IBM ein gestapeltes, auf Verallgemeinerung basierendes Ensembleframework. Bei der gestapelten Verallgemeinerung werden Modelle niedrigerer Ebenen in einem allgemeinen Modell kombiniert, um eine höhere Genauigkeit bei Vorhersagen zu erreichen. Merkmale wie n-Gramme (Unigramme, Bigramme und Trigramme) Interpunktion, Emoticons, Kraftausdrücke, Begrüßungen (wie "Hallo", "Hi" und "Danke") sowie Gefühlspolarität werden in Algorithmen für maschinelles Lernen eingegeben, um Kategorien von Emotionen zu klassifizieren.
-   **Sprachton:** Wird auf der Basis erlernter Funktionen aus der linguistischen Analyse berechnet.

### Servicequalität messen
{: #smqs}

IBM maß die Qualität des Service {{site.data.keyword.toneanalyzershort}} anhand der im vorherigen Abschnitt genannten Tondimensionen:

-   Die Kategorien der *emotionalen Töne* wurden mit Standarddatasets für Emotionen wie ISEAR und SEMEVAL verglichen. Die Ergebnisse zeigen, dass die durchschnittliche Leistung des Ensemblemodells (der Makro-Durchschnitts-F1-Wert beträgt für die beiden Datasets jeweils ca. 41 und 68 Prozent) statistisch besser ist als die beste berichtete Genauigkeit der technologisch ausgereiften Modelle (deren Makro-Durchschnitts-F1-Werte jeweils bei ca. 37 und 63 Prozent liegen).
-   Die *Sprachtöne* wurden mithilfe einer umfassenden Studie ausgewertet, bei der über zweihunderttausend Sätze aus Quellen wie Debattenforen, Reden und sozialen Medien erfasst wurden. IBM hat nach dem Zufallsprinzip 1330 dieser Sätze für analytische Töne und 1000 Sätze für jeden der selbstbewussten und zaghaften Töne ausgewählt. Anschließend übergab IBM diese Sätze an den Service {{site.data.keyword.toneanalyzershort}} und bat auch Menschen, sie zu analysieren.

    Bei der Analyse durch Menschen verwendete IBM eine Crowdsourcingplattform namens [CrowdFlower ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.crowdflower.com/){: new_window}, um die ausgewählten Sätze mit verschiedenen Kennzeichnungen zu markieren. An den Kennzeichnungsaufgaben durften nur solche Bewerter teilnehmen, die eine Zustimmungsrate von über 85 aufwiesen. Jeder Satz wurde von fünf Bewertern gekennzeichnet und IBM legte die endgültige Kennzeichnung anhand der häufigsten dieser fünf Kennzeichnungen fest.
    -   Beim *Ton "analytisch"* kennzeichneten die Menschen 915 der 1330 Sätze als "analytisch", 411 als "nicht analytisch" und 4 als "nicht verständlich". Beim Vergleich der vorhergesagten Kennzeichnung mit diesen grundlegenden Kennzeichnungen ermittelte IBM einen F1-Wert von 0,7518 für die Erkennung seines analytischen Tons.
    -   Beim *Ton "zögernd"* kennzeichneten die Menschen 292 der 1000 Sätze als "zögernd", 706 als "nicht zögernd" und 2 als "nicht verständlich". Beim Vergleich der vorhergesagten Kennzeichnung mit den grundlegenden Kennzeichnungen ermittelte IBM einen F1-Wert von 0,6369 für die Erkennung seines zögernden Tons.
    -   Beim *Ton "zuversichtlich"* kennzeichneten die Menschen 623 der 1000 Sätze als "zuversichtlich", 374 als "nicht zuversichtlich" und 3 als "nicht verständlich". Beim Vergleich der vorhergesagten Kennzeichnung mit den grundlegenden Kennzeichnungen ermittelte IBM einen F1-Wert von 0,7288 für die Erkennung seines zuversichtlichen Tons.

Insgesamt sind die Unterschiede zwischen den vorhergesagten Kennzeichnungen und den Ground-Truth-Kennzeichnungen statistisch nicht signifikant. Dieses Ergebnis zeigt, dass der Service gut funktioniert.

## Modell für Kundenengagement
{: #scem}

Der Endpunkt für das Kundenengagement identifiziert Töne aus der Kundenbetreuungsdomäne. Zur Auswahl der mit dem Modell für Kundenengagement auszuwertenden Töne führte IBM zuerst eine Studie aus, mit der ermittelt wurde, welche Dimensionen eines Tons als wichtig in der Domäne wahrgenommen werden:

1.  IBM wählte eine Gruppe von 53 Tönen aus den im Marketing verwendeten Dimensionen, aus den zur Beschreibung von Schreibstilen verwendeten Dimensionen sowie aus den Emotions- und Persönlichkeitsskalen der Psychologie aus.
1.  IBM bat Mitarbeiter auf CrowdFlower um deren Bewertung, inwieweit die 53 Tonattribute in 1000 Kundenbetreuungskonversationen eine bestimmte Äußerung beschreiben. Zur Vereinfachung der Bewertungsaufgabe im Kontext von Crowdsourcing teilte IBM die 53 Töne in vier Untergruppen ein. Die menschlichen Bewerter mussten nur eine Teilmenge der Töne bewerten. Dann aggregierte IBM diese Ergebnisse und ermittelte daraus Bewertungen für alle Töne.
1.  IBM führte in einer 53x53-Korrelationsmatrix eine Faktorenanalyse aus und fand mindestens sieben bedeutende Faktoren (Dimensionen). IBM bestimmte die Namen von Faktoren, um die wichtigsten durch die einzelnen Dimensionen ausgedrückten Konzepte darzustellen.

Mit diesen Schritten wurden sieben wichtige Tondimensionen für die Kundenbetreuungsdomäne ermittelt: Frustration, Zufriedenheit, Begeisterung, Höflichkeit, Unhöflichkeit, Traurigkeit und Mitgefühl.

### Datenerfassung
{: #sdc}

IBM verwendete Kundenunterstützungsforen von Twitter als Quellen von Konversationsdaten zur Analyse von Tönen in der Kundenbetreuungsdomäne. Viele Unternehmen verwenden Twitter als Kanal zur Unterstützung ihrer Kunden. Mitarbeiter werden angestellt und darin geschult, Tweets zu überwachen, in denen das Unternehmen erwähnt wird, Hilfeanforderungen weiterzuleiten und Kundenbedürfnisse anzusprechen.

Um so viele Konversationen wie möglich zu erfassen, wählte IBM 62 Marken aus, die dedizierte Konten für den Kundenservice auf Twitter besitzen. Bei der Auswahl dieser Marken achtete IBM darauf, eine große Bandbreite an Branchen, Standorten und Organisationsgrößen abzudecken. Insgesamt erfasste IBM 2,6 Millionen Benutzeranforderungen zwischen dem 1. Juni und dem 1. August 2016.

### Markierung der Daten
{: #sda}

IBM sichtete das erfasste Dataset und behielt nur diejenigen Konversationen, auf die mindestens eine Antwort einging und an denen nur jeweils ein Kunde und ein Mitarbeiter beteiligt waren. Außerdem entfernte IBM alle Konversationen, die nicht auf Englisch waren, sowie alle Konversationen aus dem Dataset, die Bilder in den Anfragen oder Antworten enthielten. Zum Schutz der Vertraulichkeit der Benutzer und Unternehmen ersetzte IBM alle Erwähnungen (*@mentions*) in einer Konversation durch *@customer* bzw. *@[industry]_company* (beispielsweise *@ecommerce_company*, *@telecommunication_company*), *@competitor_company* oder *@other_users*.

Bei diesem Auswahlverfahren wurden etwa 96.000 Äußerungen in Konversationen für die Markierung durch Mitarbeiter von CrowdFlower identifiziert. Zum besseren Verständnis des Markierungskontexts bat IBM die Mitarbeiter um die Markierung auf Konversationsebene, wobei alle Äußerungen einer Konversation gekennzeichnet wurden. Die subjektive Natur einiger der vorgeschlagenen Töne könnte zu nicht einheitlichen Wahrnehmungen führen. IBM bat die Bewerter, auf einer vierstufigen Likert-Skala, die von "Sehr stark" bis "Überhaupt nicht" reichte, anzugeben, wie stark diese Äußerungen ihrer Meinung nach die Töne darstellten. Eine Likert-Skala ist einer einfachen binären Ja-/Nein-Skala vorzuziehen, da sie eine größere Toleranz für verschiedene Wahrnehmungen bietet und fundiertere Kennzeichnungen generiert.

Jede Konversation wurde von fünf Bewertern markiert. IBM verwendete nur Bewerter aus den USA, die bei früheren Markierungsaufgaben eine akzeptable Leistung geboten hatten. IBM verlangte außerdem von den Bewertern, fünf Trainingsfragen zu beantworten, bevor sie zu den eigentlichen Markierungsaufgaben übergehen konnten. Mit den Trainingsfragen wurde sichergestellt, dass die Bewerter verstanden, welche Bedeutung die einzelnen Töne im Kontext von Kundenservice hatten. Zudem band IBM Validierungsfragen in die eigentlichen Aufgaben ein, um die Qualität der Kennzeichnungen der Bewerter weiter zu validieren.

IBM verwendete den Durchschnitt aus den Werten der fünf Bewerter als endgültige Kennzeichnung der jeweiligen Äußerung. Dann wandelte IBM die Kennzeichnungen mithilfe eines Schwellenwerts von 1 in Binärwerte um. Die Auswahl des Schwellenwerts 1 durch IBM basierte auf den Verteilungen der Kennzeichnungen und auf der Leistung der Modelle mit verschiedenen Schwellenwerten. Die Endergebnisse brachten folgende Verteilung der Äußerungen: 9536 frustriert, 10.806 zufrieden, 6107 begeistert, 63.853 höflich, 1688 unhöflich, 24.954 traurig und 10.475 mitfühlend.

### Tonmodelle erlernen
{: #sltm}

Aufbauend auf diesen Konversationen zum Kundenengagement, schulte IBM ein auf SVM (Support Vector Machine) basierendes Modell für maschinelles Lernen in der Vorhersage von Tönen bei neuen Äußerungen im Bereich der Kundenbetreuung. Für das Modell für maschinelles Lernen nutzte IBM mehrere Featurekategorien:

-   N-Gramm-Features
-   Lexikalische Features aus verschiedenen Wörterbüchern
-   Vorhandensein von Referenzen in der zweiten Person in der Konversation
-   Bestimmte dialogspezifische Features wie z. B. Bedanken oder Entschuldigen
-   Bestimmte Features einer höheren Ebene wie z. B. das Vorhandensein von aufeinanderfolgenden Frage- oder Ausrufezeichen

IBM fand heraus, dass etwa 30 Prozent der Beispiele mehrere Töne zugeordnet wurden. Daher entschied sich IBM dafür, eine Klassifikationsaufgabe mit mehreren Kennzeichnungen anstatt mit mehreren Klassen zu lösen. IBM schulte das Modell für jeden Ton separat, und zwar mithilfe eines OVR-Paradigmas (OVR, One-vs-Rest = einer gegen den Rest). Bei diesem Paradigma wurden die Äußerungen für die einzelnen Klassen als positive Beispiele und alle übrigen Äußerungen als negative Beispiele verwendet. IBM identifizierte die vorhergesagten Töne mit einer Wahrscheinlichkeit von mindestens 0,5 als endgültige Töne. Bei einigen Tönen waren die Trainingsdaten sehr unausgeglichen. Daher identifizierte IBM während der Schulung den optimalen Gewichtungswert der Kostenfunktion für jeden Ton.

IBM verwendete Genauigkeit, Recall und F-Wert zur Auswertung der Richtigkeit des Klassifizierungsmodells. Das Modell zeigte eine hohe Richtigkeit beim Vergleich mit einem Vergleichsdataset.
