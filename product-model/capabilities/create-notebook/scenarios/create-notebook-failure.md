---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer requests initialization in a new directory.
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
  text: The Product reports the initialization failure.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
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

# Report notebook initialization failure

## Trigger

Local repository initialization or registration fails.

## Outcome

The Product reports the failure and removes the new directory created for the unsuccessful operation.
