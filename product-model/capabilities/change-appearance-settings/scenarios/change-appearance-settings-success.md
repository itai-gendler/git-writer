---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses a theme mode, accent color, font family or editor width.
  entities:
  - entity: settings
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::appearance
    android:
      place: android::appearance
    ios:
      place: ios::appearance
- kind: product
  text: The Product saves the appearance preference and applies it.
  entities:
  - entity: settings
    effect: changes
    facts:
    - Appearance
  actor: writer
  contexts:
    desktop:
      place: desktop::appearance
    android:
      place: android::appearance
    ios:
      place: ios::appearance
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
- kind: code
  role: implementation
  target: shared/src/androidMain/kotlin/dev/jotalac/feature/settings/platform/UseDynamicColorSetting.android.kt
---

# Change appearance settings

## Trigger

The Writer changes an appearance preference.

## Outcome

The app uses the chosen appearance, and keeps it on this installation.

## Edge cases

- System dynamic color is offered on Android 12 or later.
