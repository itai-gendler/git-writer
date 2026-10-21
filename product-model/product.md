---
id: git-writer
summary: Cross-platform Markdown notebooks synchronized through Git repositories.
limitations:
- Notes are Markdown files in local Git-backed notebooks.
- Repository hosting and repository accounts are supplied by the writer’s Git host.
- Mobile notebooks are created or cloned in app-managed storage; opening an existing folder is a desktop operation.
- Conflict recovery chooses a whole local or remote file version, individually or for every conflicting file.
languages:
- en-US
- es-ES
- cs-CZ
- de-DE
- zh-CN
references:
- kind: doc
  role: intent
  target: README.md
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/ui/create_notebook/CreateNotebookDialog.kt
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/core/domain/AppLanguage.kt
---

# Git Writer

A minimalistic, cross-platform note-taking app that uses Git repositories to keep Markdown notes version-controlled and synchronized across devices. Writers keep local notebooks, edit Markdown and images, and connect notebooks to their own Git repositories from Linux, macOS, Windows, Android, or iOS.

## Intent

Keep Markdown notes version-controlled and synchronized across devices through Git repositories, in a minimalistic note-taking app.
