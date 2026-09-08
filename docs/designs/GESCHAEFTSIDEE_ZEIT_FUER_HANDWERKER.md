# Geschäftsidee: Zeit für Handwerksbetriebe

**Eigenständiges Strategiepapier.** Enthält allen Kontext, den ein neuer Chat
braucht — nichts davon setzt ein früheres Gespräch voraus.

Stand: 8. September 2026 · Diagnostik nach `office-hours` (Startup-Modus),
teilweise durchlaufen · Autor der Idee: David Schermacher (Elektromeister,
WHE-Technik)

---

## 1. Die Idee in drei Sätzen

David baut für Handwerksbetriebe individuelle KI-gestützte Systeme, die den
Papierkram übernehmen: Baustellenaufnahme, Angebotskalkulation, Nachkalkulation,
Belegvorbereitung für den Steuerberater. Der erste Kunde ist ein befreundeter
Malermeister — gleichzeitig Versuchskaninchen und Referenz. Geschäftsmodell:
monatliche Gebühr pro betreutem Betrieb, langfristig als Kleingewerbe neben dem
eigentlichen Betrieb.

Technische Basis: Obsidian-Vault als Datenhaltung (Markdown mit strukturiertem
Frontmatter), Bedienung per Chat, mobile Erfassung auf der Baustelle. Der
technische Plan liegt separat in `docs/designs/HANDWERKER_SYSTEM_PLAN.md`.

---

## 2. Die Kernthese: verkauft wird Zeit

Davids eigene Formulierung, und sie ist der Kern des Ganzen:

> Ich verkaufe Lösungen, um mehr Zeit zu bekommen. Ein Mensch hat 24 Stunden am
> Tag, und als Selbstständiger geht das meiste davon ins Business. Wenn ich
> etwas finde, das meinem Kunden wertvolle Lebenszeit schenkt, dann zahlt er mir
> dafür.

Das ist die richtige Ebene — es beschreibt, was der Kunde *kauft*, nicht was der
Anbieter *besitzt*. Und es verschiebt die Preislogik von Kosten-plus-Aufschlag zu
wertbasiert.

### Wo die These eine Lücke hat

Zeit verkauft sich nur, wenn der Kunde weiß, was er mit ihr anfängt. Drei
mögliche Antworten mit drei völlig verschiedenen Zahlungsbereitschaften:

| Kunde macht mit der Zeit | Konsequenz für den Preis |
|---|---|
| Nimmt einen weiteren Auftrag an | Bestfall. Zeit wird bei ihm zu Umsatz, er zahlt aus der Betriebskasse und rechnet die Rendite selbst nach. Höchster Preis durchsetzbar. |
| Ist bei der Familie | Emotional hoch bewertet, aber er zahlt aus der **privaten** Tasche. Private Budgets sind deutlich enger als betriebliche — dieselbe Person zahlt 2.000 € für ein Betriebswerkzeug und feilscht um 30 € beim privaten. Braucht zwingend ein zusätzliches Geldargument. |
| Füllt sie mit anderer liegengebliebener Arbeit | Warnsignal. Er merkt keinen Gewinn und kündigt nach wenigen Monaten. |

### Die Übersetzung, die verkauft

Verlorene Zeit ist unsichtbar. Sonntags Angebote zu schreiben fühlt sich für
einen Selbstständigen nach Normalzustand an, nicht nach Verlust. Verlorenes Geld
ist sichtbar. Deshalb ist der schwache Satz *„ich schenke dir Zeit"* — und der
starke:

> „Du schickst das Angebot am Tag des Ortstermins raus statt zwei Wochen später.
> Wie viele Aufträge hast du letztes Jahr an den Schnelleren verloren?"

Diese Zahl kann der Kunde rechnen. Und er nennt damit selbst den Betrag, der als
Preisanker taugt.

**Preisformel:** verlorene Anfragen pro Jahr × Deckungsbeitrag je Auftrag =
entgangener Gewinn. Davon 10–20 % ist ein verteidigbarer Jahrespreis.

---

## 3. Der Vorsprung — und was keiner ist

**Der Vorsprung ist Vertrauen und Zugang.** Ein Handwerksmeister gibt seine
Angebote, Stundensätze, Schlussrechnungen und Belege niemandem — das sind seine
intimsten Betriebszahlen, aus denen hervorgeht, ob er gut kalkuliert oder sich
seit Jahren verschätzt. Er gibt sie einem anderen Meister, den er kennt. David
ist Elektromeister; er sitzt beim Kunden auf der richtigen Seite des Tisches.
Diesen Zugang kann kein Software-Anbieter kaufen und kein Vertriebler
nachbilden.

**Die Daten sind nachgelagert, nicht vorgelagert.** Die Erfahrungswerte, die
Soll/Ist-Vergleiche, die über die Zeit entstehende Datenbank — sie sind wertvoll,
aber sie sind die *Frucht* des Vertrauens, nicht die Wurzel. Ohne Vertrauen keine
Unterlagen, ohne Unterlagen keine Daten.

