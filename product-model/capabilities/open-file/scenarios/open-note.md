---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects the note.
  entities:
  - entity: note
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
- kind: product
  text: The Product presents the note and remembers the notebook’s active file.
  entities:
  - entity: note
    effect: reads
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
---

# Open a note

## Trigger

The Writer chooses a file from the active notebook.

## Outcome

The file is active and the editor presents Markdown text for editing and rendered reading.

## Edge cases

- The previously loaded editable content is saved before selecting the next file.
- Selecting an already open file activates its existing selection.
