---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer browses the active notebook’s files.
  entities:
  - entity: notebook
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
- kind: product
  text: The Product presents folders before files, ordered by name without case sensitivity.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Name
    - Directory
  - entity: note
    effect: reads
    facts:
    - Name
    - Path
  - entity: folder
    effect: reads
    facts:
    - Name
    - Path
  - entity: image
    effect: reads
    facts:
    - Name
    - Path
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/utils/FileUtils.kt
---

# Browse files

## Trigger

The Writer browses the active notebook’s files.

## Outcome

The Product presents folders before files, ordered by name without case sensitivity.

## Edge cases

- Hidden entries are omitted from the tree.
- The tree includes Markdown notes and supported image types; empty notebooks show no files.
- The tree refreshes after file operations, successful sync, and return of window focus.
