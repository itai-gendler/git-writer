---
kind: primary
result: achieved
routes:
  desktop: Desktop
  android: Android
  ios: Ios
steps:
- kind: actor
  text: The Writer requests synchronization of the notebook.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Sync status
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
  capability: sync-notes
- kind: product
  text: The Product starts notebook synchronization and saves the open note.
  entities:
  - entity: notebook
    effect: changes
    from: Ready
    to: Syncing
    facts:
    - Sync status
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
  capability: sync-notes
- kind: condition
  text: The settings select manual conflict resolution.
  entities:
  - entity: settings
    effect: reads
    facts:
    - Conflict strategy
  actor: writer
  contexts:
    desktop:
      place: desktop::editor
    android:
      place: android::editor
    ios:
      place: ios::editor
  capability: sync-notes
- kind: product
  text: The Product leaves the notebook in conflict and carries the Writer to the conflict choices.
  entities:
  - entity: notebook
    effect: changes
    from: Syncing
    to: Conflict
    facts:
    - Sync status
    - Conflicted files
  actor: writer
  contexts:
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
  capability: sync-notes
- kind: actor
  text: The Writer selects the final conflicting version or a side for all files.
  entities:
  - entity: notebook
    effect: reads
    facts:
    - Conflicted files
  actor: writer
  contexts:
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
  capability: resolve-conflicts
- kind: product
  text: The Product applies the chosen versions, commits the merge and pushes the notebook.
  entities:
  - entity: notebook
    effect: changes
    from: Conflict
    to: Ready
    facts:
    - Conflicted files
    - Sync status
  - entity: note
    effect: changes
    facts:
    - Content
  - entity: image
    effect: changes
    facts:
    - Content
  actor: writer
  contexts:
    desktop:
      place: desktop::conflicts
    android:
      place: android::conflicts
    ios:
      place: ios::conflicts
  capability: resolve-conflicts
---

# Sync, meet conflicts and resolve them

## Trigger

The Writer requests sync and reaches manual conflict choices.

## Outcome

The conflicts are resolved and the merge is pushed.
