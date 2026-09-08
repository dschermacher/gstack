# Handwerker-System (Malerbetrieb) — Schlachtplan

Status: Entwurf zur Abstimmung. Noch keine Implementierung.
Zielnutzer: Malermeister mit eigener Firma (Freund des Auftraggebers).
Operator: David (baut und betreut das System).

---

## 1. Was das System leisten soll

Der Malermeister verdient sein Geld mit Malen. Alles drumherum kostet ihn Zeit
und Aufträge:

- **Angebote kalkulieren** dauert zu lang, also bleiben Anfragen liegen und
  Kunden gehen zum Nächsten.
- **Belege und Buchhaltung** sammeln sich bis zur Mahnung vom Steuerberater.
- **Baustellenaufnahmen** leben auf einem Zettel oder im Kopf. Was beim
  Ortstermin besprochen wurde, ist zwei Wochen später unscharf.

Das System soll diese drei Ströme in einem Ort zusammenführen — seinem
Obsidian-Vault auf dem eigenen Rechner — und dabei aus seinen eigenen Daten
lernen.

### Der eigentliche Hebel: Rückkopplung

Eine Ablage, die nur sammelt, bringt ihm nichts. Der Wert entsteht, wenn
**Aufnahme (Soll)** und **Nachkalkulation (Ist)** in derselben Datei verknüpft
sind. Dann kann das System nach 20 Projekten sagen: "Treppenhaus mit
Altanstrich — beim letzten Mal 1,8-mal so lange wie kalkuliert." Ohne diese
Rückkopplung ist es ein hübscher Aktenschrank.

Deshalb ist die Baustellenaufnahme der richtige Start: sie ist der Eingang,
an dem die Datenqualität entsteht, auf der alles andere aufsetzt.

---

## 2. Getroffene Entscheidungen

| Frage | Entscheidung | Konsequenz |
|---|---|---|
| Wo liegt die Wahrheit der Daten? | **Obsidian pur** — Markdown mit Frontmatter ist die Datenbank | Kein Server, kein Abo, keine Migration. Er besitzt seine Daten vollständig. Preispflege bei vielen hundert Positionen wird später zäh — dann ist Phase 5 der Ort dafür. |
| Wie bedient er es? | **Chat in Claude Desktop** + **Handy zuerst auf der Baustelle** | Keine Terminal-Anforderung an ihn. Braucht saubere Skills, damit er nicht frei formulieren muss. Braucht einen Sync-Pfad Handy → Rechner. |
| Wie weit geht die Buchhaltung? | **An bestehende Software andocken** | Kein Rechnungsausgang aus dem System, keine GoBD-Last bei uns. Erfordert Abstimmung mit dem Steuerberater. |
| Womit fangen wir an? | **Baustellenaufnahme** | Nutzen zeigt sich verzögert, aber die Datenbasis ist von Tag eins sauber. |

---

## 3. Die Struktur im Vault

Ein Vorschlag, kein Gesetz — die Nummern-Präfixe halten die Sortierung stabil.

```
Malerbetrieb/
├── 00 Inbox/                 alles Rohe: Fotos, Diktate, Zettel-Fotos
├── 01 Kunden/
│   └── Müller, Anna.md       Kontakt, Adresse, Projekthistorie
├── 02 Projekte/
│   └── P-2026-018 Müller Wohnung/
│       ├── Projekt.md        Status, Kunde, Objekt, Verknüpfungen
│       ├── Aufnahme.md       ← das Herzstück
│       ├── Angebot-01.md
│       ├── Nachkalkulation.md
│       ├── Fotos/
│       └── Belege/
├── 03 Stammdaten/
│   ├── Leistungen/           je Leistungsposition eine Datei
│   ├── Material/             je Artikel eine Datei
│   └── Kalkulationsbasis.md  Stundensätze, Zuschläge, Fahrtkosten
├── 04 Buchhaltung/
│   └── 2026/03/              Belege nach Namensschema + Monatspaket.md
├── 05 Erfahrungswerte/       was die KI gelernt hat (Soll/Ist je Leistungsart)
└── 99 Vorlagen/
```

Jede Datei trägt strukturiertes Frontmatter (`kunde:`, `status:`, `flaeche_m2:`,
`aufwand_soll_h:`, `aufwand_ist_h:` …). Das macht Markdown auswertbar, ohne
eine Datenbank zu brauchen — Obsidians Dataview kann daraus Listen und
Auswertungen rendern, und die KI kann die Felder lesen und schreiben.

---

## 4. Der Aufnahme-Flow — der wichtigste Teil

Die Wahrheit über Handwerker-Software: **ein System, das auf der Baustelle
Tipparbeit verlangt, wird nicht benutzt.** Er steht auf einer Leiter, hat Farbe
an den Händen und einen Kunden neben sich. Deshalb ist der Flow so gebaut, dass
er sein Verhalten kaum ändern muss:

**Auf der Baustelle (2 Minuten, ohne Bildschirm-Arbeit):**

1. **Er schreibt weiter auf seinen Zettel, wie immer** — und fotografiert ihn.
   Claude kann Bilder lesen und handschriftliche Aufmaße digitalisieren.
   Das ist der Trick, der so ein System überhaupt überleben lässt: kein
   Verhaltenswandel.
