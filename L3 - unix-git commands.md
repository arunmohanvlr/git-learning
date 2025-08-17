# Unix + Git Command Cheat Sheet (One Note Version)

---

## 🔹 Unix Commands

**Navigation**
- `pwd` – Show current directory
- `ls` – List files
- `ls -a` – List all files including hidden
- `ls -l` – Detailed file listing
- `cd <dir>` – Change directory
- `cd ..` – Move up one level
- `cd ~` – Go to home directory

**File Operations**
- `touch <file>` – Create empty file
- `mkdir <dir>` – Create new folder
- `rm <file>` – Remove file
- `rm -r <dir>` – Remove folder recursively
- `cp <src> <dest>` – Copy file or folder
- `mv <src> <dest>` – Move or rename file/folder

**Viewing & Searching**
- `cat <file>` – Show file contents
- `less <file>` – Scroll through file
- `grep <text> <file>` – Search text in file
- `grep -r <text> .` – Search text recursively in repo
- `diff <file1> <file2>` – Show differences between files

**System Info**
- `whoami` – Show current user
- `uname -a` – System information
- `ps` – Show running processes
- `top` – Live process monitor

---

## 🔹 Git Commands

**Setup**
- `git config --global user.name "Your Name"`
- `git config --global user.email "you@example.com"`

**Repository**
- `git init` – Initialize new repo
- `git clone <url>` – Clone repo

**Basic Workflow**
- `git status` – Show changes
- `git add <file>` – Stage file
- `git add .` – Stage all changes
- `git commit -m "message"` – Commit changes

**Branches**
- `git branch` – List branches
- `git branch <name>` – Create branch
- `git checkout <name>` – Switch branch
- `git checkout -b <name>` – Create + switch branch
- `git merge <branch>` – Merge branch into current

**Remotes**
- `git remote -v` – Show remotes
- `git pull` – Fetch + merge from remote
- `git push` – Push commits to remote

**History & Inspection**
- `git log` – Show commit history
- `git log --oneline` – Short commit history
- `git diff` – Show unstaged changes
- `git diff --staged` – Show staged changes

**Undo**
- `git checkout -- <file>` – Discard local changes
- `git reset HEAD <file>` – Unstage a file
- `git revert <commit>` – Create new commit to undo a commit
- `git reset --hard <commit>` – Reset branch to commit (dangerous)

---


