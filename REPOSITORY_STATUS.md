# Repository-Status – alltags-helfer

**Bestandsprüfung: 07.10.2026**

Grundlage: GitHub-Standardbranch `main`, Commit [`824a1b4beb69`](https://github.com/Ernestokoeber/alltags-helfer/commit/824a1b4beb698b45649f2496f7872a9580c3154f). Die Angaben beziehen sich auf diesen Snapshot; sie bestätigen keinen aktuellen Live-Betrieb.

## Implementierter Stand

Sphera: SvelteKit-PWA mit IndexedDB/Dexie, Aufgaben, Notizen, Projekten, Kalender und Tracking. Geräte-Sync und generische Push-Erinnerungen sind als Cloudflare Worker mit D1 implementiert.

## Dokumentationsabgleich und offene Punkte

- README-Stack von geplantem Axum-Server auf vorhandenen Cloudflare Worker korrigiert.
- Feste Testzahl durch überprüfbare Testbefehle ersetzt; VM-Workflow beibehalten.
- Worker-Doku um Push-Endpunkte, VAPID-Konfiguration und Cron ergänzt.
- Bekannte npm-Advisories beheben und Frontend/Worker anschließend getrennt prüfen.

## Verifikation

- Quelltext, Paket-/Lockdateien, vorhandene Einstiegsbefehle und GitHub-Metadaten geprüft. Keine vollständige Anwendungssuite lokal neu ausgeführt.

Jüngster gefundener Workflow: [E2E Smoke](https://github.com/Ernestokoeber/alltags-helfer/actions/runs/28104227478), `completed` / `success`, Branch `main`, Commit `824a1b4beb69`, gestartet 2026-06-24. Dieser Lauf gehört zum geprüften Codecommit.

| Workflow am geprüften Head | Ergebnis |
|---|---|
| [E2E Smoke](https://github.com/Ernestokoeber/alltags-helfer/actions/runs/28104227478) | `success` |
| [Deploy GitHub Pages](https://github.com/Ernestokoeber/alltags-helfer/actions/runs/28104227463) | `success` |

## Branch-Abgleich

Bei den erfolgreich verglichenen Branches wurden keine zusätzlichen Ahead-Commits gegenüber dem Standardbranch gefunden.

## Dependency-Prüfung

Registry-Versionen wurden am Prüftag direkt von npm, PyPI und crates.io abgefragt. „Neueste Version“ ist eine Verfügbarkeitsangabe, keine automatische Upgradeempfehlung. Mindestversionen zeigen **nicht** den tatsächlich installierten Stand. Paket-/Lockfiles wurden nicht aktualisiert.

### npm-Lockfiles

`npm audit --package-lock-only --ignore-scripts --json` wurde ohne `fix` ausgeführt. npm zählt betroffene Pakete einschließlich transitiver Abhängigkeiten; daraus folgt nicht automatisch eine ausnutzbare Anwendungslücke.

| Manifest | Niedrig | Mittel | Hoch | Kritisch | Gesamt |
|---|---:|---:|---:|---:|---:|
| `package.json` | 1 | 3 | 5 | 0 | 9 |

| Betroffenes Paket | Schwere | Advisory / Kette |
|---|---|---|
| `@sveltejs/kit` (package.json) | moderate | [@sveltejs/kit](https://github.com/advisories/GHSA-866w-xmhq-wj7x), [@sveltejs/kit](https://github.com/advisories/GHSA-wqjv-9729-c5q2), [@sveltejs/kit](https://github.com/advisories/GHSA-29g2-3rmr-qm68) |
| `@vitest/mocker` (package.json) | moderate | [@vitest/mocker](https://github.com/advisories/GHSA-82fw-gwwq-j7x9) |
| `cookie` (package.json) | low | [cookie](https://github.com/advisories/GHSA-pxg6-pf52-xh8x) |
| `devalue` (package.json) | high | [devalue](https://github.com/advisories/GHSA-9rgm-9g3h-6x36), [devalue](https://github.com/advisories/GHSA-j22f-vq7h-c4qm), [devalue](https://github.com/advisories/GHSA-hx4r-w6wj-j8fg), [devalue](https://github.com/advisories/GHSA-mcm9-63f2-9j32), [devalue](https://github.com/advisories/GHSA-wf3x-273g-mvxv), [devalue](https://github.com/advisories/GHSA-x5rw-q4pp-hg5g), [devalue](https://github.com/advisories/GHSA-4q55-j62x-fr9h) |
| `nanoid` (package.json) | high | [nanoid](https://github.com/advisories/GHSA-28wg-ghj8-5hjv), [nanoid](https://github.com/advisories/GHSA-2v37-7h3g-55p8) |
| `postcss` (package.json) | high | [postcss](https://github.com/advisories/GHSA-fxqj-rqcc-2cmp), [postcss](https://github.com/advisories/GHSA-r28c-9q8g-f849) |
| `source-map-js` (package.json) | high | [source-map-js](https://github.com/advisories/GHSA-68fv-2mgg-jv7q) |
| `undici` (package.json) | high | [undici](https://github.com/advisories/GHSA-8xcm-r25x-g524), [undici](https://github.com/advisories/GHSA-4cwx-7wf7-3272), [undici](https://github.com/advisories/GHSA-m8rv-5g2x-5cg5), [undici](https://github.com/advisories/GHSA-jr45-8vmc-qm54), [undici](https://github.com/advisories/GHSA-v3r7-h72x-cjcm), [undici](https://github.com/advisories/GHSA-3wwx-pv8p-q78v), [undici](https://github.com/advisories/GHSA-pmjh-fq2x-6v4x), [undici](https://github.com/advisories/GHSA-r53p-7pc4-xj5r), [undici](https://github.com/advisories/GHSA-rfgv-xxqx-mfg5), [undici](https://github.com/advisories/GHSA-3xpg-4rpp-hhhm), [undici](https://github.com/advisories/GHSA-2jfj-6hjv-fm6j), [undici](https://github.com/advisories/GHSA-2gqq-gqf2-x968), [undici](https://github.com/advisories/GHSA-w293-vg96-wgc3), [undici](https://github.com/advisories/GHSA-8436-99hf-9mmv), [undici](https://github.com/advisories/GHSA-rx4f-c7p8-82vq) |
| `vitest` (package.json) | moderate | [vitest](https://github.com/advisories/GHSA-82fw-gwwq-j7x9) |

### Python-/Rust-Pins

Versionierte `requirements*.txt`, `uv.lock` und `Cargo.lock` wurden gegen die [OSV-Datenbank](https://osv.dev/) abgeglichen. Ergebnisse umfassen gegebenenfalls auch Wartungs-/Unmaintained-Hinweise. Aliasse wie GHSA/PYSEC/RUSTSEC können dasselbe Problem beschreiben. Ohne Lockfile/Mindestversions-Auflösung ist keine vollständige transitive Prüfung möglich.

Für die aus diesem Repository abgefragten festen Python-/Rust-Versionen wurden keine OSV-Treffer gemeldet, oder es lagen keine festen Versionen zum Abgleich vor. Dies bestätigt keine vollständige Sicherheitsprüfung einer tatsächlich installierten Umgebung.

### Direkte Deklarationen und Registry-Stand

| Datei | Paket | Deklariert | Direkt gelockt (npm) | Neueste Registry-Version |
|---|---|---|---|---|
| `package.json` | npm: `@fontsource-variable/outfit` | `^5.2.8` | `5.2.8` | [5.3.0](https://registry.npmjs.org/%40fontsource-variable%2Foutfit/latest) |
| `package.json` | npm: `@playwright/test` | `^1.61.1` | `1.61.1` | [1.63.0](https://registry.npmjs.org/%40playwright%2Ftest/latest) |
| `package.json` | npm: `@sveltejs/adapter-static` | `^3.0.10` | `3.0.10` | [4.0.0](https://registry.npmjs.org/%40sveltejs%2Fadapter-static/latest) |
| `package.json` | npm: `@sveltejs/kit` | `^2.57.0` | `2.63.0` | [3.0.1](https://registry.npmjs.org/%40sveltejs%2Fkit/latest) |
| `package.json` | npm: `@sveltejs/vite-plugin-svelte` | `^7.0.0` | `7.1.2` | [7.3.1](https://registry.npmjs.org/%40sveltejs%2Fvite-plugin-svelte/latest) |
| `package.json` | npm: `@tailwindcss/vite` | `^4.2.2` | `4.3.0` | [4.3.3](https://registry.npmjs.org/%40tailwindcss%2Fvite/latest) |
| `package.json` | npm: `@testing-library/jest-dom` | `^6.9.1` | `6.9.1` | [7.0.1](https://registry.npmjs.org/%40testing-library%2Fjest-dom/latest) |
| `package.json` | npm: `@testing-library/svelte` | `^5.3.1` | `5.3.1` | [5.4.2](https://registry.npmjs.org/%40testing-library%2Fsvelte/latest) |
| `package.json` | npm: `@testing-library/user-event` | `^14.6.1` | `14.6.1` | [14.6.7](https://registry.npmjs.org/%40testing-library%2Fuser-event/latest) |
| `package.json` | npm: `@types/node` | `^25.9.1` | `25.9.1` | [26.6.4](https://registry.npmjs.org/%40types%2Fnode/latest) |
| `package.json` | npm: `dexie` | `^4.4.3` | `4.4.3` | [4.4.6](https://registry.npmjs.org/dexie/latest) |
| `package.json` | npm: `fake-indexeddb` | `^6.2.5` | `6.2.5` | [6.2.5](https://registry.npmjs.org/fake-indexeddb/latest) |
| `package.json` | npm: `happy-dom` | `^20.10.1` | `20.10.1` | [20.14.5](https://registry.npmjs.org/happy-dom/latest) |
| `package.json` | npm: `jsdom` | `^29.1.1` | `29.1.1` | [30.1.2](https://registry.npmjs.org/jsdom/latest) |
| `package.json` | npm: `svelte` | `^5.55.2` | `5.56.2` | [5.57.2](https://registry.npmjs.org/svelte/latest) |
| `package.json` | npm: `svelte-check` | `^4.4.6` | `4.6.0` | [4.7.6](https://registry.npmjs.org/svelte-check/latest) |
| `package.json` | npm: `tailwindcss` | `^4.2.2` | `4.3.0` | [4.3.3](https://registry.npmjs.org/tailwindcss/latest) |
| `package.json` | npm: `typescript` | `^6.0.2` | `6.0.3` | [7.0.2](https://registry.npmjs.org/typescript/latest) |
| `package.json` | npm: `vite` | `^8.0.7` | `8.0.16` | [8.3.3](https://registry.npmjs.org/vite/latest) |
| `package.json` | npm: `vitest` | `^4.1.8` | `4.1.8` | [5.0.3](https://registry.npmjs.org/vitest/latest) |

## Umfang und Grenzen

Geprüft wurden alle eigenen GitHub-Repositories aus der paginierten Owner-Liste, jeweils der Standardbranch; andere Branches wurden auf Git-Abweichungen verglichen, nicht vollständig erneut als Anwendungen getestet. Betriebszustände externer Provider, personenbezogene Inhalte, Vertrags-/Datenschutztexte und rechtliche Regelkataloge sind nicht fachlich neu abgenommen. Es wurden keine Deployments, Live-Zahlungen, Posts, Mails oder kostenpflichtigen KI-Jobs ausgelöst.

Quellen: Repository-Dateien am oben verlinkten Commit, [GitHub Actions](https://github.com/Ernestokoeber/alltags-helfer/actions), Paketregistries und [OSV](https://osv.dev/). Bei erneuter Prüfung Snapshot, Tests, CI-Zuordnung und Audits gemeinsam aktualisieren.