2. Fotos von den Räumen, Schäden, Untergründen — per Teilen-Menü in den Vault.
3. Was man nicht sieht, spricht er ein: Kundenwünsche, Zugang, Besonderheiten.

**Zur Sprachaufnahme ein technischer Vorbehalt, der den Plan mitbestimmt:**
Claude kann Audiodateien nicht direkt lesen — nur Text, Bilder und PDFs. Ein
Diktat als `.m4a` im Vault ist für die KI also zunächst stumm. Drei Wege:

- **Phase 1 (empfohlen):** Er nutzt die **Diktierfunktion der Handytastatur**
  direkt in einer Obsidian-Notiz. Spricht, es steht als Text da. Kostet nichts,
  läuft sofort, kein Zusatzwerkzeug.
- **Phase 5 (Ausbau):** Lokales Whisper-Skript, das Audio aus `00 Inbox/`
  automatisch in Text verwandelt. Dann kann er frei sprechen, ohne aufs Display
  zu schauen. Mehr Bau, deutlich besser im Alltag.
- **Zwischenlösung:** Diktier-Apps mit eingebauter Transkription (iOS
  Sprachmemos, Google Recorder) — Text herauskopieren.

**Abends am Rechner (5 Minuten):**

Er sagt in Claude Desktop: *"Aufnahme Müller verarbeiten."* Ein Skill
`baustellenaufnahme` liest Inbox-Fotos und Diktattext, füllt das
Aufnahme-Schema, legt Kunde und Projekt an — und **fragt gezielt nur nach dem,
was für die Kalkulation wirklich fehlt.** Nicht nach allem. Nur nach den drei
Dingen, ohne die der Preis Raten wäre.

---

## 5. Phasenplan

### Phase 0 — Vorbereitung (kein Code)

Interview mit dem Freund, Stammdaten einsammeln, Accounts und Hardware klären.
Die Checkliste steht in Abschnitt 7. **Ohne Phase 0 kalkuliert das System
Fantasiezahlen** — und das ist am gefährlichsten, wenn sie plausibel aussehen.

### Phase 1 — Vault-Fundament + Baustellenaufnahme (das MVP)

- Vault-Struktur, Frontmatter-Schema, Vorlagen
- Sync-Pfad Handy → Rechner einrichten und testen
- Skill `baustellenaufnahme`: Fotos + Diktat → strukturierte Aufnahme
- Obsidian auf seinem Rechner installieren und einrichten

**Abnahmekriterium:** Er macht drei echte Aufnahmen ohne deine Hilfe, und die
Ergebnisse sind gut genug, um daraus zu kalkulieren.

### Phase 2 — Kalkulation

- Stammdaten als Dateien: Leistungspositionen mit Aufwandswerten (Minuten/m²)
  und Materialverbrauch (Liter/m²), Kalkulationsbasis mit Stundensätzen
- Skill `angebot-kalkulieren`: Aufnahme → Positionen → Preis
- Ausgabe als Angebots-PDF in seinem Layout und seinen Formulierungen

**Abnahmekriterium:** Ein Angebot, das er ohne Nacharbeit an einen Kunden
schicken würde. Gegenprobe: wir kalkulieren drei alte Projekte nachträglich und
vergleichen mit dem, was er damals wirklich angeboten hat.

### Phase 3 — Nachkalkulation und Lernen

- Ist-Stunden und Ist-Material je Projekt erfassen (möglichst beiläufig)
- Soll/Ist-Vergleich, der in `05 Erfahrungswerte/` zurückfließt
- Die Kalkulation aus Phase 2 liest diese Erfahrungswerte

Hier entsteht der Wert, der ihn an das System bindet.

### Phase 4 — Buchhaltung andocken

- Belege-Flow: fotografieren → Inbox → KI liest Betrag, Datum, Lieferant,
  benennt nach Schema, ordnet dem Projekt zu
- Monatspaket für den Steuerberater in dessen Format

**Rechtlicher Rahmen, klar benennen:** Der Obsidian-Vault ist die
**Arbeitsablage**, nicht das Steuerarchiv. Die GoBD verlangt unveränderbare,
revisionssichere Aufbewahrung — das leistet ein Ordner mit Markdown-Dateien
nicht. Das revisionssichere Archiv bleibt beim Steuerberater bzw. in seiner
Buchhaltungssoftware. Wir liefern sauber strukturierte Daten dorthin und
ersetzen sie nicht.

### Phase 5 — Ausbau

Whisper-Transkription, Auswertungen (Auftragsquote, Deckungsbeiträge),
automatisches Nachfassen bei offenen Angeboten, ggf. echte Datenbank für die
Preispflege, wenn die Stammdaten aus Markdown herauswachsen.

---

## 6. Aufwand

Beide Spalten, damit die Erwartung stimmt:

