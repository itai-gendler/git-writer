---
kind: alternate
routes:
  android: Android
  ios: iOS
steps:
- kind: actor
  text: The Writer captures a photograph.
  entities: []
  actor: writer
  contexts:
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

# Add a camera image

## Trigger

The Writer captures an image with the mobile camera picker.

## Outcome

The image is saved in the notebook and referenced by the note.

## Edge cases

- Cancellation without an image leaves the content unchanged.
