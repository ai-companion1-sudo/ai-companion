# Projekttagebuch

Hier halten wir nach jedem Arbeitsschritt fest: Was wurde gemacht, warum, und was kommt als Nächstes.
Das ist das "Gedächtnis" des Projekts – hier kann jeder (auch du oder ein späterer Claude-Chat) nachlesen, wo wir stehen.

---

## 2026-07-01 – Projektstart

**Was gemacht:**
- Grundordner angelegt: `docs/` (Dokumentation), `backlog/` (Ideen/Aufgaben für später), `app/` (späterer Programmcode).
- Dieses Projekttagebuch (`PROJEKT_LOG.md`) erstellt.

**Warum:**
Bevor wir mit Programmieren anfangen, brauchen wir eine saubere Grundstruktur und ein Gedächtnis für Entscheidungen, damit nichts verloren geht.

**Wichtige Entscheidungen (gelten dauerhaft für das ganze Projekt):**
- Produkt: Ein digitaler Companion (Buddy) zum Chatten im Browser, der sich über die Zeit an alles über den Nutzer erinnert und eine wachsende Beziehung aufbaut.
- Start-Ton: freundschaftlicher Buddy, KEINE expliziten Inhalte.
- Architektur von Anfang an so bauen, dass später ohne Umbau erweitert werden kann:
  - Das KI-Modell wird immer über eine austauschbare Zwischenschicht (Adapter) angesprochen, nie direkt.
  - Inhaltsregeln (was der Companion sagen darf) werden an EINER zentralen, umschaltbaren Stelle gebündelt.
  - Ein Alters-Gate (Altersprüfung) wird als einsteckbares Modul vorbereitet, ist aber jetzt inaktiv.
- Browser-first (Web/PWA), spätere Erweiterungen: Sprache/Anruf, Avatar, ggf. Adult-Inhalte.
- Technik: Next.js + TypeScript (Frontend), Supabase (Datenbank/Login/Speicher, PostgreSQL mit pgvector für das Gedächtnis-System), EU-Region (Frankfurt).
- Zugangsdaten immer in `.env`-Datei, NIE im Code oder in Git.
- Wir starten beim Chat- und Gedächtniskern, NICHT bei Login, Design oder Bezahlung.

**Als Nächstes:**
- Kanban-Board anlegen (`docs/KANBAN.md`)
- README.md schreiben
- Git-Repository initialisieren (mit `.gitignore`, damit `.env` nie mitgespeichert wird)

---

## 2026-07-01 – Kanban-Board angelegt + Rollenverteilung der Dateien geklärt

**Was gemacht:**
- `docs/KANBAN.md` erstellt mit den Spalten Backlog, To Do, In Progress, Done.
- Geklärt, wofür welche Datei da ist: `docs/KANBAN.md` = Aufgabenliste, `PROJEKT_LOG.md` = chronologisches Tagebuch/Entscheidungen, `docs/` = fachlich-technische Dokumentation (wird gefüllt, sobald technisch etwas gebaut ist).

**Als Nächstes:**
- README.md schreiben
- Git-Repository initialisieren (mit `.gitignore`, damit `.env` nie mitgespeichert wird)

---

## 2026-07-01 – Projekt-Konten angelegt (Proton Mail + GitHub)

**Was gemacht:**
- Proton-Mail-Konto angelegt: `ai-companion1@proton.me` (dediziert für dieses Projekt, getrennt von privater Mail)
- GitHub-Konto angelegt, verknüpft mit derselben Mail-Adresse

**Wichtig:** Passwörter werden hier NIE dokumentiert. Diese gehören ausschließlich in den persönlichen Passwort-Manager des Nutzers, niemals in Projektdateien, Chat-Verläufe oder Git.

**Sicherheitshinweis vermerkt:** Nutzer hat versehentlich einen Passwort-Export im Chat eingefügt. Empfehlung gegeben, das betroffene Passwort zeitnah zu ändern.

**Als Nächstes:**
- README.md schreiben
- Git-Repository initialisieren (mit `.gitignore`, damit `.env` nie mitgespeichert wird)
- Lokales Repo mit GitHub-Repo `ai-companion1-sudo/ai-companion` verbinden und Beispiel-Inhalt durch unseren Code ersetzen
- Supabase-Konto anlegen (kann mit GitHub-Login erfolgen)

**Update:** GitHub-Mail bestätigt. Ziel-Repository für dieses Projekt festgelegt: `ai-companion1-sudo/ai-companion` (enthält aktuell noch Beispiel-Code, wird beim ersten Push ersetzt).

---

## 2026-07-01 – README.md geschrieben

