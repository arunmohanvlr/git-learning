# Git: Going Back in Time

Git allows developers to revisit and restore earlier states of a project. This is useful for undoing mistakes, testing older versions, or recovering lost work.

---

## 1. Viewing History
```bash
git log --oneline
```
Shows the list of commits with unique commit hashes. These hashes are the keys to travel back in time.

---

## 2. Checking Out Old Versions
```bash
git checkout <commit-hash>
```
Moves your working directory to the state at a past commit. This is a **detached HEAD** state, meaning you’re not on a branch.

Return to present:
```bash
git checkout main
```

---

## 3. Reverting a Commit (Safe Way)
```bash
git revert <commit-hash>
```
Creates a new commit that undoes the changes from the selected commit. Keeps history intact and is safe for shared repos.

---

## 4. Resetting to an Old Commit (Rewrite History)
```bash
git reset --hard <commit-hash>
```
Moves branch pointer back, erasing commits after that point. Dangerous if changes were already pushed.

Safer alternative:
```bash
git reset --soft <commit-hash>
```
Keeps changes staged for recommit.

---

## 5. Using Tags for Versions
```bash
git tag v1.0 <commit-hash>
git checkout v1.0
```
Tags mark important commits for easy return.

---

## 6. Time Travel Workflow Example
1. View history: `git log --oneline`  
2. Pick commit: `a1b2c3d`  
3. Checkout: `git checkout a1b2c3d`  
4. Return: `git checkout main`

---

### 🔑 Key Takeaway
- **`git checkout`** → Safely explore old commits.  
- **`git revert`** → Undo commits without altering history.  
- **`git reset`** → Rewrite history (use with caution).  
- **Tags** → Human-readable way to revisit versions.