**Kein dauerhafter Vorsprung: KI-Affinität.** David nennt seine Fähigkeit, mit
KI zu arbeiten, als das, was ihn von anderen unterscheidet. Das ist heute wahr
und wird jedes Quartal weniger wahr — die Modelle werden gezielt darauf
optimiert, ohne Affinität bedienbar zu sein. Was heute Können ist, ist übermorgen
ein Knopf. Ein Geschäft, das auf *„ich bediene das besser als andere"* gebaut
ist, schmilzt. Die KI-Fähigkeit ist der **Hebel**, nicht das Gut.

**Zwei Konsequenzen daraus:**

1. **Vertrauen ist einmal ausgebbar.** Wenn das erste System beim Freund nach
   drei Wochen nervt, ist nicht ein Kunde verloren, sondern der Zugang zu dessen
   Netzwerk — und er war der, der weiterempfehlen sollte. Deshalb: lieber ein
   Baustein, der verlässlich läuft, als vier, die wackeln.
2. **Kein Freundschaftspreis.** Ein Gefallen wird nie ein Gewerbe, weil der
   Übergang zum echten Preis nicht mehr gelingt — der Kunde erinnert sich
   dauerhaft an die erste Zahl. Wenn geschenkt werden soll, dann die
   **Aufbauphase**, nie der laufende Preis: *„Aufbau mach ich umsonst, weil du
   der Erste bist. Ab dem Tag, wo es läuft, kostet es X."*

---

## 4. Die Architekturkonsequenz: Maschinerie vs. Stammdaten

Aus der Zeit-These folgt direkt eine Bauentscheidung, die das größte
Skalierungsproblem löst.

**Das Problem:** „individualisierte Systeme" klingt nach Einzelstücken. Zehn
Kunden à 250 € sind 2.500 € Umsatz im Monat und zehn verschiedene Systeme in der
Wartung. Das ist eine Beratungsleistung mit Produktpreis — die Rechnung geht
nicht auf.

**Die Auflösung:** Wenn das Produkt *Zeit* ist und nicht *Maler-Software*, dann
ist der Kern die **Maschinerie**, und die ist gewerkeunabhängig:

```
Aufnahme  →  Kalkulation  →  Nachkalkulation  →  Belege
        (identisch für jedes Gewerk)
```

Individuell sind nur die **Stammdaten**: Leistungspositionen, Aufwandswerte,
Materialpreise, Stundensätze, Formulierungen, Layout. Also Konfiguration, nicht
Code.

Wird es so gebaut, ist Kunde Nummer zwei ein Wochenende statt drei Monate — und
„individualisiert" und „skalierbar" sind kein Widerspruch mehr. Wird es *nicht*
so gebaut, wächst die Wartungslast linear mit der Kundenzahl und die Sache
erstickt bei Kunde fünf bis sieben.

**Das ist eine Entscheidung für Tag eins**, nicht für Kunde sieben. Nachträglich
eine gewachsene Einzellösung in Maschinerie plus Konfiguration zu trennen, ist
die teuerste Variante.

---

## 5. Beweislage — ehrlich

| Behauptung | Beleg | Bewertung |
|---|---|---|
| Der Malermeister will das System | Parkplatzgespräch, er war „sehr interessiert" | **Schwach.** Interesse, nicht Nachfrage. Er musste nichts riskieren. Freunde sagen fast nie nein — Zustimmung ist als Beweis nahezu wertlos. |
| „Er wird nicht der Einzige sein" | Vermutung aus Branchenkenntnis | **Unbelegt, aber billig testbar.** Drei Handwerksmeister aus dem eigenen Netzwerk fragen — kostet eine Woche, keinen Euro. |
| Ein Betrieb zahlt monatlich dafür | Keiner | **Offen.** Bisher wurde nie über Geld gesprochen. |
| David kann es bauen | Vorhandenes eigenes Setup (Obsidian-Vault, Skills, Ninox) bei WHE-Technik, produktiv im Einsatz | **Stark.** Das Muster läuft bereits im eigenen Betrieb. |
| Zugang zur Zielgruppe | Eigener Meisterstatus, Netzwerk im Handwerk | **Stark.** Der eigentliche Vermögenswert. |

