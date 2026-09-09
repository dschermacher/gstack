# Bausteine — was das System später können soll

Ideensammlung, kein Bauplan. Hält fest, was noch nicht gebaut wird, damit die
Entscheidungen von heute es nicht verbauen.

Gehört zu `GESCHAEFTSIDEE_ZEIT_FUER_HANDWERKER.md` (Strategie) und
`HANDWERKER_SYSTEM_PLAN.md` (technischer Plan).

---

## 1. Der Ausgangsgedanke

Der Chef eines kleinen Handwerksbetriebs macht fast alles selbst — kalkulieren,
schreiben, abrechnen, und eben auch Kunden gewinnen. Genau dort sitzt ein
Baustein, den bisher niemand für ihn übernimmt: **im Hintergrund nach Anfragen
schauen und sichtbar bleiben.** Portale wie MyHammer werfen laufend Anfragen aus;
wer zuerst und ordentlich antwortet, bekommt den Auftrag. Ein Meister auf der
Leiter schaut da nicht rein.

Davids Formulierung: das Ganze soll mit verschiedenen Bausteinen ausbaubar sein.

---

## 2. Widerspruch zur Einordnung: das ist keine Randnotiz

Kundengewinnung wurde als Zukunftsidee notiert. Sie ist wahrscheinlich der
**stärkere Verkauf** als Zeitsparen, aus einem Grund, der schon in der
Strategie steht:

Zeit sparen zahlt der Kunde nur dann gut, wenn er die gewonnene Zeit in einen
weiteren Auftrag umsetzt — sonst zahlt er aus der privaten Tasche, und die ist
eng. **Kundengewinnung überspringt diesen Umweg.** Sie liefert direkt das, was
Zeitsparen erst über zwei Ecken liefert: mehr Aufträge. Die Rendite ist trivial
zu rechnen (ein gewonnener Auftrag deckt viele Monate Gebühr), und sie wird
selbstverständlich aus der Betriebskasse bezahlt.

Es bleibt trotzdem nicht der erste Baustein — aber aus einem anderen Grund als
"zu groß": weil das Risiko dort am höchsten ist, siehe Abschnitt 4.

---

## 3. Die Bausteine, entlang der Wertschöpfung

Die Reihenfolge ist echt: jeder Baustein füttert den nächsten mit Daten.

| # | Baustein | Was er tut | Stand |
|---|---|---|---|
| 1 | **Anfragen-Mappe** | Quellen sichten, passende Anfragen vorlegen: Volumen aus eigenen Preisen, Kriterien, Antwortentwurf. Recherche abnehmen, Entscheidung nicht. | Idee — spezifiziert |
| 2 | **Aufnahme** | Baustelle einmal erfassen: Zettelfoto, Bilder, Diktat → strukturierte Aufnahme. | in Arbeit (Phase 1) |
| 3 | **Angebot** | Aus der Aufnahme kalkulieren, Angebots-PDF in seinem Layout. | geplant (Phase 2) |
| 4 | **Nachfassen** | Angebote ohne Antwort nach 5 und 14 Tagen erinnern, mit fertigem Text. | Idee — siehe unten |
| 5 | **Nachkalkulation** | Soll gegen Ist, Erfahrungswerte zurück in die Kalkulation. | geplant (Phase 3) |
| 6 | **Belege** | Belege lesen, zuordnen, Monatspaket für den Steuerberater. | geplant (Phase 4) |
| 7 | **Betriebsspiegel** | Auftragsquote, welche Leistung trägt, welcher Kundentyp zahlt pünktlich. | Idee |
| 8 | **Ausführung** | Termine, Material, Mitarbeiterplanung. | bewusst offen — eigenes Projekt |

### Baustein 4 ist der unterschätzte

Nachfassen ist der billigste Umsatz, den es gibt, und praktisch kein Handwerker
macht es. Sobald Baustein 3 steht, liegt das Angebot samt Datum und Kunde schon
im System — der Zusatzaufwand ist ein Zeitstempel und ein Textentwurf. Kein
Portal, keine Schnittstelle, kein Rechtsthema.

