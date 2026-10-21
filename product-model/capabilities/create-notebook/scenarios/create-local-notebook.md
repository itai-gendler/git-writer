---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
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
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookDialog.kt
---

# Create and activate a local notebook

## Trigger

The Writer supplies a notebook name and, on desktop, a destination.

## Outcome

The new local notebook is active and its files are ready to browse.
