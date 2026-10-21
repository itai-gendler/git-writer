---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses All local or All remote.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Conflicted files
  actor: writer
  contexts: &id001
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
- kind: product
  text: The Product reports that the files could not be resolved and records the sync as failed.
  actor: writer
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Sync failed
    facts:
    - Sync status
  contexts: *id001
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/git_sync/ui/GitConflictResolveDialog.kt
- kind: code
  role: implementation
  target: shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt#JGitSyncRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.ios.kt#LibGit2SyncRepositoryImpl
---

# Report failure to resolve all files

## Trigger

Applying one side to every remaining conflict fails.

## Outcome

The Product reports the failure and the sync status shows it failed; nothing is pushed.
