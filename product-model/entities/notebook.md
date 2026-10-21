---
relations:
- entity: note
  verb: contains
  cardinality: one-to-many
- entity: folder
  verb: contains
  cardinality: one-to-many
- entity: image
  verb: contains
  cardinality: one-to-many
domain: notebooks
references:
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/notebooks_management/data/NotebookRepositoryImpl.kt#NotebookRepositoryImpl
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorScreenViewModel.kt#EditorViewModel
- kind: code
  role: implementation
  target: shared/src/commonMain/kotlin/dev/jotalac/feature/editor/ui/EditorSyncController.kt#EditorSyncController
---

# Notebook

A named local Git repository with optional remote synchronization and its current working context.

## Information kept

- **Name** — The notebook name shown in the notebook list.
- **Directory** — The local folder containing its files and Git repository.
- **Remote URL** — The connected repository address, or no remote.
- **Username** — The username used with the repository host.
- **Password or token** — The credential supplied for repository operations.
- **Active** — Whether this is the currently selected notebook.
- **Open files** — The current session’s file selections, including empty tabs and remembered per-file scroll positions.
- **Active file** — The file currently presented, remembered between launches.
- **Sync status** — The current operation result or pending conflict.
- **Conflicted files** — The relative paths that require a version choice.
- **Network status** — The observed network or remote reachability, separate from the Git operation result.

## States

### Local

No remote synchronization is configured.

### Ready

A connected notebook is idle after configuration, activation, successful synchronization, or an aborted merge.

### Syncing

A synchronization operation is in progress.

### Conflict

A merge has files awaiting resolution.

### Sync failed

The last synchronization or final push failed.
