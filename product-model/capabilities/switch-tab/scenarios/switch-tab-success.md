---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects another tab or moves to the next or previous tab.
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
  text: The Product saves the current note and changes the notebook’s active file to the selected entry.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: notebook
    effect: changes
    facts:
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

# Switch tab

## Trigger

The Writer selects another tab or moves to the next or previous tab.

## Outcome

The Product saves the current note and changes the notebook’s active file to the selected entry.

## Edge cases

- Next and previous wrap across the session’s selections.
- Switching selections restores the selected file’s remembered scroll position for this session.
