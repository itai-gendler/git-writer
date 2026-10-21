---
appliesTo:
- type: entity
  id: note
  effect: changes
  facts:
  - Content
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
---

# Note content is saved as Markdown

Editing operations save ordered Markdown blocks separated by blank lines. Local saving is independent of a remote Git connection.
