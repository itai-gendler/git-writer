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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/active_block/EditorHistoryManager.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreen.kt
---

# Undo and redo are bounded to the current editor history

The editor retains up to 50 snapshots, groups consecutive typing within 500 milliseconds, and clears redo history when a new recorded edit is made. Recreating the selected note editor starts a new history.