| Phase | Klassisches Team | CC + gstack | Faktor |
|---|---|---|---|
| Phase 0 Vorbereitung | 2 Tage | 2 Tage | 1x (Menschenarbeit, nicht komprimierbar) |
| Phase 1 Fundament + Aufnahme | 1 Woche | ~1 Tag | ~5x |
| Phase 2 Kalkulation | 2 Wochen | ~2 Tage | ~5x |
| Phase 3 Nachkalkulation | 1 Woche | ~4 Stunden | ~10x |
| Phase 4 Buchhaltung | 1 Woche | ~1 Tag | ~5x |

Die Kompression ist hier bewusst niedriger angesetzt als bei reiner
Code-Arbeit: der Engpass ist nicht das Schreiben von Software, sondern das
Herausarbeiten seines Fachwissens und das Testen im echten Betrieb.

---

## 7. Vorbereitungen — was du von ihm brauchst

Das ist der Teil, den ich nicht erfinden kann. Ohne diese Dinge wird das
System hübsch und falsch.

**Unterlagen:**

1. **3–5 alte Angebote** als PDF oder Word — gewonnene *und* verlorene. Daraus
   lesen wir sein Leistungsverzeichnis, seine Formulierungen, sein Preisniveau.
   Die verlorenen sind besonders wertvoll.
2. **2–3 Schlussrechnungen** zu Projekten, bei denen er noch weiß, wie lange es
   wirklich gedauert hat. Das kalibriert die Aufwandswerte.
3. **Fotos von 2–3 seiner handschriftlichen Aufmaßzettel** — genau so, wie er
   sie wirklich schreibt, nicht schön abgeschrieben. Danach richtet sich, was
   die KI später lesen können muss.

**Zahlen:**

4. Stundenverrechnungssatz (Meister / Geselle / Azubi), Materialaufschlag,
   Fahrtkosten-Regelung, Zuschläge (Arbeiten über Kopf, Gerüst, Wochenende).
5. Betriebsgröße und Steuerstatus: allein oder mit Gesellen? Umsatzsteuer-
   pflichtig oder Kleinunternehmer? Rechtsform?

**Umfeld:**

6. **Steuerberater:** Welches System (Datev Unternehmen online, sevdesk,
   Lexoffice, …)? Wie gibt er Belege heute ab? Ein kurzes Gespräch mit dem
   Steuerberater erspart uns später eine Umbauphase.
7. **Hardware:** Rechner Mac oder Windows? Handy iOS oder Android? Läuft schon
   eine Cloud (iCloud, Dropbox, Google Drive)?
8. **Accounts:** Welches Claude-Abo? Obsidian Sync (ca. 8 $/Monat) oder Sync
   über bestehende Cloud?

**Und das Wichtigste — ein Gespräch:**

9. **30–45 Minuten mit ihm, offen:** Wo geht die Zeit hin? Was liegt liegen?
   Welche Anfrage hat er letzte Woche nicht beantwortet und warum? Was würde er
   als Erstes loswerden wollen? Nicht fragen, welche Features er will —
   fragen, wo es weh tut.

---

## 8. Datenschutz, offen angesprochen

Kundendaten — Namen, Adressen, Objektfotos — gehen bei der Nutzung von Claude
Desktop an einen Dienstleister in den USA. Das ist kein Ausschlussgrund, aber
eine bewusste Entscheidung, die er treffen muss, nicht wir für ihn:

- Für gewerbliche Verarbeitung personenbezogener Daten braucht er einen
  Auftragsverarbeitungsvertrag. Den bietet Anthropic für die Business-Tarife
  an, für private Consumer-Accounts ist die Lage schwächer.
- Prüfen: reichen Pseudonyme im Vault (Projektnummer statt Klarname), sodass
  Klardaten die KI nie erreichen? Bei einem Malerbetrieb ist das machbar.

Vor Phase 1 zu klären, nicht danach.

---

## 9. Die drei echten Risiken

**1. Adoption, nicht Technik.** Das häufigste Ende solcher Systeme ist nicht
ein Bug, sondern ein Handwerker, der nach drei Wochen wieder den Zettel nimmt.
Gegenmittel ist im Design verbaut: Foto vom Zettel statt Formular, Diktat statt
Tippen, die KI macht die Fleißarbeit. Jede Funktion muss die Frage überstehen:
*macht das seinen Abend kürzer oder länger?*

**2. Du wirst der Support.** Wenn es läuft, ruft er dich an, wenn es nicht
läuft. Klärt vorher, was du tragen willst — und baut lieber weniger, dafür
robuster. Alles, was nur mit deiner Anwesenheit funktioniert, ist noch nicht
fertig.

**3. Stammdaten.** Ohne seine echten Aufwandswerte rechnet das System mit
Durchschnittswerten aus dem Internet. Ein Angebot, das 30 % zu niedrig ist,
sieht genauso professionell aus wie ein richtiges — und kostet ihn echtes Geld.
Deshalb die Gegenprobe in Phase 2: drei alte Projekte nachrechnen, bevor ein
einziges neues Angebot herausgeht.

---

## 10. Nächster Schritt

Antworten auf Abschnitt 7 — mindestens Punkte 1, 4, 6 und 7. Dann baue ich
Phase 1: Vault-Struktur, Aufnahme-Schema, Vorlagen und den
Baustellenaufnahme-Skill.
