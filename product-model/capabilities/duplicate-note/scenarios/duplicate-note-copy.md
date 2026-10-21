---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects the note to duplicate.
  entities:
  - entity: note
    effect: reads
    as: source
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
- kind: product
  text: The Product reads the source note and creates the copied note.
  entities:
  - entity: note
    effect: reads
    as: source
    facts:
    - Content
  - entity: note
    effect: creates
    as: copy
    facts:
    - Name
    - Path
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::files
    android:
      place: android::files
    ios:
      place: ios::files
- kind: product
  text: The Product opens the copied note.
  entities:
  - entity: note
    effect: reads
    as: copy
    facts:
    - Name
    - Path
    - Content
  - entity: notebook
    effect: changes
    facts:
    - Active file
    - Open files
  actor: writer
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
---

# Duplicate and open a note

## Trigger

The Writer duplicates a Markdown note.

## Outcome

A copy with a free name is opened for editing without changing the source.

## Edge cases

- A read or creation failure is reported and no copy is opened.
