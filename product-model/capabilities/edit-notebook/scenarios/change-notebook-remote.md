---
kind: alternate
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer edits the notebook connection.
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
  text: The Product validates changed credentials and saves the notebook details.
  entities:
  - entity: notebook
    effect: changes
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

# Change an existing remote connection

## Trigger

The Writer changes saved remote details.

## Outcome

Validated connection details replace the previous ones.
