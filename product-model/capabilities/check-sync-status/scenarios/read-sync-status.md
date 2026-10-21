---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer reads the notebook sync and network status.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Sync status
    - Network status
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
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
---

# Read synchronization and reachability status

## Trigger

The Writer inspects the active notebook’s sync status.

## Outcome

The Product distinguishes a configured idle connection, active sync, conflict, failed sync, absent connection, offline device or unreachable host.
