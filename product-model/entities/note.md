---
domain: editor
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorBlocksState.kt#EditorBlocksState
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
---

# Note

A Markdown file whose text can be edited as blocks and rendered as Markdown.

## Information kept

- **Name** — The filename, including its Markdown extension.
- **Path** — Its current location in the notebook.
- **Content** — Markdown text, including ordered blocks, task markers, links and image size annotations.
