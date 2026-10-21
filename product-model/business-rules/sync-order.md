---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Sync status
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt#JGitSyncRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.ios.kt#LibGit2SyncRepositoryImpl
---

# Synchronization commits local changes before integrating remote changes

A sync saves the loaded editable file, stages additions, modifications and deletions, commits changes if needed, integrates remote changes and pushes outgoing commits. A conflict stops the ordinary push path.
