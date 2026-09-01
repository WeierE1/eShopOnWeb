# PR-PROFILE — WeierE1/eShopOnWeb

Profil für den Skill `pr-check` (WeierE1/CRA-Private, Issue #35). **Alle Zahlen
stammen aus einem echten Lauf, nicht aus der Konfiguration** — Beleg ist
jeweils die Lauf-ID.

**Einordnung:** .NET ist im Piloten außerhalb des Umfangs (`spec.md` §0.3,
§37.2, Issue #52). Dieser Fork trägt keine MVP-Abnahmeprüfung; das Profil
existiert, damit niemand die CI-Signale hier raten muss.

Default-Branch: `main`.

## Welche Branches die CI auslöst

- `.github/workflows/dotnetcore.yml` (Name: `eShopOnWeb Build and Test`) —
  `on: [push, pull_request, workflow_dispatch]`: **jeder Push auf jeden
  Branch, jeder Pull Request, dazu manuell.**
- `.github/workflows/nullbedingung.yml` (Name: `nullbedingung`) — ebenso
  `push:` / `pull_request:` / `workflow_dispatch:` ohne Filter.
- `.github/workflows/richnav.yml` — nur `workflow_dispatch`, läuft nie von
  selbst.

## Die echten Build- und Testkommandos

Wörtlich aus den Workflows (nicht aus dem README):

- `eShopOnWeb Build and Test`:
  - `dotnet build ./eShopOnWeb.sln --configuration Release`
  - `dotnet test ./eShopOnWeb.sln --configuration Release`
- `nullbedingung` (mit TRX-Artefakt, dem .NET-Gegenstück zum Surefire-XML):
  - `dotnet restore eShopOnWeb.sln` — **die Solution muss genannt werden**,
    im Wurzelverzeichnis liegen zwei (`Everything.sln`, `eShopOnWeb.sln`);
    ohne Angabe bricht MSBuild mit MSB1011 ab
  - `dotnet build eShopOnWeb.sln --no-restore --configuration Release`
  - `dotnet test eShopOnWeb.sln --no-build --configuration Release --logger "trx;LogFileName=test-results.trx" --results-directory ./testergebnisse`
  - danach (nicht torwachend, `continue-on-error`): SBOM per
    `dotnet CycloneDX` und die §12.3-Gegenmessung

## Festgenageltes SDK

**.NET SDK 8.0.x** — in `nullbedingung.yml` über `global.json`
(`"version": "8.0.x"`, `rollForward: latestFeature`), in `dotnetcore.yml`
direkt als `dotnet-version: '8.0.x'`.

## Altlasten (Vorbestand)

Aus dem grünen `nullbedingung`-Lauf auf `main`,
[33059713307](https://github.com/WeierE1/eShopOnWeb/actions/runs/33059713307)
(2026-08-27):

```
Passed!  - Failed: 0, Passed: 44, Skipped: 0, Total: 44 - UnitTests.dll
Passed!  - Failed: 0, Passed:  3, Skipped: 0, Total:  3 - IntegrationTests.dll
Passed!  - Failed: 0, Passed: 12, Skipped: 0, Total: 12 - FunctionalTests.dll
Passed!  - Failed: 0, Passed: 15, Skipped: 0, Total: 15 - PublicApiIntegrationTests.dll
```

**74 Tests, 0 vorbestehend rot, 0 vorbestehend abgeschaltet** (dieselbe Zahl
wie in CRA-Private Issue #10).

## Laufzeit eines vollständigen Laufs

- `nullbedingung`: **3 min 6 s** (Lauf 33059713307).
- `eShopOnWeb Build and Test`: **2 min 4 s** (Lauf
  [33059713395](https://github.com/WeierE1/eShopOnWeb/actions/runs/33059713395)).

## Bekannte Flakes

**Keine bekannt** (Stand 2026-09-01).
