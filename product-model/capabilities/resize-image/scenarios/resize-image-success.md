---
kind: primary
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer chooses a size for an image in the note.
  entities:
  - entity: note
    effect: reads
    facts: []
  - entity: image
    effect: reads
    facts: []
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
- kind: product
  text: The Product changes the note image-size annotation while preserving the image data.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: image
    effect: reads
    facts:
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/markdown_rendering/CustomImageComponent.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/markdown_rendering/ImageAlt.kt
---

# Resize image

## Trigger

The Writer chooses a size for an image in the note.

## Outcome

The Product changes the note image-size annotation while preserving the image data.

## Edge cases

- The image must have loaded before its size choices are available.
- Width-only annotations retain proportions; explicit width and height annotations are rendered on all interfaces.
