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

# Releaseinformationen
{: #rnrn}

In den folgenden Abschnitten werden die neuen Funktionen und Änderungen dokumentiert, die in das jeweilige Release des Service {{site.data.keyword.toneanalyzershort}} eingebunden wurden. Die Änderungen widersprechen dem vorhandenen Code nicht.
{: shortdesc}

In den Releaseinformationen werden die *Serviceversion* und die *Schnittstellenversion* der einzelnen Aktualisierungen dokumentiert. Sie geben die *Schnittstellenversion* mit dem Abfrageparameter `version` an, um Komponenten und Funktionen zu verwenden, die mit dieser Aktualisierung verfügbar gemacht wurden. Der Service gibt beide Versionen mit dem Antwortheader `X-Service-Api-Version` zurück.
{: note}

## 22. Februar 2019
{: #February2019}

**Serviceversion** - `3.5.9`<br/> **Schnittstellenversion** - `2017-09-21`

-   Der Service {{site.data.keyword.toneanalyzershort}} verwendet nun am {{site.data.keyword.cloud}}-Standort Frankfurt (**eu-de**) die tokenbasierte Authentifizierung von Identity and Access Management (IAM). Alle neuen Serviceinstanzen, die Sie an diesem oder an einem anderen Standort erstellen, verwenden die IAM-Authentifizierung.
-   Der Service wurde auch in Bezug auf interne Änderungen und Verbesserungen aktualisiert.

## 18. November 2018
{: #November2018b}

**Serviceversion** - `3.5.4`<br/> **Schnittstellenversion** - `2017-09-21`

Der Service {{site.data.keyword.toneanalyzershort}} steht nun am {{site.data.keyword.cloud_notm}}-Standort London (**eu-gb**) zur Verfügung. Wie alle Standorte verwendet auch London die tokenbasierte IAM-Authentifizierung. Alle neuen Serviceinstanzen, die Sie an diesem Standort erstellen, verwenden die IAM-Authentifizierung.

## 7. November 2018
{: #November2018a}

**Serviceversion** - `3.5.4`<br/> **Schnittstellenversion** - `2017-09-21`

Der Service {{site.data.keyword.toneanalyzershort}} steht nun am {{site.data.keyword.cloud_notm}}-Standort Tokio (**jp-tok**) zur Verfügung. Wie alle Standorte verwendet auch Tokio die tokenbasierte IAM-Authentifizierung. Alle neuen Serviceinstanzen, die Sie an diesem Standort erstellen, verwenden die IAM-Authentifizierung.

## Ältere Releases
{: #rnor}

  - [30. Oktober 2018](#30-october-2018)
  - [11. Juni 2018](#11-june-2018)
  - [25. Mai 2018](#25-may-2018)
  - [13. März 2018](#13-march-2018)
  - [28. September 2017](#28-september-2017)
  - [25. September 2017](#25-september-2017)
  - [6. Juli 2017](#6-july-2017)
  - [1. Juli 2017](#1-july-2017)
  - [8. Mai 2017](#8-may-2017)
  - [17. April 2017](#17-april-2017)
  - [15. März 2017](#15-march-2017)
  - [1. Dezember 2016](#1-december-2016)
  - [18. Oktober 2016](#18-october-2016)
  - [3. Oktober 2016](#3-october-2016)
  - [19. Mai 2016](#19-may-2016)

### 30. Oktober 2018
{: #October2018}

**Serviceversion** - `3.5.4`<br/> **Schnittstellenversion** - `2017-09-21`

Der Service {{site.data.keyword.toneanalyzershort}} hat die Migration auf die tokenbasierte IAM-Authentifizierung für alle Standorte durchgeführt. Alle {{site.data.keyword.cloud_notm}}-Services verwenden nun die IAM-Authentifizierung. Der Service {{site.data.keyword.toneanalyzershort}} hat die Migration der Standorte an den folgenden Terminen durchgeführt:

-   Dallas (**us-south**): 30. Oktober 2018
-   Frankfurt (**eu-de**): Migration wird momentan ausgeführt
-   Washington, DC (**us-east**): 11. Juni 2018
-   Sydney (**au-syd**): 25. Mai 2018

Der Service verwendet zur Authentifizierung am Standort Frankfurt weiterhin die Cloud Foundry-Serviceberechtigungsnachweise. Dieser Standort wird in Kürze auf die IAM-Authentifizierung migriert.
{: important}

Die Migration auf die IAM-Authentifizierung wirkt sich auf neue und bereits vorhandene Serviceinstanzen unterschiedlich aus:

-   *Alle neuen Serviceinstanzen, die Sie an einem Standort erstellen*, verwenden nun für den Zugriff auf den Service die IAM-Authentifizierung. Dazu können Sie entweder ein Trägertoken oder einen API-Schlüssel übergeben. Die Tokens unterstützen authentifizierte Anforderungen, ohne dass die Serviceberechtigungsnachweise in jeden Aufruf eingebettet werden müssen. Die API-Schlüssel verwenden die HTTP-Basisauthentifizierung. Wenn Sie eines der {{site.data.keyword.watson}}-SDKs verwenden, dann können Sie den API-Schlüssel übergeben und den Lebenszyklus der Tokens über SDK verwalten.
-   *Bereits vorhandene Serviceinstanzen, die vor dem angegebenen Migrationsdatum an einem Standort erstellt wurden*, verwenden die Angaben für `{username}` und `{password}` aus den zuvor benutzten Cloud Foundry-Serviceberechtigungsnachweisen für die Authentifizierung, bis Sie die Aktualisierung zur Verwendung der IAM-Authentifizierung durchgeführt haben. Da der Service {{site.data.keyword.toneanalyzershort}} statusunabhängig arbeitet, können Sie die folgenden Schritte ausführen, um eine vorhandene Serviceinstanz auf die Verwendung der IAM-Authentifizierung umzustellen:

    1.  Löschen Sie die Serviceinstanz und erstellen Sie sie neu.
    1.  Ändern Sie Ihren Anwendungscode so, dass die IAM-Authentifizierung verwendet werden kann.

Weitere Informationen finden Sie in der folgenden Dokumentation:

-   Zum Abrufen der Informationen zu dem von Ihrer Serviceinstanz verwendeten Authentifizierungsmechanismus müssen Sie Ihre Serviceberechtigungsnachweise anzeigen. Klicken Sie hierzu im [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/dashboard/apps){: new_window} auf die gewünschte Instanz.
-   Weitere Informationen zur Verwendung von IAM-Tokens mit Watson-Services finden Sie im Abschnitt zur [Authentifizierung mit IAM-Tokens](/docs/services/watson?topic=watson-iam).
-   Weitere Informationen zur Verwendung von IAM-API-Schlüsseln mit Watson-Services finden Sie im Abschnitt zu den [API-Schlüsseln für den IAM-Service](/docs/services/watson?topic=watson-api-key-bp).
-   Beispiele zur IAM-Authentifizierung finden Sie in der [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/tone-analyzer){: new_window}.

### 11. Juni 2018
{: #June2018}

**Serviceversion** - `3.5.4`<br/> **Schnittstellenversion** - `2017-09-21`

Für Serviceinstanzen und Anwendungen, die in Washington, DC (**us east**) gehostet werden, unterstützt der Service nun einen neuen API-Authentifizierungsprozess. Weitere Informationen finden Sie in der [Serviceaktualisierung vom 30. Oktober 2018](#October2018).

### 25. Mai 2018
{: #May2018}

**Serviceversion** - `3.5.4`<br/> **Schnittstellenversion** - `2017-09-21`

Für Serviceinstanzen und Anwendungen, die in Sydney (**au-syd**) gehostet werden, unterstützt der Service nun einen neuen API-Authentifizierungsprozess. Weitere Informationen finden Sie in der [Serviceaktualisierung vom 30. Oktober 2018](#October2018).

### 13. März 2018
{: #March2018}

**Serviceversion** - `3.5.3`<br/> **Schnittstellenversion** - `2017-09-21`

Der Service wurde aktualisiert, um zusätzlich zu englischen Eingabeinhalten für den Endpunkt für das Kundenengagement (`/v3/tone_chat`) auch französische (`fr`) Eingabeinhalte hinzuzufügen. Mithilfe des Anforderungsheaders `Content-Language` können Sie eine Sprache angeben. Die Standardsprache ist amerikanisches Englisch.

### 28. September 2017
{: #September2017b}

**Serviceversion** - `3.4.1`<br/> **Schnittstellenversion** - `2017-09-21`

Der Regulierungsgrenzwert für die maximale Anzahl Anforderungen, die ein einzelner {{site.data.keyword.cloud_notm}}-Benutzername übergeben kann, ist auf 1.200 Anforderungen pro Minute gestiegen. Der Service gibt den HTTP-Antwortcode 429 *Too many requests* zurück, wenn ein Benutzer diesen Grenzwert überschreitet.

### 25. September 2017
{: #September2017a}

**Serviceversion** - `3.4.1`<br/> **Schnittstellenversion** - `2017-09-21`

-   Der Endpunkt für allgemeine Zwecke (Methode `/v3/tone`) wurde geändert.

    -   Er unterstützt neben Englisch nun Eingabeinhalt auf Französisch (`fr`).
    -   Er gibt keine sozialen Töne mehr zurück.
    -   Er gibt bei den emotionalen Tönen nicht mehr "Ekel" (`disgust`) zurück.
    -   Er lässt alle Töne mit einem Wert unter `0,5` weg. Diese Qualifizierung entspricht der Antwort der Methode `/v3/tone_chat`.
    - Er gibt bei seiner Ausgabe keine Tonkategorien (Feld `tone_categories`) mehr zurück. Alle Töne, deren Werte den qualifizierenden Schwellenwert erfüllen, werden als Teil eines einzigen Objekts namens `tones` zurückgegeben. Weiterhin werden Töne standardmäßig immer für das vollständige Dokument und für jeden einzelnen Satz zurückgegeben.
    - Er akzeptiert nicht mehr den Abfrageparameter `tones` zur Begrenzung der Ausgabe auf angegebene Töne. Alle qualifizierenden Töne werden bei jeder Anforderung zurückgegeben. Den Parameter in eine Anforderung einzuschließen, führt nicht zu einem Fehler, hat jedoch keine Auswirkung auf die Antwort.
    - Er gibt bei einzelnen Sätzen nicht mehr die Felder `input_from` und `input_to` zurück. Die Methode gibt neben den Ergebnissen ihrer Analyse jetzt nur eine ID und den Text der einzelnen Sätze zurück.

-   Der Service gibt jetzt bei teilweise korrekter Eingabe in den folgenden Fällen den HTTP-Antwortcode 200 statt 400 zurück:

    -   Wenn Sie bei der Methode `/v3/tone` einen Eingabeinhalt von mehr als 128 KB oder 1000 Sätzen übergeben, gibt der Service bei seiner Antwort ein Feld `warning` zurück. Der Service analysiert die ersten 1000 Sätze auf Dokumentebene. Nur die ersten 100 Sätze werden auf Satzebene analysiert. In älteren Versionen des Service wurde bei der Anforderung der Antwortcode 400 zurückgegeben, wenn einer der beiden Grenzwerte überschritten wurde. Darüber hinaus analysiert der Service jetzt auch Sätze mit weniger als drei Wörtern.
    -   Wenn Sie bei der Methode `/v3/tone_chat` mehr als 50 Äußerungen übergeben, gibt der Service auf der Ebene `warning` der Antwort ein Feld `warning` für den Gesamtinhalt zurück. Er analysiert nur die ersten 50 Äußerungen. Wenn Sie eine einzelne Äußerung übergeben, die mehr als 500 Zeichen enthält, gibt der Service ein Feld `error` für diese Äußerung zurück und analysiert sie nicht. In älteren Versionen des Service wurde der Antwortcode 400 zurückgegeben, wenn einer der beiden Grenzwerte überschritten wurde. Der Service gibt auch dann den Antwortcode 400 für die Anforderung zurück, wenn alle Äußerungen der Eingabe mehr als 500 Zeichen aufweisen.

-   Jetzt reguliert der Service die Anzahl der Anforderungen, die er von einem einzelnen Benutzer akzeptiert. Der Service gibt den HTTP-Antwortcode 429 *Too many requests* zurück, wenn mehr als 600 Anforderungen pro Minute von einem einzelnen {{site.data.keyword.cloud_notm}}-Benutzernamen empfangen werden.

-   Die folgenden Änderungen gelten sowohl für den Endpunkt für allgemeine Zwecke als auch für den Endpunkt für das Kundenengagement:

    -   Die mit dem Parameter `version` angegebene Schnittstellenversion ist `2017-09-21`, um die neueste Version des Service zu verwenden.
    -   Die Dokumentation wurde durch den Hinweis aktualisiert, dass der Service eine lokalisierte Ausgabe in verschiedenen Sprachen erzeugen kann. Verwenden Sie den Anforderungsheader `Accept-Language`, um die gewünschte Sprache anzugeben.

### 6. Juli 2017
{: #July2017b}

**Serviceversion** - `3.3.6`<br/> **Schnittstellenversion** - `2016-05-19`

Der Service wurde mit einer kleinen Fehlerkorrektur am Endpunkt für das Kundenengagement aktualisiert.

### 1. Juli 2017
{: #July2017a}

**Serviceversion** - `3.3.5`<br/> **Schnittstellenversion** - `2016-05-19`

Der Endpunkt für das Kundenengagement des Service {{site.data.keyword.toneanalyzershort}} ist jetzt allgemein verfügbar. Alle Aufrufe an den Endpunkt werden jetzt mit derselben Gebühr berechnet wie Aufrufe an den Endpunkt für allgemeine Zwecke.

### 8. Mai 2017
{: #May2017}

**Serviceversion** - `3.3.4`<br/> **Schnittstellenversion** - `2016-05-19`

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

-   Die Modelle des Service verwenden bei der Interpretation von Tönen eine verbesserte Sensitivität. Die Modelle verwenden jetzt mehr als nur lexikalische Einheiten. Sie berücksichtigen jetzt auch Merkmale für Interpunktion, Emoticons, Sprachparameter (z. B. die Satzstruktur) und die Satzkomplexität.
-   Das Modell für schriftliche Töne wurde in das Modell für Sprachtöne umbenannt.
-   Die Modelle für Sprach- und emotionale Töne können jetzt Negationen verarbeiten.
-   Der Service gibt keine Antwort auf Sätze mit weniger als drei Wörtern mehr zurück.
-   Der Service verfügt nun über eine einfachere und verbesserte [Demo ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://tone-analyzer-demo.ng.bluemix.net){: new_window}.
