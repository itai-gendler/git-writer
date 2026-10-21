---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer selects an item and its destination.
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
  text: The Product moves the selected item and follows an active file to its new location.
  entities:
  - entity: note
    effect: changes
    facts:
    - Path
  - entity: notebook
    effect: changes
    facts:
    - Active file
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
---

# Move a note

## Trigger

The Writer moves the selected item to another folder in the same notebook.

## Outcome

The Product moves the selected item and follows an active file to its new location.

## Edge cases

- Moving into the current directory leaves the item unchanged.
- A same-named destination or a folder moved into itself or its descendants is refused.
