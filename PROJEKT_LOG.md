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
