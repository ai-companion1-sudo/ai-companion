# AI Companion

Ein digitaler Companion (Buddy) zum Chatten im Browser – mit einem echten Gedächtnis.

## Was ist die Idee?

Anders als bei den meisten Chatbots soll dieser Companion sich **über die Zeit an alles erinnern**, was man ihm erzählt, und daraus eine wachsende, persönliche Beziehung aufbauen – kein Gespräch beginnt bei null.

Geplant ist außerdem eine Auswahl mehrerer Companion-Profile (unterschiedliches Aussehen, Charakter, Hintergrund – ähnlich einer Kennenlern-App), mit denen man parallel chatten kann. Jeder Companion hat sein eigenes, getrenntes Gedächtnis über den Nutzer.

**Start-Ton:** freundschaftlicher Buddy, keine expliziten Inhalte. Die Technik wird aber so gebaut, dass spätere Erweiterungen (Sprache/Anruf, Avatar, ggf. später Alters-geprüfte Inhalte) möglich sind, ohne alles neu bauen zu müssen.

## Technik (Tech-Stack)

- **Frontend:** [Next.js](https://nextjs.org) mit TypeScript – die Web-Oberfläche im Browser
- **Backend/Datenbank:** [Supabase](https://supabase.com) – Login, Datenspeicherung und das Gedächtnis-System (PostgreSQL-Datenbank mit der Erweiterung `pgvector`, die "ähnliche Erinnerungen" wiederfinden kann)
- **KI-Modell:** wird über eine austauschbare Zwischenschicht (Adapter) angesprochen, nie direkt fest verdrahtet

## Ordnerstruktur

```
ai_companion/
├── app/                 # Der eigentliche Programmcode (Next.js-Projekt)
├── docs/                # Fachliche & technische Dokumentation
│   └── KANBAN.md         # Aufgabenliste (Backlog, To Do, In Progress, Done)
├── backlog/              # Ideen und Aufgaben für später
│   └── BACKLOG.md
├── PROJEKT_LOG.md        # Projekttagebuch – was wurde wann gemacht und warum
└── README.md             # Diese Datei
```

## Wichtige Grundregeln

- Zugangsdaten und Schlüssel stehen ausschließlich in einer lokalen `.env`-Datei, niemals im Code und niemals in Git.
- Wir bauen zuerst den **Chat- und Gedächtniskern**, nicht Login, Design oder Bezahlung.

## Projektstand

Der aktuelle Stand, alle Entscheidungen und die nächsten Schritte stehen in [`PROJEKT_LOG.md`](./PROJEKT_LOG.md) und im [Kanban-Board](./docs/KANBAN.md).
