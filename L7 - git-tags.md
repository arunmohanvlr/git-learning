# Git Tags

Git **tags** are fixed labels that point to a specific commit. They are ideal for **releases** and marking important points in history. Unlike branches, tags **do not move**.

---

## 1) Types of Tags
**Lightweight tag (bookmark)**
```bash
git tag v1.0.0
```
**Annotated tag (recommended for releases)**
```bash
git tag -a v1.0.0 -m "Release v1.0.0"
```
**Signed tag (with GPG)**
```bash
git tag -s v1.0.0 -m "Release v1.0.0 (signed)"
```

---

## 2) Create Tags
**Tag the current commit (HEAD)**
```bash
git tag -a v1.0.1 -m "Release v1.0.1"
```
**Tag a specific commit by hash**
```bash
git tag -a v1.0.1 9fceb02 -m "Tag past commit"
```
**Add an annotated tag with a message editor**
```bash
git tag -a v1.0.1
```

---

## 3) List & Inspect Tags
**List all tags**
```bash
git tag
```
**Filter tags (e.g., all v1.x)**
```bash
git tag -l "v1.*"
```
**Show a tag’s details (commit + metadata)**
```bash
git show v1.0.1
```

---

## 4) Share Tags with Remote
**Push one tag**
```bash
git push origin v1.0.1
```
**Push all local tags**
```bash
git push origin --tags
```
> Tip: normal `git push` does **not** push tags unless explicitly specified.

---

## 5) Delete / Move / Rename Tags
**Delete local tag**
```bash
git tag -d v1.0.1
```
**Delete remote tag**
```bash
git push origin --delete v1.0.1
```
**Move a tag to a new commit (force)**
```bash
git tag -f v1.0.1 <new-commit>
git push origin -f v1.0.1
```
**Rename a tag (recreate)**
```bash
git tag newname oldname
git tag -d oldname
git push origin :refs/tags/oldname
git push origin newname
```

---

## 6) Good Practices
- Use **annotated tags** for releases; include message, changelog link, and tagger info.
- Adopt **Semantic Versioning**: `vMAJOR.MINOR.PATCH` (e.g., `v2.3.1`).
- Tag **after** the release branch is ready and CI is green.
- Push tags immediately after creation to avoid local-only tags.

---

## 7) Common Workflows
**Create a release tag from a release branch head**
```bash
git checkout release/1.2.0
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```
**Hotfix starting from a tag**
```bash
git checkout -b hotfix/1.2.1 v1.2.0
# apply fix, commit
git tag -a v1.2.1 -m "Hotfix v1.2.1"
git push origin v1.2.1
```
**Verify a signed tag**
```bash
git tag -v v1.2.0
```

---

## 8) Pitfalls to Avoid
- **Forgetting to push tags**: your teammates/CI won’t see them.
- **Overwriting released tags**: avoid unless absolutely necessary; prefer a new version.
- **Confusing tags with branches**: tags don’t move; they are snapshots.

---

### TL;DR
- Tags are **immutable labels** on commits.
- Use **annotated** (or **signed**) tags for releases.
- Always **push** tags after creating them.