**Der zentrale Denkfehler, der ohne Gegenmaßnahme passiert:** Wird das System
kostenlos gebaut, läuft nur ein Experiment („funktioniert die Software?"). Über
das Geschäft („zahlt jemand?") wird nichts gelernt — obwohl beide Experimente für
fast denselben Aufwand zu haben sind, sobald über Geld gesprochen wird.

---

## 6. Offene Fragen aus der Diagnostik

Die `office-hours`-Diagnostik ist bis Frage 1 gelaufen. Diese Punkte sind offen
und werden durch das Kundengespräch beantwortet, nicht durch Nachdenken:

1. **Status quo:** Was macht der Malermeister heute konkret? Zettel, Excel, Word
   oder Handwerkersoftware? Wie lange sitzt er an einem Angebot, und wann? Hat er
   eine Bürokraft? — Der echte Wettbewerber ist nicht Streit oder pds, sondern
   sein Zettel und sein Excel: kostenlos, funktionierend, seit fünfzehn Jahren
   vertraut.
2. **Kosten des Status quo:** Wie viele Anfragen im Jahr, wie viele davon
   unbeantwortet oder zu spät, welcher Deckungsbeitrag je Auftrag? Das ist der
   Preisanker.
3. **Zukunftsfähigkeit:** Wenn generische KI-Assistenten in drei Jahren viel mehr
   können — wird dieses Angebot dann wertvoller oder überflüssig? Die
   belastbare Antwort kann nicht „KI wird besser, also werde ich besser sein"
   lauten; das kann jeder Wettbewerber behaupten. Die tragfähige Version lautet
   vermutlich: *die Stammdaten und die Erfahrungswerte des Betriebs sind der
   Bestand, und der wächst nur bei dem, der ihn seit Jahren pflegt.*

---

## 7. Nächste Schritte

**Diese Woche, vor der ersten Zeile Code:**

1. **Das halbstündige Gespräch mit dem Malermeister.** Leitfaden liegt vor
   (`docs/designs/leitfaden.html` → PDF). Ziel: Zahlen, keine Meinungen. Regel:
   nichts verkaufen und das System nicht vorführen, solange gefragt wird —
   sonst beschreibt er das Produkt statt seinen Alltag.
2. **Drei weitere Handwerksmeister fragen**, mit demselben Bogen. Nicht „würdest
   du sowas nutzen" (Parkplatzreden), sondern „was machst du sonntags" und „wie
   viele Anfragen hast du letztes Jahr nicht beantwortet".
3. **Das Geldgespräch führen**, mit dem Aufbau-geschenkt-Modell. Und danach auf
   das Verhalten achten, nicht auf die Worte: Rückfragen zu Abrechnung, Beginn
   oder Kündigung heißen, er rechnet. Ein schnelles „ja, passt" mit Themenwechsel
   heißt, es ist noch ein Gefallen.

**Danach:**

4. Phase 1 bauen (Vault-Fundament + Baustellenaufnahme) — aber von Anfang an
   getrennt in Maschinerie und Stammdaten.
5. Die Diagnostik mit den echten Antworten fortsetzen.

---

## 8. Risiken

**Support-Last.** Läuft es, klingelt bei jedem Problem Davids Telefon. Bei
mehreren Kunden wird das der begrenzende Faktor, nicht die Entwicklungszeit.
Alles, was nur mit Davids Anwesenheit funktioniert, ist nicht fertig. Vorab
klären, wie viel Betreuung im Preis enthalten ist.

**Adoption, nicht Technik.** Solche Systeme sterben nicht an einem Fehler,
sondern daran, dass der Handwerker nach drei Wochen wieder den Zettel nimmt.
Gegenmittel ist im Design verbaut (Zettel fotografieren statt Formular
ausfüllen, diktieren statt tippen). Jede Funktion muss die Frage überstehen:
*macht das seinen Abend kürzer oder länger?*

**Stammdaten.** Ohne die echten Aufwandswerte des Betriebs rechnet das System
mit Durchschnittswerten. Ein Angebot, das 30 % zu niedrig ist, sieht genauso
professionell aus wie ein richtiges — und kostet echtes Geld. Deshalb ist die
Gegenprobe an drei alten Projekten Pflicht, bevor ein echtes Angebot rausgeht.

**Rechtliches.** Ein Markdown-Vault ist keine GoBD-konforme, revisionssichere
Belegaufbewahrung. Er ist Arbeitsablage; das Archiv bleibt beim Steuerberater.
Rechnungsstellung aus dem System ist ein eigenes Projekt mit eigenem
Risikoprofil, nicht ein Feature nebenbei.

**Datenschutz.** Es sind echte Kundendaten. Für gewerbliche Verarbeitung braucht
es einen Auftragsverarbeitungsvertrag; zu prüfen ist außerdem, ob
Pseudonymisierung im Vault reicht (Projektnummer statt Klarname), damit
Klardaten den Rechner nie verlassen. Vor Phase 1 zu klären, nicht danach.

---

## 9. Übergabe an einen neuen Chat

Zum Weiterarbeiten reicht dieses Dokument. Der sinnvolle nächste Auftrag lautet:

> Ich habe das Kundengespräch geführt. Hier sind die Antworten: [...]. Setz die
> office-hours-Diagnostik fort — Status quo, Kosten des Status quo,
> Zukunftsfähigkeit — und leite daraus einen Preis und einen Zuschnitt der ersten
> Version ab.

Falls das Gespräch noch nicht stattgefunden hat, ist jede weitere
Strategiearbeit Spekulation. Dann ist der einzige sinnvolle nächste Schritt das
Gespräch selbst.
