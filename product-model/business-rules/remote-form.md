---
appliesTo:
- type: entity
  id: notebook
  facts:
  - Remote URL
  - Username
  - Password or token
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookDialog.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/edit_notebook/EditNotebookViewModel.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/Utils.kt
---

# Remote connections require complete supported connection details

Clone and edit forms require a repository URL ending in .git, a username, and a password or token. Changed remote details are checked with the host before they are saved.
