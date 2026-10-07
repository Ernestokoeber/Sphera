# alltags-helfer zuhause wieder aufbauen

Stand: **07.10.2026**. Dieser Nachbau gehört zum gemeinsamen PC-Snapshot `pc-2026-10-07`. Den exakten veröffentlichten Commit und den zu holenden Branch nennt `playbooks/rebuild/manifest.json`. Ein normales `git pull main` kann einen anderen Stand liefern.

## Voraussetzungen und Spezifikation

Node 24.x; npm; Ubuntu 24.04 Multipass-VM alltagshelfer-dev; Cloudflare Worker/D1 für Sync.

Versionen aus Manifesten, Toolchain-Dateien und Lockfiles verwenden. Der Quell-PC hat Windows 11 Pro Build 26100, Intel i5-6500 (4 Kerne), 31,9 GiB RAM und eine RTX 2060. Das sind gemessene Quellwerte, keine belegten Mindestanforderungen. Die Infrastruktur ist pro Projekt einzurichten; Ports aus mehreren Projekten können kollidieren, daher zunächst einzeln starten.

## Quellcode und lokale Arbeiten

Grundlage vor diesem Checkpoint: `5eef3994a69f8c3a6d24b4857d831cafc0b721ed`. In diesem Checkpoint gesichert: **0 zuvor lokale geänderte/neue Dateien**. Der Checkpoint enthält Arbeitsstände, die erst nach den folgenden Prüfungen als betriebsbereit gelten. Historische Angaben in REPOSITORY_STATUS.md beschreiben den früheren Audit-Snapshot und ersetzen die Abnahme dieses Checkpoints nicht.

## Einrichtung

Ab dem Repository-Root; Verzeichniswechsel und VM-Vorgaben beachten. Bestehende `.env`-Dateien erhalten und fehlende Werte gezielt ergänzen.

```text
npm ci
```

Vorhandene Konfigurationsvorlagen: keine Standard-.env-Vorlage gefunden; README und Projektkonfiguration prüfen.

Benannte Variablen aus den Vorlagen (ohne Werte): keine aus .env-Vorlagen extrahiert.

## Start und Prüfung

```text
npm run dev
```

```text
npm run check
npm test
npm run build
```

Erfolg bedeutet: benötigte Werkzeuge verfügbar, Lockfiles unverändert installiert, Tests/Build erfolgreich, Dienste erreichbar und ein lokaler Funktionscheck bestanden. Fehlende Zugänge oder nicht ausgeführte Integrationstests als **offen** protokollieren. Keine produktiven Daten durch Seeds ersetzen.

## Daten und Wiederherstellung

In der App unter Einstellungen JSON exportieren/importieren. IndexedDB und localStorage liegen im Browserprofil; ein Git-Clone stellt sie nicht wieder her. Sync-Schlüssel und VAPID-Schlüssel separat sichern. Worker-Einrichtung: sync-worker/README.md. VM-Bind-Mount: scripts/vm-dev.sh.

Erst auf einer getrennten Testkopie wiederherstellen und fachlich prüfen. Ein Clone rekonstruiert Quellcode; Datenbankinhalte, Browserdaten, VM-Festplatten und Passwortspeicher kommen aus getrennten Sicherungen. Eine bereits vorhandene Sicherung dieser Daten wurde durch diesen Checkpoint nicht nachgewiesen.

## Versionierte Abhängigkeiten

SHA-256 der gesicherten Lock-/Requirements-Dateien:

| Datei | SHA-256 |
|---|---|
| `package-lock.json` | `778117f4cae7b0a980e042a11bf7e51489414c9b67fcd64060d7fca234467478` |

## Vertiefende vorhandene Anleitungen

- [REPOSITORY_STATUS.md](REPOSITORY_STATUS.md)
