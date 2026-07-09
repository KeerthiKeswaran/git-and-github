# Git and GitHub Concepts Curriculum

Welcome to the central repository for the Git & GitHub Mastery. This repository contains structured solutions and professional documentation for 10 distinct Git tasks, each demonstrating a core piece of version control competency.

The codebase is organized chronologically by task, with each task receiving its own dedicated `task-X` branch and isolated markdown documentation detailing the experiment and operations performed.

---

## Curriculum Overview

| Module | Title | Primary Focus | Branch |
| :---: | :--- | :--- | :--- |
| **01** | [Initialize, Commit, and Branch Basics](./task-1/task-1-readme.md) | `git init`, `add`, `commit`, `checkout -b`, `merge`, `log` | `task-1` |
| **02** | [Using .gitignore and Tracking Files](./task-2/task-2-readme.md) | `.gitignore` rules, `git status`, untracked files | `task-2` |
| **03** | [Undoing Changes & Reverting Commits](./task-3/task-3-readme.md) | `git restore`, `git revert`, `git reset` | `task-3` |
| **04** | [Simulating and Resolving Merge Conflicts](./task-4/task-4-readme.md) | Divergent branches, `git diff`, Manual block resolution | `task-4` |
| **05** | [Interactive Rebasing for Clean Commit History](./task-5/task-5-readme.md) | `git rebase -i`, Squashing, history restructuring | `task-5` |
| **06** | [Stashing Changes for Context Switching](./task-6/task-6-readme.md) | `git stash`, `push`, `pop`, `list`, `drop` | `task-6` |
| **07** | [Cherry-Picking Commits Between Branches](./task-7/task-7-readme.md) | `git cherry-pick <hash>`, Single-commit portability | `task-7` |
| **08** | [Using Git Hooks for Automated Checks](./task-8/task-8-readme.md) | `.git/hooks/pre-commit`, automated scripting, lint/testing | `task-8` |
| **09** | [Remote Repositories and Collaboration](./task-9/task-9-readme.md) | Pull/Merge Requests, `git push origin`, `git pull` | `task-9` |
| **10** | [Comprehensive Workflow & Recovery](./task-10/task-10-readme.md) | `git push --force`, Data-loss simulation, `git reflog` | `task-10` |

---

## 🛠️ Essential Git Command Reference

| Command | Description |
| :--- | :--- |
| `git clone <url>` | Clone an existing repository to your local machine |
| `git status` | Check the current state of the working directory |
| `git add <file>` | Stage changes for the next commit |
| `git commit -m "msg"` | Commit staged changes to the repository history |
| `git push` | Push local commits to the remote repository |
| `git pull` | Fetch and merge changes from the remote repository |
| `git branch <name>` | Create a new isolated line of development |
| `git checkout <b-name>` | Switch from one branch to another |
| `git log --oneline --graph` | View a visual, compact list of branch history |
| `git reflog` | View the hidden ledger of branch pointer movements |
