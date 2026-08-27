# Agent context

## Was dieses Repository ist

**[Zielbild]-Material des CRA-Piloten** — ein Fork von
`dotnet-architecture/eShopOnWeb` (`net8.0`, upstream seit 13.01.2025 archiviert,
Central Package Management über `Directory.Packages.props`).

**Er trägt keine MVP-Abnahmeprüfung.** Sein einziger Zweck im Jetzt ist die
Nachmessung von spec.md §12.3: das Zielframework fehlt in der CycloneDX-SBOM
vollständig (`metadata.component` gibt es gar nicht) — eine CVE in .NET selbst
kann darum in keiner Dependency-Track-Version als Finding erscheinen. Details:
[CRA-Private#52](https://github.com/WeierE1/CRA-Private/issues/52).

Gesteuert wird alles aus [`WeierE1/CRA-Private`](https://github.com/WeierE1/CRA-Private).

## Regeln

- **Nichts fürs Zielbild bauen** (P4): kein Renovate, kein SBOM-Upload nach
  Dependency-Track, keine statischen .NET-Tore. Wenn Zeit übrig ist, geht sie in
  die Nice-to-have-Liste von `CRA-Private`, nicht hierher.
- **Kein Direktpush auf `main`** — Ruleset aktiv, 409. Alles per PR.
- SDK über `global.json` festgenagelt (8.0.x). Das Wurzelverzeichnis enthält
  **zwei** Solutions — `dotnet`-Kommandos brauchen `eShopOnWeb.sln` ausdrücklich
  (sonst MSB1011).

## Dokumentation

**Nach jedem gemergten PR:** Eintrag in [`docs/changes/`](docs/changes/README.md)
— Konvention steht im Index von `CRA-Private/docs/changes/` und im Skill
`change-catalogue`. Repo-übergreifende Learnings nach `CRA-Private/LEARNINGS.md`.
