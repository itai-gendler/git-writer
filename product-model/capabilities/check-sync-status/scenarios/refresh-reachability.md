---
kind: alternate
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: condition
  text: A remote reachability check is due.
  entities: []
  unattended: true
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product checks the remote host and updates notebook network status.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Network status
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

# Refresh remote reachability

## Trigger

The editor becomes visible, the remote changes, or the network monitor reports a change.

## Outcome

The observed reachability is refreshed independently of whether Git has remote commits.

## Edge cases

- On mobile, an operating-system offline result is distinguished from a host that cannot be reached.
- Active sync, pending conflict, and absent configuration take precedence over the connectivity display.
