---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer resolves the remaining conflicting versions.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Conflicted files
  actor: writer
  contexts:
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
- kind: product
  text: The Product commits the resolution but records a failed notebook push.
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Sync failed
    facts:
    - Conflicted files
    - Sync status
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: image
    effect: changes
    facts:
    - Content
  actor: writer
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/git_sync/ui/GitConflictResolveDialog.kt
- kind: code
  role: implementation
  target: shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt#JGitSyncRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.ios.kt#LibGit2SyncRepositoryImpl
---

# Keep a local resolution after a failed push

## Trigger

The version choices resolve the merge but the final push fails.

## Outcome

The conflict list is cleared and the Writer is told that resolution is local but the push failed. A subsequent sync can push it.
