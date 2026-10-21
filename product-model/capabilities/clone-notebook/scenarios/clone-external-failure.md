---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer requests the clone.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
- kind: product
  text: The Product reports the remote access or cloning failure.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookDialog.kt
- kind: code
  role: implementation
  target: shared/src/jvmAndAndroidMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.jvm.kt#JGitSyncRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/iosMain/kotlin/dev/jotalac/feature/git_sync/data/GitSyncRepositoryImpl.ios.kt#LibGit2SyncRepositoryImpl
---

# Report rejected access or clone failure

## Trigger

The host cannot validate the credentials, or cloning fails.

## Outcome

No notebook is registered; the new clone directory is removed and the Writer receives an error.
