---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer enters search text for the note.
  entities:
  - entity: note
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product presents matching note text and lets the Writer move through the matches.
  entities:
  - entity: note
    effect: reads
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/editor_find/MarkdownFindState.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/MarkdownEditor.kt
---

# Find in note

## Trigger

The Writer enters search text for the note.

## Outcome

The Product presents matching note text and lets the Writer move through the matches.

## Edge cases

- An empty query or a query with no match returns no matches.
- Next and previous wrap through the matches. Search state resets when the selected file changes.
