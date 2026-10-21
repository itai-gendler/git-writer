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
- kind: product
  text: The Product commits local notebook changes, merges remote changes, pushes outgoing commits and reloads a
    changed open note.
  entities:
  - entity: notebook
    effect: changes
    from: Syncing
    to: Ready
    facts:
    - Sync status
    - Conflicted files
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

# Synchronize automatically

## Trigger

Auto sync is on, and a connected notebook is opened, has stayed open for ten minutes since its last sync, or is being left (the desktop app quits or the mobile app goes to the background).

## Outcome

Local and remote changes are exchanged without the Writer asking, and an open note the pull changed is reloaded.

## Edge cases

- On opening a connected notebook, automatic sync starts immediately when typing is idle.
- Periodic runs wait ten minutes after the previous run and wait for a three-second typing pause.
- Disabling Auto sync stops periodic runs.
- The final mobile background sync is best effort because the operating system may stop the app.
