---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer enters a name and, on desktop, chooses a destination.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
  capability: create-notebook
- kind: product
  text: The Product creates the notebook and its default asset folder.
  entities:
  - entity: notebook
    effect: creates
    to: Local
    facts:
    - Name
    - Directory
    - Remote URL
    - Username
    - Password or token
    - Active
    - Open files
    - Active file
    - Sync status
    - Conflicted files
    - Network status
  - entity: folder
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
  capability: create-notebook
- kind: product
  text: The Product activates the notebook and carries the Writer to its files.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Active
    - Active file
    - Open files
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
  capability: create-notebook
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

# Create a notebook and browse its files

## Trigger

The Writer creates a local notebook.

## Outcome

The new notebook is active and its contents can be browsed.
