# Projektregeln für Claude / KI-Agenten

## Commit-Attribution

**Keine Claude-/Anthropic-Attribution in Commits.** Damit "Claude" nicht als
Contributor im Repository erscheint, dürfen Commit-Messages in diesem Repo
folgende Trailer **nicht** enthalten:

- `Co-authored-by: Claude <noreply@anthropic.com>` (oder ähnliche Anthropic-Co-Authors)
- `Claude-Session: ...`

Diese Regel gilt für alle künftigen Commits, unabhängig von Standard-Vorgaben
des Tools.

### Optionale technische Absicherung

Im Repo liegt der Hook `.githooks/commit-msg`, der diese Trailer automatisch
entfernt. Einmalig pro Klon aktivieren:

```sh
git config core.hooksPath .githooks
```
