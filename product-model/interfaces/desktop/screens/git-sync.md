---
entities:
- entity: settings
  shows:
  - Auto sync
  - Conflict strategy
  collects:
  - Auto sync
  - Conflict strategy
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/settings/ui/settings_sections/SyncSettings.kt
---

# Git Sync settings

Automatic synchronization and conflict-resolution preferences.
