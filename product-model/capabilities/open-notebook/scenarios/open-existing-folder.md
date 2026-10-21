---
kind: alternate
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
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/list_notebooks/NotebookListViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/data/ActiveNotebookManager.kt#ActiveNotebookManager
---

# Open an existing desktop folder

## Trigger

The Writer selects an existing local directory.

## Outcome

The directory is registered once and active. An existing Git history is preserved; a folder without Git is initialized. Existing Git remote settings do not populate the app’s remote credentials.

## Edge cases

- Opening an already registered directory activates its existing registration instead of creating another.
- A conflicting display name receives a numerical suffix beginning with 2.
- If registration fails, only Git metadata newly initialized by this operation is removed; existing history remains.
