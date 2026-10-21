---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer requests a new Markdown file.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: add-note
- kind: product
  text: The Product creates the note with an unused untitled name.
  entities:
  - entity: note
    effect: creates
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
  capability: add-note
- kind: product
  text: The Product opens the note in the editor.
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
  capability: add-note
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

# Add a note and write in it

## Trigger

The Writer adds a note.

## Outcome

The new note is opened and contains the Writer’s text.
