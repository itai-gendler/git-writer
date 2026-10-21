---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Network status
  - Sync status
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/NetworkUtils.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/SyncFloatingButton.kt
---

# Remote reachability is distinct from Git synchronization

A responding remote host establishes reachability, not repository authorization or commit freshness. An unreachable host leaves manual retry available; a known offline mobile device disables manual sync.
