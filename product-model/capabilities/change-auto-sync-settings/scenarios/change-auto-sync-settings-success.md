---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer turns Sync automatically on or off.
  entities:
  - entity: settings
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::git-sync
    android:
      place: android::git-sync
    ios:
      place: ios::git-sync
- kind: product
  text: The Product saves the Auto sync setting for this installation.
  entities:
  - entity: settings
    effect: changes
    facts:
    - Auto sync
  actor: writer
  contexts:
    desktop:
      place: desktop::git-sync
    android:
      place: android::git-sync
    ios:
      place: ios::git-sync
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/data/UserSettingsManager.kt#UserSettingsManager
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/settings/ui/SettingsViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/settings/ui/SettingsContent.kt
---

# Change Auto sync settings

## Trigger

The Writer turns Sync automatically on or off under Git Sync.

## Outcome

With Auto sync off, a connected notebook syncs only when the Writer asks; with it on, automatic runs resume on opening, periodically and on leaving.
