---
domain: editor
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
---

# Image

An image file stored in a notebook and displayed independently or referenced by Markdown.

## Information kept

- **Name** — The image filename.
- **Path** — Its location in the notebook.
- **Content** — The image data saved or displayed.
