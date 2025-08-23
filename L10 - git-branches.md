# Git Branches

---

## 🔹 What is a Branch?

* A **branch** in Git is simply a **movable pointer to a commit**.
* By default, every repository starts with one branch called `main` (sometimes `master`).
* As you make commits, the branch pointer moves forward automatically to the latest commit.
* Branches allow you to work on features, bug fixes, or experiments **independently** without affecting the main code.

---

## 🔹 Why Branches?

* Keep the **main branch stable** (production-ready).
* Work on **new features or hotfixes in isolation**.
* Multiple developers can work in parallel without interfering.
* Flexible workflows (Git Flow, trunk-based development, GitHub Flow).

---

## 🔹 Branch Basics

**1. Create a new branch**

```bash
git branch feature/login
```

**2. Switch to a branch**

```bash
git checkout feature/login
# OR modern Git
git switch feature/login
```

**3. Create + switch in one step**

```bash
git checkout -b feature/login
# OR
git switch -c feature/login
```

**4. List branches**

```bash
git branch
```

(`*` marks the branch you are currently on.)

**5. Merge a branch**

```bash
git checkout main
git merge feature/login
```

**6. Delete a branch**

```bash
git branch -d feature/login
# force delete if not merged
git branch -D feature/login
```

**7. Push a branch to remote**

```bash
git push -u origin feature/login
```

---

## 🔹 Branch Example Workflow

1. Start from `main`:

   ```bash
   git checkout main
   git pull
   ```
2. Create feature branch:

   ```bash
   git checkout -b feature/signup-form
   ```
3. Make changes, commit:

   ```bash
   git add .
   git commit -m "Add signup form"
   ```
4. Push to remote:

   ```bash
   git push -u origin feature/signup-form
   ```
5. Open a Pull Request → review → merge into `main`.

---

## 🔹 Visual: Branching and Merging

```
main:    A---B---C
              \
feature:       D---E
```

After merging:

```
main:    A---B---C---M
              \     /
feature:       D---E
```

---

## 🔹 Branch Naming Conventions

### 1. Main Branches

* `main` → stable production-ready code.
* `develop` → integration branch (common in Git Flow).

### 2. Feature Branches

* **Pattern:** `feature/<ticket-id>-<short-description>`
* Examples:

  * `feature/1234-user-login`
  * `feature/profile-page-ui`

### 3. Bugfix Branches

* **Pattern:** `bugfix/<ticket-id>-<short-description>`
* Examples:

  * `bugfix/5678-navbar-overlap`
  * `bugfix/null-pointer-exception`

### 4. Hotfix Branches

* **Pattern:** `hotfix/<ticket-id>-<short-description>`
* Examples:

  * `hotfix/7890-critical-payment-error`
  * `hotfix/ssl-cert-renewal`

### 5. Release Branches

* **Pattern:** `release/<version>`
* Examples:

  * `release/1.0.0`
  * `release/2.5.3`

### 6. Experiment / Spike Branches

* **Pattern:** `experiment/<short-description>`
* Examples:

  * `experiment/graphql-api`
  * `experiment/new-cache-strategy`

---

## 🔑 Best Practices

* Use **lowercase + hyphens** in names.
* Include **ticket/issue IDs** for traceability.
* Delete branches after merging to keep repo clean.
* Never commit directly to `main`; always use PRs/MRs.
* Keep branch names **short but descriptive**.

---

✅ **In summary:**

* Branches = **lightweight, isolated lines of work**.
* Naming convention depends on purpose:

  * `main`, `develop`
  * `feature/...`
  * `bugfix/...`
  * `hotfix/...`
  * `release/...`
  * `experiment/...`

---