---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer edits the notebook name.
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
  text: The Product changes the notebook name and directory and updates the active file location.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Name
    - Directory
    - Active file
  - entity: note
    effect: changes
    facts:
    - Path
  - entity: folder
    effect: changes
    facts:
    - Path
  - entity: image
    effect: changes
    facts:
    - Path
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

# Rename a notebook

## Trigger

The Writer changes the notebook name and saves.

## Outcome

The name and directory are updated and an active file under the old path follows the renamed directory.

## Edge cases

- Duplicate names or an occupied destination prevent the rename.
