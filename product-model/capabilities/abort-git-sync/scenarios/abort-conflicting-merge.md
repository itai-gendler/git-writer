---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer aborts the conflicting notebook merge.
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
  text: The Product resets the notebook to the pre-pull commit and clears the conflict list.
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Ready
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

# Abort conflict recovery

## Trigger

The Writer aborts sync or dismisses the conflict choices.

## Outcome

The conflicting merge is abandoned and the conflict list clears. Local edits committed before pulling remain in that commit.

## Edge cases

- Outside a merge, abort does not reset the working files.