**Was gemacht:**
`README.md` im Hauptordner erstellt: erklärt in einfachen Worten die Projektidee, den Tech-Stack, die Ordnerstruktur und die Grundregeln.

**Als Nächstes:**
- Git-Repository initialisieren (mit `.gitignore`, damit `.env` nie mitgespeichert wird)
- Lokales Repo mit `ai-companion1-sudo/ai-companion` auf GitHub verbinden

---

## 2026-07-01 – Git-Repository lokal eingerichtet, erster Commit

**Was gemacht:**
- `git init` im Projektordner ausgeführt (lokales Repository, noch NICHT mit GitHub verbunden)
- `.gitignore` erstellt: schützt u.a. `.env`, `node_modules/`, Build-Ordner und lokale Claude-Code-Einstellungen (`.claude/settings.local.json`) davor, jemals mitgespeichert zu werden
- Git-Identität lokal (nur für dieses Projekt) gesetzt: Name `ai-companion1`, Mail `ai-companion1@proton.me`
- Ersten Commit erstellt mit allen bisherigen Setup-Dateien (README, PROJEKT_LOG, Kanban, Backlog, .gitignore)

**Warum:**
Git speichert ab jetzt jede Änderung nachvollziehbar. Wichtig: Es wurde noch NICHTS zu GitHub hochgeladen – das ist ein bewusst separater, späterer Schritt, bei dem wir das lokale Repo mit `ai-companion1-sudo/ai-companion` verbinden.

**Setup abgeschlossen.** Alle 5 geplanten Setup-Schritte (Ordnerstruktur, Projekttagebuch, Kanban-Board, README, Git) sind erledigt.

**Als Nächstes (wartet auf Nutzer-OK):**
- Erster inhaltlicher Schritt für den Chat-Prototyp (siehe Kanban "To Do")

---

## 2026-07-01 – Start Supabase-Setup

**Was gemacht:**
Nutzer hat OK gegeben, mit dem Chat-/Gedächtniskern zu beginnen. Karte "Supabase-Projekt anlegen" von "To Do" nach "In Progress" verschoben. Nutzer wird jetzt Schritt für Schritt durch die Supabase-Kontoerstellung geführt (Konto legt der Nutzer selbst an, wie in den Projektregeln festgelegt).

**Als Nächstes:**
- Supabase-Konto/-Projekt anlegen lassen (EU-Region Frankfurt)
- Schlüssel in `.env`-Datei eintragen (Anleitung dazu geben)

**Update:** Supabase-Konto angelegt (`joi-platform`). Passwort NICHT dokumentiert (Sicherheitsregel, siehe oben). Nutzer hat erneut ein Passwort im Chat eingefügt (2. Mal) – Empfehlung gegeben, es zeitnah zu ändern.

---

## 2026-07-01 – Supabase-Schlüssel in .env.local eingetragen

**Was gemacht:**
- `app/.env.local` (echte Werte, NICHT in Git) und `app/.env.example` (leere Vorlage, darf in Git) angelegt
- Nutzer hat Project URL, Publishable Key (= neuer Name für "anon key") und Secret Key (= neuer Name für "service_role key") selbst aus dem Supabase-Dashboard eingetragen
- Werte wurden nur "blind" geprüft (Länge/Format, nie Klartext-Ausgabe) – mit einer Ausnahme: bei der Fehlersuche wurde die Datei versehentlich einmal per Read-Tool angezeigt, wodurch die Werte kurz im Tool-Verlauf sichtbar waren. Nutzer wurde informiert und gefragt, ob der Secret Key rotiert werden soll – Entscheidung: nein, Risiko wird als gering eingestuft (lokales Projekt, noch nicht produktiv).
- URL enthielt zunächst fälschlich einen `/rest/v1/`-Zusatz, wurde korrigiert.

**Wichtige Lektion:** Vor dem nächsten Mal grundsätzlich NIE `.env`-Dateien mit echten Secrets per Read-Tool öffnen – nur über Skripte prüfen, die lediglich Länge/Format ausgeben.

**Als Nächstes:**
- Next.js-Projekt in `app/` aufsetzen (TypeScript)
- Lokales Repo mit `ai-companion1-sudo/ai-companion` auf GitHub verbinden

---

## 2026-07-01 – Next.js-Projekt aufgesetzt

