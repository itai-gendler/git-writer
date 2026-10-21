---
appliesTo:
- type: entity
  id: notebook
  effect: creates
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
permits:
- actors:
  - writer
---

# The Writer creates notebook registrations

The Writer creates, clones or opens a directory to register a notebook on this device.
