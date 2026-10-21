---
kind: primary
result: achieved
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer selects an existing local directory.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
  capability: open-notebook
- kind: product
  text: The Product registers a local notebook for that directory.
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
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
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
  actor: writer
  contexts:
    desktop:
      place: desktop::files
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
  capability: browse-files
---

# Open an existing folder and browse its files

## Trigger

The desktop Writer opens an existing folder.

## Outcome

The registered notebook is active and its files can be browsed.
