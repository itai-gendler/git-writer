---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects the note.
  entities:
  - entity: note
    effect: reads
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
  capability: open-file
- kind: product
  text: The Product presents the note and remembers the notebook’s active file.
  entities:
  - entity: note
    effect: reads
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
  capability: open-file
- kind: actor
  text: The Writer changes the open note’s Markdown text.
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
  capability: edit-note
- kind: product
  text: The Product changes the note content and saves it locally after the editing pause.
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
  capability: edit-note
---

# Open a note and write in it

## Trigger

The Writer selects a Markdown file from the notebook files.

## Outcome

The file is opened in the editor and its changed content is saved locally.
