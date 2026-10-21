---
availability:
- place: desktop
- place: android
- place: ios
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/editor_find/MarkdownFindState.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/MarkdownEditor.kt
domain: editor
---

# Find in note

Find case-insensitive literal text across the current note’s Markdown blocks and visit matches in either direction.
