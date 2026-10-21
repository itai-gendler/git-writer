---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer enters a name, the repository URL and credentials and, on desktop, chooses a destination.
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
  text: The Product validates remote access, clones the notebook and imports its notes, folders and images.
  entities:
  - entity: notebook
    effect: creates
    to: Ready
    facts:
    - Name
    - Directory
    - Remote URL
    - Username
    - Password or token
    - Active
    - Open files
    - Active file
    - Sync status
    - Conflicted files
    - Network status
  - entity: note
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
    - Content
  - entity: folder
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
  - entity: image
    effect: creates
    with: notebook
    facts:
    - Name
    - Path
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::add-notebook
    android:
      place: android::add-notebook
    ios:
      place: ios::add-notebook
- kind: product
  text: The Product carries the Writer to the notebook files.
  entities:
  - entity: notebook
    effect: changes
    facts:
    - Active
    - Active file
    - Open files
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
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

# Clone and activate a remote notebook

## Trigger

The Writer supplies a name, repository URL, username and password or token for a repository containing notes, folders and images.

## Outcome

The clone is registered and active; its local files can be browsed.