Wenn ein einziges nachgefasstes Angebot pro Quartal zum Auftrag wird, hat das
System sich bezahlt. **Das ist der Baustein, den ich vor Baustein 1 bauen würde**
— gleiche Wirkungsrichtung (mehr Aufträge), ein Bruchteil des Risikos.

---

## 4. Baustein 1 im Detail: die Anfragen-Mappe

### Der Auftrag an den Baustein

Der Bot **recherchiert und legt vor, er handelt nicht.** Er kennt das Profil des
Betriebs (Gewerk, Umkreis, Zielauftragsgröße, was er nicht machen will), sichtet
die Quellen und liefert eine Auflistung: worum es geht, geschätztes Volumen, was
dafür und was dagegen spricht, was noch fehlt — plus einen fertigen
Antwortentwurf. Der Meister überfliegt, wählt aus, drückt ab. Die Recherchearbeit
ist ihm abgenommen, die Entscheidung nicht.

Praktische Form: eine **Morgenmappe.** Eine Liste, sortiert nach erwartetem Wert,
kurz genug für einen Kaffee.

### Was in eine Zeile gehört

| Feld | Inhalt |
|---|---|
| Worum es geht | Zwei Sätze, aus der Anfrage destilliert — nicht der Originaltext |
| Quelle und Alter | Woher, und wie lange sie schon offen ist (alt = viele Mitbewerber) |
| Geschätztes Volumen | Grobe Spanne, gerechnet **mit seinen eigenen Preisen** |
| Dafür / Dagegen | Die Kriterien im Klartext, jedes einzeln nachprüfbar |
| Was fehlt | Was er beim ersten Anruf fragen muss, damit er kalkulieren kann |
| Antwortentwurf | In seiner Sprache, auf die genannten Details eingehend |

Das geschätzte Volumen ist der Punkt, an dem dieses System jedem generischen
Werkzeug überlegen ist: sobald Baustein 3 steht, liegen seine Aufwandswerte und
Preise im Vault. Aus „Wohnung, 80 m², streichen und Decken" wird dann eine Spanne
aus *seiner* Kalkulation, nicht aus einer Branchentabelle. Bausteine, die
aufeinander aufbauen, statt nebeneinanderher zu laufen.

### Die Prozentzahl — hier liegt die Falle

Eine Zuschlagswahrscheinlichkeit als Prozentwert war Teil der Idee. Genau die
sollte am Anfang **nicht** ausgegeben werden.

Eine frei geschätzte Zahl wirkt autoritativ, ohne es zu sein. „73 % Chance" liest
sich wie Statistik, ist aber ein Sprachmodell, das eine plausibel klingende Zahl
formt — und der Meister richtet seine Entscheidung danach aus. Das ist derselbe
Fehler wie ein Angebot mit Durchschnittswerten aus dem Internet: es sieht
professionell aus und ist falsch.

Der saubere Weg, in zwei Stufen:

1. **Am Anfang: nachprüfbare Kriterien statt Note.** Umkreis, Gewerk-Treffer,
   Auftragsgröße im Zielband, Alter der Anfrage, Zahl der Mitbewerber (falls das
   Portal sie zeigt), wie konkret die Beschreibung ist. Als sichtbare Liste, die
   er selbst gegenlesen kann. Er kalibriert im Kopf, und das kann er besser als
   jedes Modell — er ist Meister.
2. **Später: seine echte Quote.** Wenn zu jeder Anfrage festgehalten ist, ob er
   angeboten und ob er gewonnen hat, entsteht nach dreißig bis fünfzig Vorgängen
   eine belastbare Zuschlagsquote je Kategorie. **Dann** darf eine Zahl dran, und
   dann ist sie seine eigene.

Das ist dieselbe Regel wie bei der Kalkulation, nur auf Anfragen angewandt:
erst messen, dann schätzen. Und sie erklärt, warum Baustein 1 vom Anfang an
mitschreiben muss, was aus jeder Anfrage geworden ist — sonst lernt er nie.

### Wo die Minen liegen

