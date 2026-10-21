---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer opens the notebook list.
  entities:
  - entity: notebook
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::notebooks
    android:
      place: android::notebooks
    ios:
      place: ios::notebooks
- kind: product
  text: The Product presents each notebook’s name and directory, or the empty list.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
    - Active
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/list_notebooks/NotebookListViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
---

# Browse notebooks

## Trigger

The Writer opens the notebook list.

## Outcome

The Product presents each notebook’s name and directory, or the empty list.
