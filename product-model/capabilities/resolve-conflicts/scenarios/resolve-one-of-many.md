---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects a local or remote version for one conflicting file.
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
  text: The Product applies the selected file version and removes its notebook conflict entry.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Conflicted files
  - entity: note
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

# Resolve one file while others remain

## Trigger

The Writer selects a side for one of several conflicting paths.

## Outcome

That path is removed from the unresolved list; the remaining paths still require decisions.

## Edge cases

- A file-operation failure is reported and the path remains unresolved.
