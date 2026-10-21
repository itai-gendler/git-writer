---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer clears the remote credentials and saves.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::edit-notebook
    android:
      place: android::edit-notebook
    ios:
      place: ios::edit-notebook
- kind: product
  text: The Product removes the notebook remote connection and keeps its local files.
  entities:
  - entity: notebook
    effect: changes
    from: Ready
    to: Local
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

# Clear remote credentials

## Trigger

The Writer clears the remote credentials and saves.

## Outcome

The Product removes the notebook remote connection and keeps its local files.
