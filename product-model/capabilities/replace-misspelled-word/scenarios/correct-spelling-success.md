---
kind: primary
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer chooses a spelling suggestion for a word.
  entities: []
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
- kind: product
  text: The Product replaces that word in the note content.
  entities:
  - entity: note
    effect: changes
    facts:
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
references:
- kind: code
  role: implementation
  target: shared/src/jvmMain/kotlin/dev/jotalac/feature/editor/ui/spellcheck/Spellcheck.jvm.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/active_block/ActiveEditorBlock.kt
---

# Correct spelling

## Trigger

The Writer chooses a spelling suggestion for a word.

## Outcome

The Product replaces that word in the note content.

## Edge cases

- If the dictionary is unavailable, the product presents no misspellings or suggestions.
- Chinese is not offered as a separate spelling-language choice.
