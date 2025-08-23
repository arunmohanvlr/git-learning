# Git Stash

`git stash` is used to temporarily save uncommitted changes (both staged and unstaged) so you can work on something else or switch branches without committing. Later, you can reapply the stashed changes.

---

## 🔹 Basic Usage

**Stash current changes (modern way):**
```bash
git stash push -m "WIP: update login form"
```

**(Deprecated) Older syntax:**
```bash
git stash save -m "WIP: update login form"
```

**List all stashes:**
```bash
git stash list
```

**Reapply the latest stash and drop it:**
```bash
git stash pop
```

**Apply a specific stash without dropping it:**
```bash
git stash apply stash@{2}
```

**Drop a specific stash:**
```bash
git stash drop stash@{2}
```

**Clear all stashes:**
```bash
git stash clear
```

---

## 🔹 When to Use Git Stash

1. **Switching branches quickly**
   ```bash
   git stash
   git checkout hotfix/urgent-bug
   git checkout feature/my-work
   git stash pop
   ```

2. **Pulling updates but you have local changes**
   ```bash
   git stash
   git pull --rebase
   git stash pop
   ```

3. **Testing something temporarily**
   - Stash current work, experiment, then return.

4. **Keep working directory clean for builds/tests**
   - Stash uncommitted changes, run tests, then reapply.

---

## 🔑 Key Takeaways
- `git stash` = **temporary shelf** for uncommitted changes.
- Prefer `git stash push -m "message"` (instead of deprecated `save -m`).
- Use labels (`-m`) to remember what each stash is.
- Don’t forget to reapply with `pop` or `apply` after stashing.
