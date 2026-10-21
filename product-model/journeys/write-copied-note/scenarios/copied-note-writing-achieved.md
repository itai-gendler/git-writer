---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer selects the note to duplicate.
  entities:
  - entity: note
    effect: reads
    as: source
    facts:
    - Name
    - Path
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: duplicate-note
- kind: product
  text: The Product reads the source note and creates the copied note.
  entities:
  - entity: note
    effect: reads
    as: source
    facts:
    - Content
  - entity: note
    effect: creates
    as: copy
    facts:
    - Name
    - Path
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: duplicate-note
- kind: product
  text: The Product opens the copied note.
  entities:
  - entity: note
    effect: reads
    as: copy
    facts:
    - Name
    - Path
    - Content
  - entity: notebook
    effect: changes
    facts:
    - Active file
    - Open files
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
  capability: duplicate-note
- kind: actor
  text: The Writer changes the open note’s Markdown text.
  entities:
  - entity: note
    effect: reads
    facts: []
    as: copy
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
  capability: edit-note
- kind: product
  text: The Product changes the note content and saves it locally after the editing pause.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
    as: copy
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
  capability: edit-note
---

# Duplicate a note and write in the copy

## Trigger

The Writer duplicates a note.

## Outcome

The copied note is opened and can be edited independently.
