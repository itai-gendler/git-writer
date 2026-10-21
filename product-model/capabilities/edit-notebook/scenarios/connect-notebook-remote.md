---
kind: alternate
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer supplies the notebook remote details.
  entities:
  - entity: notebook
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::edit-notebook
    android:
      place: android::edit-notebook
    ios:
      place: ios::edit-notebook
- kind: product
  text: The Product validates access, configures the remote and saves the notebook connection.
  entities:
  - entity: notebook
    effect: changes
    from: Local
    to: Ready
    facts:
    - Remote URL
    - Username
    - Password or token
    - Sync status
  actor: writer
  contexts:
    desktop:
      place: desktop::edit-notebook
    android:
      place: android::edit-notebook
    ios:
      place: ios::edit-notebook
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/edit_notebook/EditNotebookViewModel.kt
---

# Connect a local notebook to a remote

## Trigger

The Writer enters a repository URL, username and password or token and saves.

## Outcome

The notebook has a validated remote connection and is ready for synchronization.
