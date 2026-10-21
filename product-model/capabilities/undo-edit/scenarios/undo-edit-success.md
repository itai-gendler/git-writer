---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses Undo.
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
  text: The Product restores the preceding recorded note content and editing position.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/MarkdownEditorState.kt#MarkdownEditorState
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorBlocksState.kt#EditorBlocksState
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
---

# Undo edit

## Trigger

The Writer chooses Undo.

## Outcome

The Product restores the preceding recorded note content and editing position.

## Edge cases

- With no earlier recorded edit, the content is unchanged.