**Was gemacht:**
- Node.js systemweit von 18.12 auf 24 LTS aktualisiert (via winget), da Next.js mind. Node 20.9 braucht
- Next.js-Projekt in `app/` erstellt: TypeScript, App Router, Tailwind CSS, ESLint, `src/`-Ordnerstruktur
- `.env.local`/`.env.example` blieben erhalten (kurz ausgelagert, nach dem Erstellen zurückgelegt)
- `.claude/launch.json` angelegt, damit der Dev-Server künftig einfach gestartet werden kann
- Server testweise gestartet und per Screenshot geprüft – Next.js-Standardseite lädt korrekt

**Wichtiger Hinweis für zukünftige Arbeit:** Next.js Version ist 16.2.9, sehr neu. Die automatisch erstellte `app/AGENTS.md` warnt ausdrücklich, dass sich APIs/Konventionen von älterem Trainingswissen unterscheiden können – vor dem Schreiben von echtem Code sollte die lokale Doku in `app/node_modules/next/dist/docs/` geprüft werden.

**Kleine Doppelung (unkritisch):** Next.js hat automatisch ein eigenes `app/README.md` und `app/.gitignore` angelegt (Next.js-Standardinhalte). Das überschneidet sich nicht mit unserem Haupt-`README.md`/`.gitignore`, beide Ebenen ergänzen sich einfach.

**Als Nächstes:**
- Lokales Repo mit `ai-companion1-sudo/ai-companion` auf GitHub verbinden (überschreibt Beispiel-Inhalt)
- Danach: erster Chat-Prototyp (Chat-Oberfläche + KI-Adapter)

---

## 2026-07-01 – Mit GitHub verbunden

**Was gemacht:**
- Lokalen Branch von `master` auf `main` umbenannt (GitHub-Konvention)
- Remote `origin` auf `https://github.com/ai-companion1-sudo/ai-companion.git` gesetzt
- Mit Nutzer-Bestätigung: Force-Push durchgeführt, alter Beispiel-Code auf GitHub ersetzt durch unseren Projektstand
- Git Credential Manager (bereits systemweit vorhanden) hat die Anmeldung übernommen, kein Passwort/Token nötig

**Setup ist jetzt komplett:** lokales Projekt + GitHub-Repo sind synchron.

**Als Nächstes:**
- Erster Chat-Prototyp: einfache Chat-Oberfläche + Verbindung zum KI-Modell über einen austauschbaren Adapter

---

## 2026-07-01 – Produktvision erweitert: Mehrere Companions (wie Tinder)

**Was entschieden:**
Statt nur EINEM festen Companion soll es mehrere Companion-Profile geben, die sich in Aussehen, kulturellem Hintergrund, Charaktereigenschaften und Geo-Position unterscheiden. Ablauf:
1. Ein Swipe-Bildschirm (ähnlich Tinder) zum Entdecken und Hinzufügen neuer Companions – jederzeit nutzbar, nicht nur einmalig.
2. Eine Übersicht mehrerer aktiver Chats (ähnlich WhatsApp-Chatliste).
3. Jeder Companion hat sein **eigenes, getrenntes Gedächtnis** über die Beziehung zum Nutzer – Companion A weiß nichts von dem, was der Nutzer Companion B erzählt hat.

**Warum:**
Nutzer-Wunsch: Die App soll sich anfangs wie eine bekannte Kennenlern-/Dating-App anfühlen (Profilauswahl, Swipen), aber mit KI-Companions statt echten Personen, und mehrere parallele Beziehungen ermöglichen statt nur einer.

**Was das technisch bedeutet (wichtig für spätere Datenbank-Planung):**
- Das Gedächtnis-System darf nicht "ein Nutzer = ein Gedächtnis" sein, sondern muss "ein Nutzer + ein Companion = ein eigenes Gedächtnis" abbilden (mehrere getrennte Gedächtnisse pro Nutzer).
- Companion-Profile brauchen eigene Datensätze (Aussehen, Charakter, Hintergrund, Geo-Position).
- Bleibt aber wie ursprünglich geplant: KI-Modell hinter Adapter, Inhaltsregeln zentral, Alters-Gate als inaktives Modul.

**Wichtig:** Das ist ein Design-/Onboarding-Thema. Wir bauen weiterhin zuerst den Chat- und Gedächtniskern (mit einem einzigen Test-Companion), bevor Swipe-Bildschirm, mehrere Profile und Auswahl-UI gebaut werden. Die Idee ist aber jetzt so festgehalten, dass die Datenbank von Anfang an "mehrere Companions pro Nutzer" zulässt, statt später umgebaut werden zu müssen.

**Als Nächstes:**
- Kanban-Board anlegen (`docs/KANBAN.md`)
- README.md schreiben
- Git-Repository initialisieren (mit `.gitignore`, damit `.env` nie mitgespeichert wird)
