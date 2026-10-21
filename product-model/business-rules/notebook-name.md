---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Name
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/edit_notebook/EditNotebookViewModel.kt
---

# Notebook names are nonempty and unique

New and edited notebook names must be nonempty and unique among registered notebooks. Opening another folder with the same display name assigns a free numerical suffix.
