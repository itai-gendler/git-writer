---
appliesTo:
- type: entity
  id: notebook
  effect: changes
  to: Syncing
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/SyncFloatingButton.kt
permits:
- actors:
  - writer
  when:
  - fact: Remote URL
    present: true
  - fact: Password or token
    present: true
  - fact: Network status
    is-not: Offline
  - fact: Sync status
    is-not: Syncing
- unattended: true
  when:
  - fact: Remote URL
    present: true
  - fact: Password or token
    present: true
  - entity: settings
    fact: Auto sync
    is: true
---

# Synchronization requires a connected notebook

The Writer starts synchronization with a configured remote URL and credential. Manual sync is unavailable during an existing sync or a known offline state. Automatic starts additionally require Auto sync to be enabled.
