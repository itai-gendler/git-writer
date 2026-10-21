---
availability:
- place: desktop
references:
- kind: code
  role: implementation
  target: shared/src/jvmMain/kotlin/dev/jotalac/feature/editor/ui/spellcheck/Spellcheck.jvm.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/components/active_block/ActiveEditorBlock.kt
domain: editor
---

# Add word to dictionary

Add a word marked as misspelled to the operating system's spelling dictionary on desktop, so the editor stops marking it. The dictionary itself belongs to the operating system.
