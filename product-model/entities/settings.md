---
singleton: true
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/data/UserSettingsManager.kt#UserSettingsManager
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/settings/ui/SettingsContent.kt
---

# Settings

Preferences kept for this installation of Git Writer.

## Information kept

- **Appearance** — Theme mode, accent, font and editor width preferences; Android 12 or later also offers system dynamic color.
- **App language** — The selected interface language; English is the default.
- **Spell check language** — The desktop dictionary language, defaulting to the app language.
- **Auto sync** — Whether automatic synchronization is enabled; enabled by default.
- **Conflict strategy** — Manual by default, or automatic selection of local or remote file versions.
