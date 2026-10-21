---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Active file
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
---

# The active file follows local rename and move operations

Renaming or moving an active file or an enclosing folder updates its remembered path. Deleting that file or an enclosing folder clears the active selection.
