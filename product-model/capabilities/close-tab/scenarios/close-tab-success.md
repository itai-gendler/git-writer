---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer closes a tab.
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
  text: The Product saves the note and removes that selection from the notebook’s open files.
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
---

# Close tab

## Trigger

The Writer closes a tab.

## Outcome

The Product saves the note and removes that selection from the notebook’s open files.

## Edge cases

- Closing the active selection activates the next selection at that position, or the preceding one.
- Closing the only selection replaces it with a fresh empty selection.
