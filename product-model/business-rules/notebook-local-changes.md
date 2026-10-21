---
appliesTo:
- type: entity
  id: notebook
  effect: changes
  facts:
  - Name
  - Directory
  - Remote URL
  - Username
  - Password or token
  - Active
  - Active file
  - Open files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/NetworkUtils.kt
permits:
- actors:
  - writer
---

# The Writer changes local notebook details

The Writer changes a notebook’s name, connection and local working selection.
