---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses Manual merge, or Auto merge with a preference for local or remote changes.
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
  text: The Product saves the conflict strategy for this installation.
  entities:
  - entity: settings
    effect: changes
    facts:
    - Conflict strategy
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

# Change conflict resolution settings

## Trigger

The Writer changes the resolution strategy under Git Sync.

## Outcome

The next sync that meets conflicts either stops for the Writer's choices or keeps every local or every remote version.
