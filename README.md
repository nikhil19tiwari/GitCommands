# 📘 Comprehensive Git Commands & Concepts Notes — *The Post-Mortem*

---

## 📑 Table of Contents

1. Git Conceptual Model: The Four Areas
2. Basic Setup and Repository Initialization
3. Basic Workflow: Taking a Snapshot
4. The "Undo" Buttons: Navigating Backward
5. Branching and Merging
6. Stashing: Pausing Your Work
7. Inspecting History (`git log` Deep Dive)
8. Remote Workflow & Collaboration
9. Altering History
10. Plumbing: Inside the `.git` Folder
11. Collaboration Platform Concepts

---

## 1️⃣ Git Conceptual Model: The Four Areas

Understanding Git = Understanding **how files move**.

### A. Working Directory

* Your actual project files
* Status:

  * `Untracked`
  * `Modified`

### B. Staging Area (Index)

* Prepares snapshot for commit
* Status: `Staged`

### C. Local Repository (HEAD)

* Stores commits (immutable snapshots)
* `HEAD` → points to latest commit

### D. Remote Repository

* Hosted version (GitHub, GitLab)

---

## 2️⃣ Basic Setup & Initialization

### Configure Git

```bash
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"
```

### Initialize Repo

```bash
git init
```

### Clone Repo

```bash
git clone https://github.com/user/repo.git
```

---

## 3️⃣ Basic Workflow: Snapshot

### Check Status

```bash
git status
```

### Add Files

```bash
git add file.txt
git add .
```

### See Changes

```bash
git diff
git diff --staged
```

### Commit

```bash
git commit -m "message"
git commit -am "message"
```

---

## 4️⃣ Undo Operations 🔁

### 1. Discard Changes (Working Dir)

```bash
git restore file.txt
```

---

### 2. Unstage File

```bash
git restore --staged file.txt
```

---

### 3. Undo Commit (Local)

#### Soft (keep staged)

```bash
git reset --soft HEAD~1
```

#### Mixed (default)

```bash
git reset HEAD~1
```

#### Hard ⚠️ (danger)

```bash
git reset --hard HEAD~1
```

---

### 4. Undo Pushed Commit (Safe)

```bash
git revert <commit-hash>
```

---

## 5️⃣ Branching & Merging 🌿

### Create Branch

```bash
git branch feature
```

### Switch Branch

```bash
git switch feature
```

### Merge

```bash
git merge feature
```

### Delete Branch

```bash
git branch -d feature
```

---

## 6️⃣ Stashing 🧠

### Save Work

```bash
git stash
git stash save "message"
```

### List

```bash
git stash list
```

### Apply

```bash
git stash apply
```

### Pop

```bash
git stash pop
```

### Delete

```bash
git stash drop stash@{0}
git stash clear
```

---

## 7️⃣ Inspecting History 🔍

### Basic Log

```bash
git log
```

### Useful Flags

```bash
git log --oneline
git log --graph --oneline --all
git log -p -2
git log --stat
git log --author="name"
git log --grep="fix"
```

### Blame

```bash
git blame file.txt
```

---

## 8️⃣ Remote Workflow 🌐

### Add Remote

```bash
git remote add origin <url>
```

### View Remotes

```bash
git remote -v
```

### Fetch

```bash
git fetch origin
```

### Pull

```bash
git pull origin main
```

### Push

```bash
git push origin main
```

---

## 9️⃣ Altering History ⚠️

### Amend Commit

```bash
git commit --amend -m "new message"
```

### Add Missing File

```bash
git add file.txt
git commit --amend --no-edit
```

### Force Push (danger)

```bash
git push --force
```

---

### Interactive Rebase

```bash
git rebase -i HEAD~3
```

---

## 🔟 Inside `.git` Folder (Plumbing)

### Important Files

| Path            | Purpose                |
| --------------- | ---------------------- |
| `.git/config`   | Repo config            |
| `.git/HEAD`     | Current branch pointer |
| `.git/index`    | Staging area           |
| `.git/logs/`    | Reflog                 |
| `.git/refs/`    | Branch & tag refs      |
| `.git/objects/` | Object database        |

---

### Git Object Types

#### 1. Blob

* File content only

#### 2. Tree

* Directory structure

#### 3. Commit

* Snapshot + metadata

#### 4. Tag

* Named reference

---

## 1️⃣1️⃣ Collaboration Concepts 🤝

### Issue

* Track bugs/tasks

---

### Fork

* Copy of repo to your account

---

### Pull Request (PR)

#### Workflow:

1. Fork repo
2. Clone fork
3. Create branch
4. Commit changes
5. Push
6. Create PR
7. Review & merge

---

## 🧠 Final Mental Model

```
Working Dir → Staging → Commit → Remote
      ↑            ↓         ↑
   restore     reset     revert
```

---

## 🚀 Pro Tip

* Use `reset` for **local undo**
* Use `revert` for **shared undo**
* Use `stash` for **temporary pause**
* Use `rebase` for **clean history**

---

## 📌 Conclusion

Git is not about commands — it's about **movement of data between 4 areas**.

Master that, and every command becomes predictable.

---

**Happy Coding 💻🔥**
