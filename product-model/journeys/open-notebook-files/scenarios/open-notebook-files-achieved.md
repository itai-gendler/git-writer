---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer selects the notebook.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
  actor: writer
  contexts:
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
  capability: open-notebook
- kind: product
  text: The Product activates the notebook and carries the Writer to its files.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Active
    - Active file
    - Open files
    - Sync status
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: open-notebook
- kind: actor
  text: The Writer browses the active notebook’s files.
  entities:
  - entity: notebook
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: browse-files
- kind: product
  text: The Product presents folders before files, ordered by name without case sensitivity.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
  - entity: note
    effect: reads
    facts:
    - Name
    - Path
  - entity: folder
    effect: reads
    facts:
    - Name
    - Path
  - entity: image
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
  capability: browse-files
---

# Open a saved notebook and browse its files

## Trigger

The Writer opens a saved notebook.

## Outcome

The active notebook’s files can be browsed.
