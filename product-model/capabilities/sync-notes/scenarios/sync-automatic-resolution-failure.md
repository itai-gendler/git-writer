---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer requests synchronization of the notebook.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Sync status
  actor: writer
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
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: condition
  text: The settings select automatic conflict resolution.
  actor: writer
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
  text: The pull meets files changed on both sides, leaving the notebook in conflict.
  actor: writer
  entities:
  - entity: notebook
    effect: changes
    from: Syncing
    to: Conflict
    facts:
    - Sync status
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product reports failure to resolve the notebook conflicts.
  actor: writer
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Sync failed
    facts:
    - Sync status
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

# Report failure to apply the configured conflict preference

## Trigger

A synchronization encounters conflicts and applying the configured local or remote preference fails.

## Outcome

The Product reports failure to resolve conflicts and records sync failure.
