---
kind: validation
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer submits edited notebook details.
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
  text: The Product reports the connection validation problem.
  entities: []
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

# Reject incomplete or unavailable connection details

## Trigger

The remote form is incomplete, the URL is invalid, or the host rejects access.

## Outcome

The form reports the problem and stays open for correction.
