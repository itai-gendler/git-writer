---
appliesTo:
- type: entity
  id: notebook
  effect: removes
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
permits:
- actors:
  - writer
---

# The Writer deletes local notebooks

The Writer deletes registered notebooks and their contained local files.
