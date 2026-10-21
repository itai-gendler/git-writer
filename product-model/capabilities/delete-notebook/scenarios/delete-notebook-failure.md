---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer deletes the notebook.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
  actor: writer
  contexts: &id001
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
- kind: product
  text: The Product reports the failed operation.
  actor: writer
  entities: []
  contexts: *id001
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/list_notebooks/NotebookListViewModel.kt
---

# Report notebook deletion failure

## Trigger

The filesystem or registration removal fails.

## Outcome

The notebook list presents the error; the Product does not report deletion success.
