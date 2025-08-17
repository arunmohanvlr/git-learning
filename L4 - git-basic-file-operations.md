# Git File Operations Cheat Sheet

This note explains how to **add, edit, delete, and rename files** in Git, including **commit and push** steps with proper commit messages.

---

## 1. Add a File

**Command:**

```bash
touch index.html
git add index.html
git commit -m "Add index.html file"
git push origin main
```

**Purpose:** Create a new file, track it in Git, commit the addition, and push it to remote.

---

## 2. Edit File Content

**Command:**

```bash
echo "<h1>Hello World</h1>" >> index.html   # Edit file content
git add index.html
git commit -m "Edit index.html with Hello World content"
git push origin main
```

**Purpose:** Modify a file, stage the changes, commit them with a message, and push to remote.

---

## 3. Delete a File

**Command:**

```bash
git rm old.txt
git commit -m "Delete old.txt file"
git push origin main
```

**Purpose:** Remove a file from working directory and repository, commit the deletion, and push to remote.

---

## 4. Rename a File

**Command:**

```bash
git mv README.txt README.md
git commit -m "Rename README.txt to README.md"
git push origin main
```

**Purpose:** Rename or move a file, stage the change automatically, commit it, and push to remote.

---

👉 Each operation is followed by a **commit** with a meaningful message and a **push** to update the remote repository.

