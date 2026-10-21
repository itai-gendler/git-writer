---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer requests a new tab.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product saves the current note, adds an empty selection to the notebook and clears the active file.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: notebook
    effect: changes
    facts:
    - Open files
    - Active file
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/EditorTabsRow.kt
---

# New tab

## Trigger

The Writer requests a new tab.

## Outcome

The Product saves the current note, adds an empty selection to the notebook and clears the active file.
