---
actors:
- writer
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/MarkdownEditorState.kt#MarkdownEditorState
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorBlocksState.kt#EditorBlocksState
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/utils/MarkdownTextModificationUtils.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/markdown_rendering/CustomMarkdownComponents.kt
---

# Write from a copied note

## Goal

The Writer duplicates a note.

## Success criterion

The copied note is opened and can be edited independently.
