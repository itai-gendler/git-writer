---
appliesTo:
- type: entity
  id: settings
  facts:
  - Auto sync
- type: entity
  id: notebook
  facts:
  - Sync status
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
---

# Automatic sync waits for a pause in typing

Automatic sync runs on opening a connected notebook, then at ten-minute intervals, and on leaving. Periodic and opening runs wait for a three-second typing pause; leaving requests a final sync directly.
