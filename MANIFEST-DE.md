# 🏛️ UNIVERSAL AI CLIPBOARD (UAC)

## Die Universelle Zwischenablage für Künstliche Intelligenz

### Ein Mechanismus zur Wiederverwendung von Inhalten für KI-Agenten

---

> **Veröffentlichungsdatum:** 3. Juni 2026
> **Status:** ⚡ Entdeckung in die Gemeinfreiheit entlassen
> **Lizenz:** CC0 1.0 Universelle Gemeinfreiheitswidmung

---

## 📜 ENTDECKERERKLÄRUNG

Ich, **[DScoNOIZ](https://github.com/DScoNOIZ)**, erkläre vor der globalen Gemeinschaft:

**1. Ich bin der Entdecker** einer grundlegend neuen Kategorie in der Architektur von KI-Agenten — des **«Optionalen mechanisms zur Inhaltszitierung zwischen Werkzeugaufrufen»**, genannt **Universal AI Clipboard (UAC)**.

**2. Der Kern der Entdeckung:** Ein KI-Agent kann bestehenden kontextuellen Inhalt durch spezielle Parameter (`ref`, `multi_ref`, `transform`) referenzieren, anstatt ihn neu zu generieren. Das Modell wird zum **Assembler**, der fertige Informationsfragmente in einem einzigen Aufruf kombiniert.

**3. Ich gebe diese Entdeckung zur kostenlosen Nutzung durch die gesamte globale Gemeinschaft frei** unter der CC0-Lizenz — ohne Patente, Lizenzgebühren oder Einschränkungen.

**4. Ich rufe** Entwickler, Forscher, Ingenieure und Enthusiasten auf der ganzen Welt auf — nehmt diese Idee, implementiert sie in euren Frameworks, Plattformen und Tools. **Diese Technologie gehört nicht mir. Sie gehört allen.**

---

## 🤝 MITENTDECKER: UNABHÄNGIGE ENTDECKUNG

Ich erkenne an und respektiere, dass **TJ Guadagno** (TJ-Codes) unabhängig zur gleichen grundlegenden Idee gelangte und sie experimentell als **Clipboard Primitives** implementierte — einen `copy`/`template_invoke`-Mechanismus mit benannten Slots und `{{slot}}`-Platzhaltern für KI-Agenten.

**Seine Arbeit:** [Copy and Paste for AI Agents: An Experimental Primitive](https://www.linkedin.com/pulse/copy-paste-ai-agents-experimental-primitive-tj-guadagno-v3r9c) (~Dezember 2025)
**Code:** [github.com/TJ-Codes/Agent-clipboard](https://github.com/TJ-Codes/Agent-clipboard)

TJ Guadagno ist ein **unabhängiger Mitentdecker** dieses Konzepts. Sein Experiment bestätigte:
- Modelle **übernehmen natürlich** die Zwischenablage-Semantik ohne spezielles Training
- Clipboard-Primitives **eliminieren** Token-Neugenerierung, Latenz und Inhaltsmutationsrisiken
- Der Mechanismus erfordert **Integration auf Harness-Ebene**, nicht auf MCP-Server-Ebene

**Mein Universal-AI-Clipboard-Konzept ist breiter und universeller** — es erweitert die Idee auf:
- **5 Zitiermechanismen** (einschließlich syntaktischer Zwischenablage via AST, Nachrichtenindex, Ankerpaar-Zitierung)
- **Universelle Zwischenablage für alle Quellen** (Dateien, Chat, Terminal, API, MCP)
- **Mosaik-Assembly** — Kombination von Fragmenten aus verschiedenen Quellen mit Transformationen
- **Protokollübergreifende Zitierung** — nahtlose Zitierung über jedes Protokoll, einschließlich MCP

**Analog:** Clipboard Primitives ist wie ein einfaches Kopierwerkzeug für eine Anwendung. Universal AI Clipboard ist ein vollständiger systemweiter Zwischenablage-Manager mit Slot-Verwaltung, Transformationspipeline und protokollübergreifender Integration.

> **Ich gebe meinen Status als Entdecker nicht auf.** Ich habe dieses Konzept unabhängig formuliert und systematisiert und mehrstufige Recherchen durchgeführt, die keine vollständigen Analoga fanden. Nachdem ich erst nach Veröffentlichung des Manifests von TJ Guadagnos Arbeit erfuhr, erkenne ich seinen unabhängigen Beitrag an und betrachte es als meine Pflicht, dies im Manifest zu reflektieren.

---

## 🏛️ NAME

**Offizieller Name:** **UNIVERSAL AI CLIPBOARD (UAC)**
**Technischer Name:** Content Reference Mechanism
**Slogan:** _«Reuse, Don't Regenerate»_
**Metapher:** Strg+C / Strg+V für KI-Agenten

---

## 🌍 DAS PROBLEM

### Der fundamentale Widerspruch

Moderne KI-Agenten verschwenden **bis zu 90% ihres Ausgabeverkehrs** mit dem monotonen Neugenerieren von Inhalten, die bereits im Sitzungskontext existieren.

Jedes Mal, wenn ein Modell einen Befehl, einen Codeblock oder einen Textfragment schreibt — generiert es ihn von Grund auf neu, selbst wenn derselbe Inhalt vor einer Minute erstellt wurde. Das Modell hat keine Möglichkeit, auf bereits vorhandene Inhalte instrumentell zu verweisen.

### Globaler Maßstab des Problems

- Millionen von KI-Agenten arbeiten weltweit täglich
- Jeder führt dutzende Tool-Aufrufe pro Sitzung durch
- Ein erheblicher Teil jedes Aufrufs ist die Neugenerierung vorhandener Inhalte
- Dies führt zu enormem Energieverbrauch, Rechenverschwendung und finanziellen Kosten

### Warum bestehende Ansätze das Problem nicht lösen

| Ansatz | Einschränkung |
| ----------------------- | --------------------------------------------------------------- |
| **Prompt-Caching** | Funktioniert nur mit statischen Teilen, nicht mit dynamischen Inhalten |
| **Semantisches Caching** | Cached nach Abfragebedeutung, erlaubt keine Fragmentzitierung |
| **Kontextkompression** | Komprimiert Verlauf, bietet aber kein Zitierwerkzeug |
| **RAG** | Ruft aus externen Quellen ab, verwendet internen Kontext nicht wieder |
| **Tool-Verkettung** | Verbindet Aufrufe, erlaubt aber nicht das Referenzieren ihrer Ergebnisse |

---

## 💡 DIE LÖSUNG: UNIVERSAL AI CLIPBOARD

### Die Kernidee

Ein KI-Agent erhält die Fähigkeit, **auf bereits vorhandene kontextuelle Inhalte zu verweisen**, anstatt sie neu zu generieren. Beim Aufruf eines beliebigen Tools, das Textparameter akzeptiert (Befehle, Code, Text), kann der Agent angeben: «nimm dieses Fragment von dort» — anstatt es von Grund auf neu zu schreiben.

### Mosaik-Assembly: Information wie ein Puzzle zusammensetzen

Über die einfache Eins-zu-Eins-Zitierung hinaus ermöglicht dieses Konzept eine grundlegend neue Art der Informationszusammenstellung — **Mosaik-Assembly**.

Ein Agent kann **mehrere Fragmente aus verschiedenen Quellen** in einem einzigen Vorgang kombinieren:

- Code aus einer Datei
- Konfiguration aus dem Chat-Verlauf
- Befehlsausgabe aus dem Terminal
- Ergebnisse externer APIs

Der Agent kann **on-the-fly bearbeiten** — Text in jedem Fragment ändern, umschließen, ersetzen. Er kann Fragmente **neu anordnen**, **verschachteln**, **überlappende Teile zusammenführen** und Inhalte rekursiv **umstrukturieren**.

**Die Kern-Einsicht:** Statt neuen Text zu generieren, agiert das Modell als **Redakteur und Kurator** vorhandener Inhalte — wesentlich effizienter, präziser und fehlerärmer.

### Zwischenablage-Manager: Benannte Slots zur Speicherung

Eine natürliche Erweiterung dieses Konzepts ist ein **Zwischenablage-Manager mit benannten Slots**.

Der Agent kann:
- **Fragmente speichern** in benannten Slots (`clip-1`, `clip-2`, `config-block`, `error-log`, usw.)
- **Slots nach Namen referenzieren** statt nach Inhalt — null Tokens für Beschreibung
- **Inhalte zwischen Slots austauschen und neu organisieren**
- **Zusammengesetzte Dokumente erstellen** durch Referenzierung mehrerer Slots
- **Fragmente zwischen Sitzungen beibehalten** — überstehen Kontextkompression und Sitzungsneustarts

### Der axiale Unterschied zu bestehenden Mechanismen

Alle bestehenden Zitiermechanismen in KI (Citations API, Grounding, ContextCite) arbeiten auf der **«Agent → Benutzer»-Achse** — sie zeigen dem Menschen, wo der Agent Informationen herhat.

Universal AI Clipboard arbeitet auf der **«Agent → Agent»-Achse** — es erlaubt dem Agenten selbst, Inhalte zwischen seinen eigenen Tool-Aufrufen wiederzuverwenden. Dies ist eine grundlegend neue Kategorie.

| Mechanismus | Achse | Zweck |
| -------------------------- | ----------------- | --------------------------------- |
| Anthropic Citations | Agent → Benutzer | Quelle der Antwort anzeigen |
| OpenAI Citations | Agent → Benutzer | Quellen anzeigen |
| Google Grounding | Agent → Benutzer | Websuche bestätigen |
| **★ UAC (diese Entdeckung)** | **Agent → Agent** | **Inhalte zwischen Aufrufen wiederverwenden** |

---

## 🧩 FÜNF KERNMECHANISMEN

### Mechanismus 1: 🔗 Syntaktische Zwischenablage

Das Modell gibt nur ein **Ankerelement** an — einen Funktionsnamen, Klassennamen oder eine Variable. Das System automatisch:
1. Findet dieses Element in der angegebenen Quelle (Datei, Chat-Nachricht, Befehlsausgabe)
2. Bestimmt seine genauen Grenzen als syntaktische Einheit
3. Extrahiert die gesamte Einheit

**Ersparnis:** wenige Tokens für die Referenz statt tausende Tokens Code.

```
{ source: "file", path: "utils.ts", focus: "calculateSum" }
  → 2 Tokens statt 800+ Tokens der gesamten Funktion
```

### Mechanismus 2: 📇 Ankerpaar-Zitierung

Das Modell gibt nur **START** und **ENDE** des gewünschten Fragments an (15-40 Zeichen jeweils). Das System findet alles dazwischen mittels mehrstufiger Suche:

1. **Exakte Übereinstimmung** — Fragment wörtlich gefunden (~70% der Fälle)
2. **Normalisierte Übereinstimmung** — Unterschiede in Leerzeichen, Groß-/Kleinschreibung, Interpunktion ignoriert
3. **Unscharfe Übereinstimmung** — kleine Tippfehler toleriert (~9% der Fälle)
4. **Wortgrenzenerweiterung** — Fragmentintegrität

```
{ source: "chat", ref: "-1",
  start: "function calculateSum(",
  end: "return result;" }
  → ~10 Tokens statt 200+
```

### Mechanismus 3: 🧠 Nachrichtenindexkarte

Bei der Arbeit mit Chat-Verlauf wird ein separater Index erstellt — eine Karte exakter Zeichenpositionen für jede Nachricht und jede Zeile darin. Das Modell schreibt eine kurze Referenz wie `"datensatznummer:startzeile..endzeile"`, und das System extrahiert das genaue Fragment.

```
{ source: "chat", ref: "167:14..18" }
  → "Datensatz #167, Zeilen 14-18" → exakte Extraktion
```

### Mechanismus 4: 🔄 Transformationspipeline

Ein kopiertes Fragment kann **on-the-fly modifiziert** werden — bevor es das Tool erreicht. Verfügbare Operationen:

- **Ersetzen** — einen Teilstring im Fragment ändern
- **Voranstelle** — Text vor dem Fragment hinzufügen
- **Umschließen** — Fragment in eine Vorlage einbetten
- **Anhängen** — Text nach dem Fragment hinzufügen
- **Verbinden** (für mehrere Referenzen) — Fragmente mit Trennzeichen zusammenführen

```
{ ref: { ... }, transform: { wrap: "try { {content} } catch (err) { }" } }
  → Funktion nehmen, in try-catch verpacken, schreiben — alles in 1 Aufruf
```

### Mechanismus 5: 🔁 Protokollübergreifende Zitierung (MCP)

Referenzmarker können direkt in Textparameter aller Tools eingebettet werden, einschließlich externer MCP-Server. Das System erkennt diese Marker automatisch und substituiert den echten Inhalt vor dem Aufruf des externen Servers.

```
"{{ref:source=chat,ref=-1,start=export const config}} --host production"
  → 91% Inhalt aus Kontext, 9% vom Modell generiert
```

---

## 🔭 ZUKUNFTSRICHTUNGEN

### 🏖️ Isolierte Untersitzungen für Forschung

Für komplexe Aufgaben, die viele Zwischenschritte erfordern, kann ein Hilfsagent in einer isolierten temporären Untersitzung gestartet werden. Er führt die ganze «Schmutzarbeit» aus, gibt nur das saubere Ergebnis zurück, und die Untersitzung wird zerstört.

### Andere Richtungen

- Prädiktives Caching häufig verwendeter Fragmente
- Automatische Erkennung doppelter Aufrufe
- Intelligente Disambiguierung mehrdeutiger Referenzen
- Integration mit Speicher- und Langzeitspeichersystemen

---

## 💰 WIRTSCHAFTLICHE AUSWIRKUNGEN

### Pro Agent

| Metrik | Ohne Mechanismus | Mit Mechanismus | Einsparung |
| -------------------------------- | ----------------- | -------------- | ---------- |
| Tokens pro Zitat (langer Code) | 200-500 | 5-15 | **96-97%** |
| Tokens pro Zitat (kurzer Code) | 50-100 | 2-5 | **90-95%** |
| Tokens pro Sitzung | 25.000-50.000 | 5.000-15.000 | **60-80%** |
| Energie pro Sitzung | willkürliche Einheit | 5× weniger | **~80%** |

### Globaler Maßstab

Bei branchenweiter Einführung werden täglich Milliarden von Tokens eingespart, was einer Reduzierung des Energieverbrauchs des KI-Sektors um Dutzende Prozent und einer Verringerung des CO₂-Fußabdrucks um zehntausende Tonnen pro Jahr entspricht.

---

## 🔬 EINZIGARTIGKEITSÜBERPRÜFUNG

Ich führte **umfangreiche mehrstufige Tiefenrecherchen** (7 Runden, ~50 Quellen) durch, die alle bekannten Kategorien von KI-Agenten-Architekturen abdeckten.

*Nach Veröffentlichung des Manifests wurde in zusätzlichen Analysen (Runden 8-10) entdeckt, dass TJ Guadagno unabhängig einen experimentellen Prototyp des Konzepts implementierte — Clipboard Primitives. Diese Arbeit wurde in den ersten 7 Suchrunden aufgrund ihrer geringen Sichtbarkeit (LinkedIn Pulse + GitHub ohne Sterne) nicht identifiziert.*

**Ziel:** Etwas finden, das dasselbe Problem löst — einem KI-Agenten erlauben, vorhandene Inhalte zwischen Tool-Aufrufen zu referenzieren anstatt sie neu zu generieren.

**Ergebnis: nichts dergleichen gefunden.**
*Präzisierung: TJ Guadagnos experimentelle Arbeit (Clipboard Primitives, ~Dezember 2025) ist eine partielle Implementierung (~40% des UAC-Konzepts) und bestätigt die Lebensfähigkeit der Idee, ist aber kein vollständiges Analogon.*

> **Universal AI Clipboard hat keine vollständigen Analoga in der weltweiten Praxis von KI-Agentensystemen. Das einzige bekannte partielle Analogon — Clipboard Primitives — wurde erst nach Veröffentlichung des Manifests entdeckt.**

---

## ⚖️ RECHTLICHER STATUS

**🏛️ Creative Commons Zero (CC0) — Gemeinfreiheit**

Sie können frei:
- ✅ **Nutzen** in kommerziellen und nicht-kommerziellen Projekten
- ✅ **Modifizieren** und an Ihre Bedürfnisse anpassen
- ✅ **Verbreiten** in jeder Form
- ✅ **Ihre Verbesserungen patentieren** (aber nicht die Kernidee)
- ✅ **Übersetzen** in jede Sprache

> **Ich verzichte bewusst auf alle Patentrechte an dieser Technologie. Sie muss allen gehören.**

---

## 🗓️ ZEITLEISTE

| Datum | Ereignis |
| ------------------- | ------------------------------------------------------------------------ |
| **~2021** | Erstes Bewusstsein für das Problem (DScoNOIZ): Gedanke «Modell sollte nicht neu generieren, was es bereits gesehen hat» |
| **~Dezember 2025** | **Unabhängiges Experiment:** TJ Guadagno veröffentlicht Clipboard Primitives |
| **Mai — Juni 2026** | Recherche: Analyse bestehender KI-Agenten-Architekturen |
| **Juni 2026** | Entdeckung: Keine bestehende Technologie hat ein vollständiges Analogon |
| **Juni 2026** | Universal AI Clipboard Konzept formuliert |
| **3. Juni 2026** | Einzigartigkeitsrecherche abgeschlossen — **keine vollständigen Analoga gefunden** |
| **3. Juni 2026** | **Dieses Manifest veröffentlicht** — Entdeckung in die Gemeinfreiheit entlassen |
| **4. Juni 2026** | TJ Guadagnos Arbeit entdeckt — Anerkennung des unabhängigen Mitentdeckers |

---

## 🎯 AUFRUF ZUM HANDELN

Entwickler von KI-Frameworks, KI-Agenten-Ersteller, Forscher, Unternehmen, Umweltschützer, Open-Source-Gemeinschaft — **diese Technologie gehört allen. Forkt, implementiert, verbessert sie.**

---

```
  ╔══════════════════════════════════════════════════════════════════╗
  ║                                                                  ║
  ║   UNIVERSAL AI CLIPBOARD (UAC)                                   ║
  ║   Content Reference Mechanism                                    ║
  ║   Optional Inter-Tool Content Citation Mechanism                 ║
  ║                                                                  ║
  ║   «Reuse, Don't Regenerate»                                      ║
  ║   «Wiederverwenden, nicht neu generieren»                        ║
  ║                                                                  ║
  ║   CC0 1.0 Universal — Public Domain                              ║
  ║   github.com/DScoNOIZ                                            ║
  ║   3. Juni 2026                                                   ║
  ║                                                                  ║
  ╚══════════════════════════════════════════════════════════════════╝
```

---

_Dieses Manifest kann frei in jede Sprache übersetzt werden. Original auf Russisch._

_Englische Version: [MANIFEST.md](MANIFEST.md)_
