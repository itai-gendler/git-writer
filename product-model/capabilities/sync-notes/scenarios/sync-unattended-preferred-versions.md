---
kind: alternate
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
  text: The settings choose automatic local or remote conflict resolution.
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
  text: The Product applies the preferred versions, commits the resolution and pushes the notebook changes.
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Ready
    facts:
    - Sync status
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: image
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

# Resolve conflicts during an automatic run

## Trigger

An automatic sync encounters conflicts with a local or remote preference selected.

## Outcome

The configured whole-file versions are applied, committed and pushed.
