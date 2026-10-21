---
kind: primary
routes:
  desktop: Desktop
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer supplies picture data for insertion.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
- kind: product
  text: The Product saves the image and inserts its reference in the note.
  entities:
  - entity: image
    effect: creates
    facts:
    - Name
    - Path
    - Content
  - entity: note
    effect: changes
    facts:
    - Content
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
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/data/EditorRepositoryImpl.kt#EditorRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/MarkdownEditor.kt
---

# Add an image to a note

## Trigger

The Writer supplies an image using desktop paste or drop, or the mobile image picker.

## Outcome

The image is saved and the note contains its notebook-root-relative images reference; editing continues after the inserted image.

## Edge cases

- Several images can be inserted together.
- A failed image save reports an error; only successfully saved images are inserted.
