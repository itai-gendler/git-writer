---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Conflicted files
- type: entity
  id: settings
  facts:
  - Conflict strategy
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

# Conflict resolution keeps a whole chosen file version

A manual choice applies to one file or every remaining file. The local or remote preference selects the complete file version; the final resolved file completes the merge commit and push.
