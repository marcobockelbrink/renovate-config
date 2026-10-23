# renovate-config

Gemeinsame [Renovate](https://docs.renovatebot.com/)-Konfiguration für alle Repos.

In jedem Repo genügt eine `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>marcobockelbrink/renovate-config"]
}
```

Voraussetzung: Die [Renovate-App](https://github.com/apps/renovate) ist für dieses Repo **und** das Ziel-Repo installiert (das Preset liegt privat).

## Regeln

- Updates kommen montags vor 6 Uhr, Sicherheitsupdates sofort.
- Neue Versionen erst nach 3 Tagen (Schutz vor zurückgezogenen oder kompromittierten Releases).
- Images und Actions immer per Tag plus Digest gepinnt (`config:best-practices`).
- Minor, Patch und Digest mergen sich selbst, wenn alle Checks grün sind. Renovate wartet selbst auf die Checks,
  `platformAutomerge` ist aus, weil private Free-Repos keine Branch-Protection haben.
- Majors nie automatisch; Postgres-Majors erst nach Freigabe im Dependency Dashboard (Dump/Restore nötig).
- Alle GitHub-Actions-Updates als ein gemeinsamer PR.
