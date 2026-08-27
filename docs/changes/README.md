# Change catalogue

Ein Eintrag je gemergtem Pull Request **dieses Forks**. Konvention und
Begründung: `docs/changes/` im Automatisierungs-Repository
[`WeierE1/CRA-Private`](https://github.com/WeierE1/CRA-Private/tree/main/docs/changes).

**Was dieses Repository ist:** ein Fork von `dotnet-architecture/eShopOnWeb`
(`net8.0`, upstream seit 13.01.2025 archiviert). Er ist **[Zielbild]-Material**
des CRA-Piloten und trägt keine MVP-Abnahmeprüfung — sein einziger Zweck im
Jetzt ist die Nachmessung von spec.md §12.3 (das Zielframework fehlt in der
CycloneDX-SBOM vollständig). Details: CRA-Private Issue #52.

<!-- INDEX:BEGIN -->

| PR | Merged (UTC) | Title | Issues | Size | Detail |
|---|---|---|---|---|---|

| [pr-002](https://github.com/WeierE1/eShopOnWeb/pull/2) | 2026-08-27 09:37 | CLAUDE.md: Rolle im CRA-Piloten, Regeln, Katalog-Pflicht | — | +31/−0 · 1 | [→](pr-002-claude-md-rolle-regeln-katalog.md) |
| [pr-001](https://github.com/WeierE1/eShopOnWeb/pull/1) | 2026-08-27 09:30 | Change catalogue anlegen | — | +38/−0 · 1 | [→](pr-001-change-catalogue-anlegen.md) |
<!-- INDEX:END -->
## Was der Katalog nicht abdeckt

**Vier Commits erreichten den Standardzweig direkt, ohne PR und ohne Review** —
per Contents-API, bevor das Ruleset `kein-merge-durch-automatik` (27.08.2026)
den Direktpush unterband:

| Commit | Datum | Was |
|---|---|---|
| `14d908c5` | 26.08. 08:30 | `nullbedingung.yml` — Build/Test + §12.3-Gegenprobe |
| `c33cb63b` | 26.08. 08:34 | Solution ausdrücklich benannt (zwei `.sln` im Wurzelverzeichnis, MSB1011) |
| `d05b2eac` | 26.08. 08:36 | CycloneDX-Schalter `--json` statt `-j` |
| `ebb2a325` | 26.08. 08:38 | Workflow neu geschrieben (der vorige Fix hatte die Datei beschädigt) |

Ergebnis der Kette: Lauf 32948787983 grün, 74 Tests, §12.3 bestätigt
(0 × `net8.0`/`NETCore.App` in der SBOM, `metadata.component` fehlt ganz).
Dokumentiert in pr-054/pr-058 des Automatisierungs-Repositories und in Issue #52.
