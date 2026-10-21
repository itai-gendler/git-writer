---
kind: alternate
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer changes the spelling-language setting.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::language
- kind: product
  text: The Product saves the settings for spelling.
  entities:
  - entity: settings
    effect: changes
    facts:
    - Spell check language
  actor: writer
  contexts:
    desktop:
      place: desktop::language
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

# Choose a separate spelling language

## Trigger

The desktop Writer selects a spelling language or Same as app language.

## Outcome

The selected dictionary language is used for subsequent spell checks.
