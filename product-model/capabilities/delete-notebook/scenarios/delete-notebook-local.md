---
kind: primary
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
  contexts:
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
- kind: product
  text: The Product removes the notebook and its local contents.
  entities:
  - entity: notebook
    effect: removes
    from: Local
  - entity: note
    effect: removes
    with: notebook
  - entity: folder
    effect: removes
    with: notebook
  - entity: image
    effect: removes
    with: notebook
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/list_notebooks/NotebookListViewModel.kt
---

# Delete a local notebook

## Trigger

The Writer deletes a saved notebook.

## Outcome

The local notebook and its files are removed; an active deleted notebook is cleared. The remote repository is not deleted.
