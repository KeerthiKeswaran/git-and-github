# Task 7: Cherry-Picking Commits Between Branches

## Objective
Apply a specific, isolated commit from one branch to another using the `git cherry-pick` command. Handle any merge conflicts that result from this direct application.

## Experiment Scenario

### 1. Preparing the Branches and Commits
To execute this scenario, two separate branches were used: `task-6` and `task-7`.

- **On `task-6`:** A new text file named `cherry-pick.txt` was created with some initial content and committed to the branch history.
  - *Commit Hash Example:* `92b3917` (Created cherry-pick.txt)

- **On `task-7`:** A file with the exact same name (`cherry-pick.txt`) was created independently, but with *different* content. This was also committed to `task-7`.

### 2. Initiating the Cherry-Pick
While checked out on the `task-7` branch, the goal was to pull in ONLY the specific commit from `task-6` where `cherry-pick.txt` was created/modified.

- **Command:** 
  ```bash
  git cherry-pick 92b3917
  ```

### 3. Handling the Merge Conflict
Because both branches modified/created `cherry-pick.txt` with diverging contents, Git could not safely figure out which content was preferred. The cherry-pick paused and resulted in a merge conflict.

- **Console Output:** Git flagged a conflict in `cherry-pick.txt` and halted the process.
- **Resolution:** The conflicting file (`cherry-pick.txt`) was opened in an editor. The Git conflict markers were assessed, and the final content was manually merged to accommodate both changes, resolving the conflict.

### 4. Finalizing the Process
Once the file was corrected, it was staged, and the cherry-pick sequence was manually committed and finalized.

- **Commands:**
  ```bash
  git add cherry-pick.txt
  git commit -m "cheery-pick-merge-conflict"
  git push
  ```

### 5. Verification
A quick `git log` verification confirmed that the changes originally authored in `task-6` were successfully ported and merged into the timeline of `task-7` through the manual cherry-pick interaction.
