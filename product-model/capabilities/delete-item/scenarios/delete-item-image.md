---
kind: alternate
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer deletes the selected item.
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
  text: The Product deletes the selected item and clears the active file if it was removed.
  entities:
  - entity: image
    effect: removes
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

# Delete an image

## Trigger

The Writer deletes the selected item.

## Outcome

The Product deletes the selected item and clears the active file if it was removed.

## Edge cases

- Filesystem failures are reported.
