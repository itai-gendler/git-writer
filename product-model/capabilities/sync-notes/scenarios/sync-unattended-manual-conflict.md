---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: condition
  text: Auto sync is enabled and a connected notebook has opened, reached its ten-minute interval, or is leaving
    the foreground.
  entities:
  - entity: settings
    effect: reads
    facts:
    - Auto sync
  - entity: notebook
    effect: reads
    facts:
    - Remote URL
    - Password or token
  unattended: true
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product starts notebook synchronization and saves the open note.
  entities:
  - entity: notebook
    effect: changes
    from: Ready
    to: Syncing
    facts:
    - Sync status
  - entity: note
    effect: changes
    facts:
    - Content
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: condition
  text: The settings select manual conflict resolution.
  entities:
  - entity: settings
    effect: reads
    facts:
    - Conflict strategy
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product leaves the notebook in conflict and presents the pending version choices.
  entities:
  - entity: notebook
    effect: changes
    from: Syncing
    to: Conflict
    facts:
    - Sync status
    - Conflicted files
  contexts:
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt#JGitSyncRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.ios.kt#LibGit2SyncRepositoryImpl
---

# Show conflicts from an automatic run

## Trigger

An automatic sync encounters conflicts while the resolution setting is Manual.

## Outcome

The unresolved paths are presented when the Writer is in the editor; version choices remain pending.
