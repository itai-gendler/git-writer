---
appliesTo:
- type: entity
  id: image
  effect: creates
- type: entity
  id: note
  facts:
  - Content
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/ImageLoaderConfig.kt#resolveImagePath
---

# Inserted images belong to the notebook images directory

Supplied image bytes are saved in the active notebook’s images directory and the note receives an images/ reference resolved from the notebook root.
