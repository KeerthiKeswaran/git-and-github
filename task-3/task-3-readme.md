# Task 3: Undoing Changes and Reverting Commits

## Objective
Experiment with undoing changes in the working directory and un-committing changes using Git commands such as `git restore`, `git revert`, and `git reset`. 

## Experiment Report

### 1. Undoing Uncommitted Changes
To discard local modifications to a tracked file before they are committed, we use `git restore` (or `git checkout -- <file>`). 

- **Scenario:** I edited `experiment.txt` but realized the changes were wrong and wanted to go back to the original tracked state.
- **Command:** `git restore experiment.txt`
- **Result:** The changes in the working directory were permanently discarded, and the file reverted to its last committed state.

### 2. Safely Undoing a Commit (`git revert`)
`git revert` is used to safely undo a previous commit by creating a *new* commit that applies the exact opposite changes.

- **Scenario:** I accidentally committed a file with a typo, but this commit was already pushed to a shared repository.
- **Command:** `git revert <commit-hash>`
- **Result:** Git created a new commit that undid the changes introduced by the flawed commit. The repository's history was preserved, avoiding conflicts for other collaborators.

### 3. Removing Commits Entirely (`git reset`)
`git reset` moves the branch pointer backward, effectively erasing commits from the project's history. This shouldn't typically be done on shared branches.

- **Scenario:** I made multiple messy commits locally and wanted to wipe them out completely before pushing.
- **Command:** `git reset --hard <commit-hash>` (resets back to the specified commit)
- **Result:** The branch was pointed back to the older commit. The messy commits were removed from the commit history, and the working directory was updated to match the old commit.

## Comparison: Revert vs. Reset
| Feature | `git revert` | `git reset` |
| :--- | :--- | :--- |
| **Action** | Creates a new commit that negates previous changes. | Modifies branch history by moving the branch pointer backwards. |
| **History** | Preserves commit history (leaves a trail of who undid what). | Rewrites history (erases commits as if they never happened). |
| **Safety** | Very safe. Ideal for public, shared branches. | Dangerous if pushed. Only use on local, un-pushed branches. |
