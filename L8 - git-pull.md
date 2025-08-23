# Git Pull

`git pull` updates your current branch from its remote tracking branch. It runs **fetch** first, then integrates via **merge** (default) or **rebase**.

---

## Basics
**Default (merge):**
```bash
git pull
# equivalent to: git fetch && git merge origin/<current-branch>
```
**Explicit remote/branch:**
```bash
git pull origin main
```
**Rebase instead of merge:**
```bash
git pull --rebase
```
**Fast‑forward only (no merge commits):**
```bash
git pull --ff-only
```

---

## Before You Pull
- Ensure a clean working tree: commit or stash local edits.
```bash
git stash push -m "wip"
git pull --rebase
git stash pop
```

- Verify upstream:
```bash
git branch -vv
# Set if missing:
git branch --set-upstream-to origin/main
```

---

## Scenarios

### A) Fast‑forward (no local commits)
- Your branch is behind remote; no local commits.
- Result: pointer just moves forward (no conflicts).
```bash
git pull --ff-only
```

### B) Merge (both sides changed)
- You and remote have commits.
- Result: auto‑merge or a merge commit; conflicts possible.
```bash
git pull
# resolve conflicts if prompted, then commit the merge
```

### C) Rebase workflow (linear history)
- Replay your local commits on top of remote.
```bash
git pull --rebase
# if conflicts arise, resolve, then:
git add <files>
git rebase --continue
```
- Set once:
```bash
git config --global pull.rebase true
# or per-branch:
git config branch.<name>.rebase true
```

### D) Unrelated histories
- Two independent histories (rare).
```bash
git pull --allow-unrelated-histories
# resolve conflicts, then commit
```

### E) Local uncommitted changes
1) Tracked edits present → stash/commit first.  
2) Untracked files would be overwritten → move/rename/remove them.
```bash
git stash
git pull
git stash pop
```

### F) Submodules
```bash
git pull --recurse-submodules
# or after pull:
git submodule update --init --recursive
```

---

## Resolving Conflicts

### Merge conflicts
Markers appear in files:
```diff
<<<<<<< HEAD
your changes
=======
their changes
>>>>>>> origin/main
```
Steps:
```bash
# edit files to the desired content
git add <files>
git commit   # completes the merge
```
Abort merge:
```bash
git merge --abort
```

### Rebase conflicts
```bash
# fix files
git add <files>
git rebase --continue
# skip problematic commit:
git rebase --skip
# abort and go back:
git rebase --abort
```

---

## Common Options & Safety

```bash
git pull --ff-only        # refuse to create a merge commit
git pull --rebase         # keep history linear
git pull --no-rebase      # force merge if configured to rebase
git pull --no-commit      # merge but don't auto-commit (inspect first)
git pull --squash         # squash fetched changes (no merge commit)
```

Editor hint (for merge messages):
```bash
git config --global core.editor "code --wait"
```

---

## Quick Recipes

**Safe linear update:**
```bash
git fetch
git rebase origin/main
```

**Classic update with merge:**
```bash
git pull
```

**Pull with local work in progress:**
```bash
git stash push -m "wip"
git pull --rebase
git stash pop
```

**Ensure only fast‑forward:**
```bash
git pull --ff-only
```

---

### TL;DR
- `git pull = fetch + merge` (or `--rebase`).
- Keep working tree clean to avoid conflicts.
- On conflicts: resolve → `git add` → `git commit` (merge) or `git rebase --continue` (rebase).
