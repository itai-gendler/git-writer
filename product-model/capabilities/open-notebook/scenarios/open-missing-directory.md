---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects the notebook.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
  actor: writer
  contexts:
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
- kind: product
  text: The Product reports that its directory no longer exists.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Directory
  actor: writer
  contexts:
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
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

# Report a missing notebook directory

## Trigger

The Writer chooses a notebook whose local folder has disappeared.

## Outcome

Activation fails with an explanatory error; the existing selection remains.
