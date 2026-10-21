---
availability:
- place: desktop
- place: android
- place: ios
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/NetworkUtils.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenState.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/SyncFloatingButton.kt
domain: git-sync
---

# Check sync status

Read the current Git operation result and the availability of the active notebook’s remote.
