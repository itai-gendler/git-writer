---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer enters a new name for the selected item.
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
  text: The Product renames the selected item and follows an active file to its new location.
  entities:
  - entity: note
    effect: changes
    facts:
    - Name
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

# Rename a note

## Trigger

The Writer enters a new name for the selected item.

## Outcome

The Product renames the selected item and follows an active file to its new location.

## Edge cases

- Blank input cancels renaming. An unchanged name is a no-op.
- The existing file extension is retained when omitted from the supplied name.
- An existing destination produces an error.
