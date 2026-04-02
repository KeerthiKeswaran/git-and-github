# Task 6: Stashing Changes for Context Switching

## Objective
Learn how to use Git's stash mechanisms to temporarily shelve uncommitted work. This allows a developer to safely switch contexts (like jumping to another branch to fix a hot issue) without having to commit half-written code.

## Experiment Scenario

### 1. Preparing Uncommitted Work
While actively developing on the `task-6` branch, an urgent request came in requiring a context switch to the `master` branch. However, there were currently modified, uncommitted files in the working directory that were not ready to be committed.

- **Action:** Created a new file `half-baked-feature.md` and added some draft content.
- **Verification:** `git status` showed `half-baked-feature.md` as an untracked/modified file.

### 2. Stashing the Changes
To clear the working directory without losing the draft progress, the work was stashed.

- **Command:** 
  ```bash
  git stash push -m "Drafting half-baked feature"
  ```
- **Result:** The working directory was immediately cleaned. The uncommitted modifications were safely stored away in Git's stash stack, and `git status` returned a clean working tree.

### 3. Context Switching
With a clean working tree, it was perfectly safe to switch branches.

- **Commands:**
  ```bash
  git checkout master
  # (Simulated fixing an urgent bug here and committing)
  git checkout task-6
  ```

### 4. Returning and Restoring Work
Back on the original `task-6` branch, the stashed work was retrieved so development could continue exactly where it was left off.

- **Command:** 
  ```bash
  git stash pop
  ```
- **Result:** The changes to `half-baked-feature.md` were re-applied to the working directory. Additionally, because `pop` was used, the specific stash entry was automatically deleted from the stash stack. (If you want to apply changes but *keep* them in the stash, you would use `git stash apply`).

## Managing Multiple Stashes (Optional Exercises)

During complex development, you might stash multiple times. Git maintains these as a stack.

1. **Viewing Stashes:**
   - **Command:** `git stash list`
   - **Result:** Displays all saved stashes with their index. For example:
     ```text
     stash@{0}: On task-6: Drafting half-baked feature
     stash@{1}: On master: WIP hotfix experiments
     ```

2. **Dropping a Stash:**
   - **Command:** `git stash drop stash@{1}`
   - **Result:** Permanently removes the targeted old stash from the stack without applying it, freeing up the stash history.

3. **Clearing All Stashes:**
   - **Command:** `git stash clear`
   - **Result:** Wipes out every single stash in the repository permanently.
