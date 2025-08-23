# Difference between `git pull` and `git pull --rebase`

This note explains what happens with a normal **git pull** (fetch + merge) versus **git pull --rebase** (fetch + rebase), with examples and when to use each.

---

## Quick Definition
- **git pull** → `git fetch` + **merge** the remote branch into your current branch (may create a merge commit).
- **git pull --rebase** → `git fetch` + **rebase** your local commits on top of the remote branch (no merge commit; rewrites your local commit hashes).

---

## Visual Mental Model

**Normal `git pull` (merge)**  
Your branch and the remote both have new commits; Git makes a **merge commit** to combine:
```
A---B---C (your local)
         \
          M---N (remote)
           \
            MC (merge commit created by pull)
```
Resulting history keeps the branching/merging structure.

**`git pull --rebase` (replay your work)**  
Your local commits are **replayed on top** of the remote branch, keeping history linear:
```
A---M---N---B'---C'
```
(`B'` and `C'` are rebased versions of your commits.)

---

## Concrete Example

Starting point:
```bash
git checkout main
# You commit locally
echo "v1" >> app.js && git add app.js && git commit -m "Local: add v1"
echo "v2" >> app.js && git add app.js && git commit -m "Local: add v2"
# Meanwhile, teammates pushed commits to origin/main
```

### A) Normal pull (merge)
```bash
git pull
```
- Git fetches remote changes and **merges** them.
- If both sides changed the same parts, you’ll resolve **merge conflicts** once, then a **merge commit** is created.

### B) Pull with rebase
```bash
git pull --rebase
```
- Git fetches remote changes and **replays** your commits on top.
- If conflicts occur, you resolve them **per commit**, then continue:
```bash
git add <files>
git rebase --continue
```
- No merge commit is created; history is linear.

---

## When to Use Which

**Use normal `git pull` (merge) when:**
- Your team is fine with merge commits in history.
- You want to preserve the exact parallel history and merge context.
- You’re merging work that has meaningful merge points you want to keep.

**Use `git pull --rebase` when:**
- You (or your team) prefer a **clean, linear history** without merge commits.
- You’re updating a **feature branch** from `main` before opening a PR.
- You want `git log` and `git bisect` to be simpler to read.

> ⚠️ Rebase **rewrites local commit hashes**. Avoid rebasing public/shared history that others may already have.

---

## Setup Tips

**Make rebase the default for your pulls (optional):**
```bash
git config --global pull.rebase true
```
Per branch:
```bash
git config branch.<name>.rebase true
```

**Enforce fast‑forward only (safe):**
```bash
git pull --ff-only
```
This refuses to create a merge commit during pull. If not possible, Git stops and you can decide to merge or rebase manually.

---

## Conflict Handling

**During merge (normal pull):**
```bash
git pull
# If conflicts:
#   edit files (look for <<<<<<<, =======, >>>>>>> markers)
git add <files>
git commit     # completes the merge
```
Abort the merge:
```bash
git merge --abort
```

**During rebase (pull --rebase):**
```bash
git pull --rebase
# If conflicts:
#   edit files, then
git add <files>
git rebase --continue
# or skip/abort
git rebase --skip
git rebase --abort
```

---

## TL;DR
- **`git pull`** keeps merge commits → preserves branching context.
- **`git pull --rebase`** keeps history linear → cleaner log, rewritten local hashes.
- Prefer **`--rebase`** on feature branches; use plain **pull** if your team embraces merge commits or you need the merge context.
