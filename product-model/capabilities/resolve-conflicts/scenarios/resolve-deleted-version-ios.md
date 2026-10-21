---
kind: alternate
routes:
  ios: iOS
steps:
- kind: actor
  text: The Writer chooses the deleted side for the conflicting path.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Conflicted files
  actor: writer
  contexts:
    ios:
      place: ios::conflicts
- kind: product
  text: The Product removes the note and completes the resolved notebook merge.
  entities:
  - entity: note
    effect: removes
  - entity: notebook
    effect: changes
    from: Conflict
    to: Ready
    facts:
    - Conflicted files
    - Sync status
  actor: writer
  contexts:
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

# Keep the deleted side of an iOS conflict

## Trigger

An iOS file conflict includes a deletion on the side the Writer selects.

## Outcome

The file is deleted locally and staged as resolved; the final resolved path completes the merge and push.
