# Task 5: Interactive Rebasing for Clean Commit History

## Objective
Utilize Git's interactive rebase functionality to organize and clean up a messy commit history. This involves squashing multiple small commits into a single cohesive commit, reordering them, and editing commit messages.

## Experiment Scenario

### 1. Generating a Messy History
To prepare the scenario, multiple minor and somewhat disorganized commits were made to a single feature file:

1. **Commit 1:** `git commit -m "Add basic skeleton for feature X"`
2. **Commit 2:** `git commit -m "fix tpyo in skeleton"` *(intentional typo in message)*
3. **Commit 3:** `git commit -m "Add more logic"`
4. **Commit 4:** `git commit -m "WIP almost done"`

At this point, the `git log` showed a cluttered history of 4 micro-commits.

### 2. Initiating Interactive Rebase
To clean up the last 4 commits, the interactive rebase command was used:
```bash
git rebase -i HEAD~4
```

This opened our default text editor displaying the 4 commits from oldest to newest:
```text
pick 1a2b3c4 Add basic skeleton for feature X
pick 5d6e7f8 fix tpyo in skeleton
pick 9g0h1i2 Add more logic
pick 3j4k5l6 WIP almost done
```

### 3. Reordering, Editing, and Squashing
Inside the editor, the commit instructions were modified to achieve a clean history:
- The first commit was kept as the base (`pick`).
- The second commit was marked to be squashed (`squash`) into the first, as it was just a typo fix.
- The third commit was kept (`pick`) but marked for a message edit (`reword`).
- The fourth commit was squashed (`squash`) into the third.

**Modified Rebase File:**
```text
pick 1a2b3c4 Add basic skeleton for feature X
squash 5d6e7f8 fix tpyo in skeleton
reword 9g0h1i2 Add more logic
squash 3j4k5l6 WIP almost done
```

After saving and closing the file, Git automatically spawned new editor windows to let us rewrite the final commit messages for the squashed clusters. The resulting history condensed the 4 noisy commits into 2 clear, well-documented commits.

## Why Squash Commits Before Merging?
Squashing (condensing) commits before merging a feature branch into `main` or `master` is highly beneficial:
1. **Cleaner History:** It removes intermediate "noise" like `WIP` (Work In Progress) commits or minor typo fixes.
2. **Reviewability:** Pull requests become easier to read when reviewers only see logical, complete units of work rather than 50 micro-adjustments.
3. **Easier Reverts/Rollbacks:** If a feature introduces a bug on the main branch, a cleanly squashed feature allows you to use `git revert` on a *single* commit rather than having to hunt down and revert a dozen tiny fragments.
