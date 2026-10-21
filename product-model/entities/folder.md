---
relations:
- entity: note
  verb: contains
  cardinality: one-to-many
- entity: image
  verb: contains
  cardinality: one-to-many
domain: notebooks
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
---

# Folder

A named directory used to organize files within a notebook.

## Information kept

- **Name** — The folder name.
- **Path** — Its location within the notebook.
