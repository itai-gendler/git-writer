---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer enters a name, the repository URL and credentials and, on desktop, chooses a destination.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
  capability: clone-notebook
- kind: product
  text: The Product validates remote access, clones the notebook and imports its notes, folders and images.
  entities:
  - entity: notebook
    effect: creates
    to: Ready
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
  - entity: note
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
    - Content
  - entity: folder
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
  - entity: image
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
  capability: clone-notebook
- kind: product
  text: The Product carries the Writer to the notebook files.
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
  capability: clone-notebook
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

# Clone a notebook and browse its files

## Trigger

The Writer clones a remote notebook.

## Outcome

The clone is active and its files are presented.
