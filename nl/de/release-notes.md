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

# Releaseinformationen

In den folgenden Abschnitten werden die neuen Funktionen und Änderungen dokumentiert, die in das jeweilige Release des Service {{site.data.keyword.toneanalyzershort}} eingebunden wurden. Die Änderungen widersprechen dem vorhandenen Code nicht.
{: shortdesc}

> **Hinweis:** In den Releaseinformationen werden nun die *Serviceversion* und die *Schnittstellenversion* der einzelnen Aktualisierungen dokumentiert. Sie geben die *Schnittstellenversion* mit dem Abfrageparameter `version` an, um Komponenten und Funktionen zu verwenden, die mit dieser Aktualisierung verfügbar gemacht wurden. Der Service gibt beide Versionen mit dem Antwortheader `X-Service-Api-Version` zurück.

## 28. September 2017
{: #September2017b}

**Serviceversion:** `3.4.1`<br/> **Schnittstellenversion:** `2017-09-21`

-   Der Regulierungsgrenzwert für die maximale Anzahl Anforderungen, die ein einzelner {{site.data.keyword.Bluemix_notm}}-Benutzername übergeben kann, ist auf 1.200 Anforderungen pro Minute gestiegen. Der Service gibt den HTTP-Antwortcode 429 *Too many requests* zurück, wenn ein Benutzer diesen Grenzwert überschreitet.

## 25. September 2017
{: #September2017a}

**Serviceversion:** `3.4.1`<br/> **Schnittstellenversion:** `2017-09-21`

-   Der Endpunkt für allgemeine Zwecke (die Methode `/v3/tone`) wurde wie folgt geändert:

    -   Er unterstützt neben Englisch nun Eingabeinhalt auf Französisch (`fr`).
    -   Er gibt keine sozialen Töne mehr zurück.
    -   Er gibt bei den emotionalen Tönen nicht mehr "Ekel" (`disgust`) zurück.
    -   Er lässt alle Töne mit einem Wert unter `0,5` weg. Diese Qualifizierung entspricht der Antwort der Methode `/v3/tone_chat`.
    - Er gibt bei seiner Ausgabe keine Tonkategorien (Feld `tone_categories`) mehr zurück. Alle Töne, deren Werte den qualifizierenden Schwellenwert erfüllen, werden als Teil eines einzigen Objekts namens `tones` zurückgegeben. Weiterhin werden Töne standardmäßig immer für das vollständige Dokument und für jeden einzelnen Satz zurückgegeben.
    - Er akzeptiert nicht mehr den Abfrageparameter `tones` zur Begrenzung der Ausgabe auf angegebene Töne. Alle qualifizierenden Töne werden bei jeder Anforderung zurückgegeben. Den Parameter in eine Anforderung einzuschließen, führt nicht zu einem Fehler, hat jedoch keine Auswirkung auf die Antwort.
    - Er gibt bei einzelnen Sätzen nicht mehr die Felder `input_from` und `input_to` zurück. Die Methode gibt neben den Ergebnissen ihrer Analyse jetzt nur eine ID und den Text der einzelnen Sätze zurück.

-   Der Service gibt jetzt bei teilweise korrekter Eingabe in den folgenden Fällen den HTTP-Antwortcode 200 statt 400 zurück:

    -   Wenn Sie bei der Methode `/v3/tone` einen Eingabeinhalt von mehr als 128 KB oder 1000 Sätzen übergeben, gibt der Service bei seiner Antwort ein Feld `warning` zurück. Der Service analysiert die ersten 1000 Sätze auf Dokumentebene und - wie derzeit - nur die ersten 100 Sätze auf Satzebene. In älteren Versionen des Service wurde bei der Anforderung der Antwortcode 400 zurückgegeben, wenn einer der beiden Grenzwerte überschritten wurde. Beachten Sie auch, dass der Service jetzt Sätze mit weniger als drei Wörtern analysiert.
    -   Wenn Sie bei der Methode `/v3/tone_chat` mehr als 50 Äußerungen übergeben, gibt der Service auf der Ebene `warning` der Antwort ein Feld `warning` für den Gesamtinhalt zurück. Er analysiert nur die ersten 50 Äußerungen. Wenn Sie eine einzelne Äußerung übergeben, die mehr als 500 Zeichen enthält, gibt der Service ein Feld `error` für diese Äußerung zurück und analysiert sie nicht. In älteren Versionen des Service wurde der Antwortcode 400 zurückgegeben, wenn einer der beiden Grenzwerte überschritten wurde. Beachten Sie, dass der Service auch dann den Antwortcode 400 bei der Anforderung zurückgibt, wenn alle Äußerungen der Eingabe mehr als 500 Zeichen aufweisen.

-   Jetzt reguliert der Service die Anzahl der Anforderungen, die er von einem einzelnen Benutzer akzeptiert. Der Service gibt den HTTP-Antwortcode 429 *Too many requests* zurück, wenn er mehr als 600 Anforderungen pro Minute von einem einzelnen {{site.data.keyword.Bluemix_notm}}-Benutzernamen empfängt.

-   Die folgenden Änderungen gelten sowohl für den Endpunkt für allgemeine Zwecke als auch für den Endpunkt für Kundenengagement:

    -   Die mit dem Parameter `version` angegebene Schnittstellenversion ist `2017-09-21`, um die neueste Version des Service zu verwenden.
    -   Die Dokumentation wurde durch den Hinweis aktualisiert, dass der Service eine lokalisierte Ausgabe in einer Reihe von Sprachen erzeugen kann. Verwenden Sie den Anforderungsheader `Accept-Language`, um die gewünschte Sprache anzugeben.

## 6. Juli 2017
{: #July2017b}

**Serviceversion:** `3.3.6`<br/> **Schnittstellenversion:** `2016-05-19`

Die Dokumentation wurde mit einer kleinen Fehlerkorrektur am Endpunkt für Kundenengagement aktualisiert.

## Ältere Releases

-   [1. Juli 2017](#July2017a)
-   [8. Mai 2017](#May2017)
-   [17. April 2017](#April2017)
-   [15. März 2017](#March2017)
-   [1. Dezember 2016](#December2016)
-   [18. Oktober 2016](#October2016b)
-   [3. Oktober 2016](#October2016a)
-   [19. Mai 2016](#May2016)

### 1. Juli 2017
{: #July2017a}

**Serviceversion:** `3.3.5`<br/> **Schnittstellenversion:** `2016-05-19`

Der Endpunkt für Kundenengagement des Service {{site.data.keyword.toneanalyzershort}} ist jetzt allgemein verfügbar. Alle Aufrufe des Endpunkts werden jetzt mit derselben Gebühr berechnet wie Aufrufe des Endpunkts für allgemeine Zwecke.

### 8. Mai 2017
{: #May2017}

**Serviceversion:** `3.3.4`<br/> **Schnittstellenversion:** `2016-05-19`

IBM hat die Bewertungsmodelle für emotionale Töne sowie für Töne für Kundenbetreuung und Kundenengagement durch die Erweiterung des Trainingsdatasets aktualisiert. Jetzt haben die Modelle eine höhere Genauigkeit beim Vergleichsdataset.

### 17. April 2017
{: #April2017}

-   Speziell für die Kundenengagementdomäne ist jetzt eine neue Gruppe von Tönen verfügbar: *Frustriert*, *Zufrieden*, *Begeistert*, *Höflich*, *Unhöflich*, *Traurig* und *Mitfühlend*. Der Service erkennt diese Töne im Text einer Konversation zwischen einem Kunden und einem Mitarbeiter. Die Töne liegen derzeit in der Betaversion vor.
-   IBM hat Aktualisierungen am Bewertungsmodell für emotionale Töne freigegeben, die die Ergebnisse der Emotionen verbessern.

### 15. März 2017
{: #March2017}

IBM hat das Bewertungsmodell für emotionale Töne aktualisiert. Das Trainingsdataset wurde erweitert. Folglich haben die Modelle jetzt eine höhere Genauigkeit beim Vergleichsdataset.

### 1. Dezember 2016
{: #December2016}

IBM hat die Bewertungen der emotionalen Töne des Dokuments aktualisiert. Das neue Modell berücksichtigt bei der Zusammenfassung der Dokumentbewertung das Emotionsprofil von Sätzen.

### 18. Oktober 2016
{: #October2016b}

IBM hat die sozialen Töne erweitert. Der Service verwendet jetzt ein quelloffenes Verfahren zur Worteinbettung namens [GloVe ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://nlp.stanford.edu/projects/glove/){: new_window} zur Ableitung der Bewertung sozialer Töne. Dank dieser Änderung kann der Service bei der Berechnung sozialer Töne einen breiteren Wortschatz abdecken. Weitere Informationen zur Ableitung sozialer Töne finden Sie im Abschnitt [Die Wissenschaft hinter dem Service](http://www.ibm.com/watson/developercloud/doc/personality-insights/science.html) des Service {{site.data.keyword.personalityinsightsshort}}.

### 3. Oktober 2016
{: #October2016a}

IBM hat die Erkennung von Emotionen auf Satzebene erweitert. Der Service verwendet jetzt neue Trainingsdaten, einen neuen Featureauswahlprozess und erweiterte Wörterbücher für Wörter, Emojis und Slang. Diese Änderungen bewirken andere, erhebliche verbesserte Emotionsbewertungen auf Satzebene. Die API des Service wurde nicht geändert.

### 19. Mai 2016
{: #May2016}

Das allgemein verfügbare Release des Service {{site.data.keyword.toneanalyzershort}} enthält die folgenden neuen Funktionen:

-   Die Modelle des Service verwenden bei der Interpretation von Tönen eine verbesserte Sensitivität. Die Modelle verwenden jetzt mehr als nur lexikalische Einheiten. Sie berücksichtigen jetzt weitere Merkmale für Interpunktion, Emoticons, Sprachparameter (z. B. die Satzstruktur) und die Satzkomplexität.
-   Das Modell für schriftliche Töne wurde in das Modell für Sprachtöne umbenannt.
-   Die Modelle für Sprach- und emotionale Töne können jetzt Negationen verarbeiten.
-   Der Service gibt keine Antwort auf Sätze mit weniger als drei Wörtern mehr zurück.
-   Der Service hat jetzt eine einfachere und verbesserte [Demo ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://tone-analyzer-demo.mybluemix.net){: new_window}.