**Automatisiert absenden — nicht.** Zwei harte Gründe:

1. **Plattform-Regeln.** Portale untersagen automatisierten Zugriff und Scraping
   in ihren Nutzungsbedingungen üblicherweise. Fliegt der Account, ist nicht
   Davids Werkzeug weg, sondern der Vertriebskanal seines Kunden. Vor dem Bau die
   AGB des konkreten Portals lesen und prüfen, ob eine offizielle Schnittstelle
   existiert — die ist immer der richtige Weg, auch wenn sie weniger kann. Reines
   Vorlegen ohne Absenden entschärft das nicht automatisch: schon das
   maschinelle Auslesen kann untersagt sein.
2. **Schlechte Aufträge.** Wer auf alles bietet, gewinnt vor allem das, was
   andere liegen lassen. Die Auswahl ist der Wert, nicht die Geschwindigkeit.

**Fremde personenbezogene Daten.** In Anfragen stehen Namen und Adressen von
Leuten, die mit dem Betrieb noch in keiner Beziehung stehen. Also: nur speichern,
was für die Entscheidung nötig ist, und löschen, was nicht weiterverfolgt wird.
Kein Sammelarchiv aus Verlegenheit.

### Korrektur zum Kanal

LinkedIn ist für einen Malermeister der falsche Ort, jedenfalls im
Privatkundengeschäft — dort sitzen keine Hausbesitzer. Realistisch nach Wert:

1. **Google-Unternehmensprofil und Bewertungen.** Für Handwerk der Kanal Nummer
   eins. Wer bei „Maler + Ort" oben mit vierzig guten Bewertungen steht, braucht
   keine Portale. Ein Baustein, der nach jedem abgeschlossenen Auftrag um eine
   Bewertung bittet, ist billig zu bauen und wirkt jahrelang.
2. **Empfehlung.** Läuft ohne Technik, lässt sich aber unterstützen: wer hat
   empfohlen, und wurde sich bedankt.
3. **Portale** wie MyHammer. Funktionieren, kosten Marge und liefern
   preissensible Kundschaft.
4. **LinkedIn** — nur B2B: Hausverwaltungen, Bauträger, Architekten. Größere,
   wiederkehrende Aufträge, eigener Weg, nicht derselbe wie MyHammer.

## 5. Was ein Baustein erfüllen muss

Damit "ausbaubar" nicht zu "gewachsen" wird, drei Bedingungen:

1. **Einzeln verkaufbar.** Ein Baustein, der nur im Verbund Sinn ergibt, ist
   kein Baustein, sondern ein halbes Produkt. Jeder muss allein einen
   nachvollziehbaren Nutzen haben.
2. **Auf der gemeinsamen Maschinerie.** Er liest und schreibt in denselben Vault
   mit demselben Schema. Was betriebsspezifisch ist, sind Stammdaten, nicht
   Code. Sonst kippt die Skalierbarkeit, die in der Strategie festgehalten ist.
3. **Abschaltbar.** Ein Kunde, der Baustein 1 nicht will, bekommt ihn nicht —
   ohne dass etwas anderes dadurch kaputtgeht.

Praktische Folge für Phase 1: Kunden, Projekte und Angebote brauchen von Anfang
an **stabile Kennungen und Statusfelder** im Frontmatter (`status:`,
`angebot_versendet_am:`, `quelle:`). Nachfassen und Betriebsspiegel entstehen
später fast von allein, wenn diese Felder ab Tag eins gepflegt sind — und sind
teuer, wenn sie nachgerüstet werden müssen.

---

## 6. Nächster Schritt

Nichts davon vor dem Kundengespräch. Aber eine Frage lohnt sich dort zusätzlich:

> **Wie kommen deine Kunden heute zu dir?** Empfehlung, Google, Portale,
> Stammkunden, Hausverwaltungen? Und: hast du schon mal über MyHammer
> gearbeitet — was war das Ergebnis?

Die Antwort entscheidet, ob Baustein 1 später überhaupt der richtige ist oder ob
es die Bewertungen sind.
