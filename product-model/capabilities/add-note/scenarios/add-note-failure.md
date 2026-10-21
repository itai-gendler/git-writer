---
kind: edge
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer requests a new Markdown file.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
- kind: product
  text: The Product reports why the file could not be created.
  entities: []
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
---

# Report failure to create a note

## Trigger

There is no active notebook or the filesystem cannot create the file.

## Outcome

The Product reports the failure and no new note is opened.
