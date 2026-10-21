---
appliesTo:
- type: entity
  id: notebook
  effect: removes
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
---

# Deleting a notebook removes its local files

Notebook deletion removes its local directory recursively and clears the active selection if necessary. It does not delete the hosted repository.
