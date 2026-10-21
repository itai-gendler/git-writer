---
availability:
- place: desktop
- place: android
- place: ios
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreen.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor_sidebar/ui/SidebarViewModel.kt#EditorSidebarViewModel
domain: editor
---

# Open file

Open a Markdown note or image, reusing an already open selection when possible.
