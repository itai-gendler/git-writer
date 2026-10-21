---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Open files
  - Active file
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/data/ActiveNotebookManager.kt#ActiveNotebookManager
---

# The editor retains at least one file selection

Closing the last tab creates an empty selection. Changing notebooks resets the open tabs; the active notebook and file are remembered across launches, while the entire tab list is session-only.
