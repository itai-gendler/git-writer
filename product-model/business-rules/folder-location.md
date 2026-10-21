---
appliesTo:
- type: entity
  id: folder
  effect: changes
  facts:
  - Path
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
---

# A folder cannot be moved into itself or its descendants

Move operations preserve an acyclic folder hierarchy.
