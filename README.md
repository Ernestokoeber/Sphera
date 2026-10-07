# Sphera

**Privat & Arbeit, ein Ort.** Ein local-first Second-Brain & Daily-Planner als PWA
(iPhone + Android + Desktop): Notizen, Aufgaben, Termine/Kalender und ein
Arbeitsbereich (Kollegen-Notizen + Kundensupport) — verbunden durch die **Sphären-Sicht**:
Ein Umschalter im Header (Privat / Alles / Arbeit) filtert die gesamte App, sodass
beide Lebensbereiche in einer App leben, ohne sich zu vermischen.

> Den vollständigen Plan, die Architektur und die Roadmap findest du in
> **[PROJEKT.md](./PROJEKT.md)**.

## Design

Dunkles Premium-Theme („Zwei Sphären"): Privat = Amber, Arbeit = Himmelblau —
die beiden Farbwelten rahmen die App und verschmelzen im App-Icon. Glas-Karten
(`backdrop-blur`), schwebende Navigationsleiste, Outfit-Schrift (selbst gehostet,
offline-fähig), Inline-SVG-Icons statt Emojis.

## Stack

- **Client:** SvelteKit als PWA, lokale Daten via IndexedDB (Dexie)
- **Spracheingabe:** OS-Diktat (on-device)
- **Sync/Push-Backend:** Cloudflare Worker + D1 unter `sync-worker/`; Ende-zu-Ende-verschlüsselte Sync-Daten und generische Push-Erinnerungen. Axum/Rust ist im aktuellen Repository nicht implementiert.

## Status

In Umsetzung — alle 6 Tabs funktional, **installierbare PWA** (Service Worker +
Offline), **Unit-/Komponententests (Vitest)** + **E2E-Smoke (Playwright)**. Changelog/Details in **[PROJEKT.md](./PROJEKT.md)**
(Abschnitt „Umgesetzt").

**Funktionen:** globale Sphären-Sicht Privat/Arbeit/Alles (in localStorage gemerkt),
Heute (Schnellnotiz + Briefing + sanfter Tagestipp + „Brücke" mit dem nächsten Termin je Sphäre),
Notizen (Suche/Kategoriefilter/Bearbeiten/Tags/Pin/Kategorie, Markdown), **Aufgaben**
(projektübergreifend, Frist/Wiederholung), **Projekte** (laufende Vorhaben bündeln
Notizen, verschachtelbar, archivierbar), Termine + **Monats-Kalender** (Kategorie,
Vorbereitungs-Tasks, wiederkehrend), **Arbeit** (Kollegen-Notepad + Kundensupport-Log
+ **Anheft-Bereich** für dauerhaft oben angepinnte Workflows), **Tracking** (Zeit-/Lern-Erfassung
+ Dashboard: Tag/Woche/Fach/Streak), lokale Auto-Kategorie
für „offen"-Notizen (kein Cloud), **Geräte-Sync** (E2EE, automatisch — bei Start, im
Vordergrund, alle 2 Min und sofort nach jeder Änderung), **Push-Erinnerungen**
(generisch, E2EE-konform) und **Datensicherung** (JSON-Export/-Import mit
Last-Write-Wins-Merge, unter Einstellungen). Installierbar (Manifest + Icons),
offline-fähig, `storage.persist()` + Warnung bei blockierter IndexedDB.

## Deployment (GitHub Pages)

Jeder Push auf `main` baut und veröffentlicht die PWA automatisch über
`.github/workflows/deploy.yml` nach **GitHub Pages**:
`https://ernestokoeber.github.io/alltags-helfer/` — von dort lässt sie sich am
Handy „Zum Home-Bildschirm hinzufügen" (installierbare PWA, offline-fähig).

Technik: Der Workflow setzt `BASE_PATH=/alltags-helfer` (→ `paths.base` in
`svelte.config.js`), die Routen werden als Client-Shells prerendert und
`404.html` dient als SPA-Fallback für unbekannte Pfade. Hinweis: Auf dem
GitHub-Free-Plan funktioniert Pages nur bei **öffentlichen** Repos.

## Entwicklung

Läuft in einer Multipass-VM (`alltagshelfer-dev`, Ubuntu 24.04) zur Isolation der
npm-Dependencies.

**Arbeitsteilung (wichtig unter Windows):** Der Quellcode (`src/`, Config) liegt auf
dem Host und wird dort editiert. Die VM hält nur die generierten Ordner
(`node_modules`, `.svelte-kit`, `build`); `node_modules` ist VM-lokal gebunden
(schnell + umgeht die sshfs-Grenzen des Mounts). Vom VM erzeugte Dateien sind auf dem
Host schreibgeschützt — daher **niemals Quellcode in der VM erzeugen**.

**Dev-Server starten** (in der VM):

```bash
multipass exec alltagshelfer-dev -- bash /home/ubuntu/alltags-helfer/scripts/vm-dev.sh
```

Das Skript stellt den `node_modules`-Bind sicher (nötig nach jedem VM-Neustart) und
startet Vite. Hinweis: PWA-Features (Service Worker, Installation, Push) brauchen
HTTPS oder `localhost` — fürs Testen auf echten Geräten später via `mkcert` oder
Cloudflare-Tunnel (siehe PROJEKT.md).

## Prüfungen

Die CI verwendet Node.js 22. Im eingerichteten VM-Checkout: `npm ci`, `npm run check`, `npm test` und `npm run build`. Für Browser-Smoke-Tests zusätzlich Playwright installieren und `npm run test:e2e` ausführen. Ein historisches Testergebnis ist kein Ersatz für einen erneuten Lauf nach Änderungen.

## Bestandsprüfung

Code-/Dokumentationsabgleich, geprüfter Commit, CI-Zuordnung, Branch-Abweichungen und Dependency-Befunde vom **07.10.2026**: [REPOSITORY_STATUS.md](REPOSITORY_STATUS.md).

## Zuhause nachbauen

Gemeinsamer PC-Stand, Voraussetzungen, Start, Prüfungen und getrennte Datensicherung: [REBUILD.md](REBUILD.md). Zentraler Einstieg: `Ernestokoeber/playbooks`, Branch `docs/repository-audit-2026-10-07`, `rebuild/HOME_SETUP.md`.
