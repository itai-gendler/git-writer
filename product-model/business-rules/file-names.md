---
appliesTo:
- type: entity
  id: note
  facts:
  - Name
  - Path
- type: entity
  id: folder
  facts:
  - Name
  - Path
- type: entity
  id: image
  facts:
  - Name
  - Path
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
---

# File operations preserve distinct filesystem names

New notes gain a free numerical suffix rather than replacing a same-named file. Rename and move reject occupied destinations. Renaming retains a file extension when it was omitted.
