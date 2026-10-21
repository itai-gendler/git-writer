---
kind: primary
routes:
  desktop: Desktop
steps:
- kind: actor
  text: The Writer chooses to add a word marked as misspelled to the dictionary.
  entities:
  - entity: note
    effect: reads
    facts:
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
- kind: product
  text: The Product stops marking that word in the open block and passes it to the operating system's spelling dictionary.
  entities: []
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

# Add a word to the dictionary

## Trigger

The desktop Writer opens the spelling suggestions on a marked word and chooses to add it to the dictionary.

## Outcome

The word is no longer marked in the block being edited, and the operating system's spelling dictionary is asked to accept it. The note's text is unchanged.
