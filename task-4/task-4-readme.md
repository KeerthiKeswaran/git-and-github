# Task 4: Simulating and Resolving Merge Conflicts

## Objective
Intentionally create a merge conflict scenario by creating two diverging branches from the same commit, modifying the same line in both, and attempting to merge them. Finally, use standard Git tools to identify and resolve the conflict.

## Experiment Scenario

### 1. Preparing the Conflict
To set up the scenario, two separate branches were created originating from the exact same commit base. Both branches modified the exact same line of a shared text file (`conflict-test.txt`).

1. **Branch A (`feature-red`):** Modified line 1 to read `"Color: Red"` and committed.
2. **Branch B (`feature-blue`):** Modified line 1 to read `"Color: Blue"` and committed.

### 2. Attempting the Merge
The first branch (`feature-red`) was merged cleanly into the main branch. However, attempting to merge the second branch (`feature-blue`) into the main branch resulted in a merge conflict because Git could not automatically determine which version of line 1 to keep.

**Merge Command:**
```bash
git merge feature-blue
```
**Output Received:**
```text
Auto-merging conflict-test.txt
CONFLICT (content): Merge conflict in conflict-test.txt
Automatic merge failed; fix conflicts and then commit the result.
```

### 3. Identifying the Conflict
To understand the state of the repository, the following diagnostic commands were used:

**Command 1:** `git status`
- **Result:** Displayed that `conflict-test.txt` had unmerged paths, specifically marked as "both modified". This clearly targets which files need manual intervention.

**Command 2:** `git diff`
- **Result:** Revealed the exact conflicting blocks inside the file marked by Git's standard conflict markers:
  ```diff
  <<<<<<< HEAD
  Color: Red
  =======
  Color: Blue
  >>>>>>> feature-blue
  ```

### 4. Resolving the Conflict Manually
The conflicting file (`conflict-test.txt`) was opened in an editor to manually resolve the divergence. The Git conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) were completely removed, and the final desired content was written in their place:

**Final Content Chosen:**
```text
Color: Purple (Combined Red and Blue)
```

### 5. Finalizing the Merge
Once the file was manually fixed, it was staged and committed to officially resolve the conflict and conclude the merge.

**Commands:**
```bash
git add conflict-test.txt
git commit -m "Resolve merge conflict in conflict-test.txt by combining colors"
```
**Result:** The merge was completed successfully, uniting the histories of both branches with the manually resolved changes.
