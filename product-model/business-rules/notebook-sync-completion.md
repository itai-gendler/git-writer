---
appliesTo:
- type: entity
  id: notebook
  effect: changes
  to: Ready
- type: entity
  id: notebook
  effect: changes
  to: Conflict
- type: entity
  id: notebook
  effect: changes
  to: Sync failed
- type: entity
  id: notebook
  effect: changes
  to: Local
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
permits:
- actors:
  - writer
- unattended: true
---

# A notebook's sync result comes from the Writer's sync or an automatic one

A sync the Writer starts, or one Auto sync starts, ends the notebook ready, in conflict or failed; clearing the remote credentials returns it to a local notebook.
