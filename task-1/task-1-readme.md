# Task 1: Git Basics and Workflow

## Objective
The objective of this task was to demonstrate core Git competencies, including repository initialization, staging, committing, and managing separate lines of development via branching and merging.

---

## Workflow Implementation

### 1. Repository Initialization
The repository was initialized to begin tracking project changes.
- **Input:** `git init`
- **Explanation:** Established the `.git` directory and internal data structures.

### 2. Creating and Staging Files
Created primary identification files for Task 1 and added them to the staging area.
- **Input:** 
  ```bash
  git add task-1/file-1.md task-1/file-2.md
  ```
- **Execution Result (git status):**
  ```text
  On branch master
  Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
          new file:   task-1/file-1.md
          new file:   task-1/file-2.md
  ```

### 3. Committing Baseline Changes
Committed the staged files to the repository history.
- **Input:** `git commit -m "Initialize task-1 files"`
- **Execution Result:**
  ```text
  [master 343f6ea] Rename task-1.md and add file-1, file-2
   4 files changed, 40 insertions(+)
   create mode 100644 task-1/file-1.md
   create mode 100644 task-1/file-2.md
  ```

### 4. Branch Management and Merging
Developed features in a dedicated `task-1` branch and subsequently integrated them into the main branch.
- **Input:**
  ```bash
  git checkout -b task-1
  git checkout master
  git merge task-1
  ```
- **Execution Result:**
  ```text
  Updating ab89704..343f6ea
  Fast-forward
   task-1/file-1.md        | Bin 0 -> 42 bytes
   task-1/file-2.md        | Bin 0 -> 42 bytes
   task-1/task-1-readme.md |  40 ++++++++++++++++++++++++++++++++++++++++
   task-1/task-1.md        | Bin 2866 -> 0 bytes
  ```

### 5. Final History Verification
Confirmed the successful integration of all branches and commits.
- **Input:** `git log --oneline --graph --all`
- **Execution Result:**
  ```text
  * cfba3be (HEAD -> master, task-1) Update file encoding for task-1
  * 343f6ea Rename task-1.md and add file-1, file-2
  * ab89704 (origin/task-1) update task-1
  * 13a4370 update task-1
  * 50a6e56 initial-commit-task-1
  * 9840e0b (origin/master) initial-main-brach
  ```
