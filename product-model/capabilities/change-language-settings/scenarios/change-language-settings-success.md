---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses the app language.
  entities:
  - entity: settings
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::language
    android:
      place: android::language
    ios:
      place: ios::language
- kind: product
  text: The Product saves the app language and shows the app in it.
  entities:
  - entity: settings
    effect: changes
    facts:
    - App language
  actor: writer
  contexts:
    desktop:
      place: desktop::language
    android:
      place: android::language
    ios:
      place: ios::language
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

# Change language settings

## Trigger

The Writer chooses English, Spanish, Czech, German or Chinese as the app language.

## Outcome

The app is shown in the chosen language; English is used until another is chosen.
