---
kind: primary
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer chooses Copy path for a note.
  entities:
  - entity: note
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::files
- kind: product
  text: The Product copies the note path to the clipboard and reports completion.
  entities:
  - entity: note
    effect: reads
    facts:
    - Path
  actor: writer
  contexts:
    desktop:
      place: desktop::files
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarContent.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/components/file_tree/context_menu/ItemContextMenu.kt
---

# Copy item path

## Trigger

The Writer chooses Copy path for a note.

## Outcome

The Product copies the note path to the clipboard and reports completion.

## Edge cases

- The same operation is available for folders and image files.
