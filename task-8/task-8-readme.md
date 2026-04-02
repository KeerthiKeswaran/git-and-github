# Task 8: Using Git Hooks for Automated Checks

## Objective
Set up an automated Git hook to run local scripts (such as linters, code formatting checks, or basic tests) right before a commit is finalized, aborting the commit if the tests fail.

## Experiment Scenario

### 1. Creating the Pre-Commit Hook
Git provides a hidden directory (`.git/hooks`) containing template files for various lifecycle events. To enforce a rule before committing, a script named `pre-commit` (with no file extension) was created in this folder. 

### 2. Writing the Hook Script
A simple shell script was written for the `pre-commit` hook to automatically search the repository for any lingering "TODO" comments.

**Script Content (`.git/hooks/pre-commit`):**
```sh
#!/bin/sh

# This searches the actual content of the files you are about to commit
if grep -r "TODO" .; then
    echo "COMMIT REJECTED: You have 'TODO' in your code!"
    exit 1
else
    echo "Check passed! Proceeding with commit..."
    exit 0
fi
```

*Note: The script exits with a status of `1` upon detecting the forbidden keyword. Git interprets any non-zero exit code as a failure and immediately aborts the commit.*

### 3. Testing the Hook
To test the pipeline:
1. **Failure Case:** A test file (`test-fail.txt`) containing the word "TODO" was staged. When `git commit` was executed, the script detected the keyword, printed `"COMMIT REJECTED: You have 'X' in your code!"`, and canceled the commit process safely.
2. **Success Case:** The word "X" was removed from the file. When `git commit` was attempted again, the script passed cleanly with exit code `0`, and the commit was successfully recorded in the repository.

---

## Why Use Git Hooks in Collaborative Projects?
Integrating Git Hooks into a team's workflow drastically improves code quality and efficiency:

1. **Automated Quality Control:** Pre-commit hooks can enforce code styling standards (like Prettier or ESLint), ensuring that poorly formatted code never even makes it into the repository. 
2. **Preventing Broken Builds:** By running unit tests or syntax checks at the hook level, developers catch broken code locally before pushing it to CI/CD pipelines, saving server resources and time.
3. **Security:** Hooks can be written to scan for accidentally exposed *** keys or sensitive credentials before they are permanently baked into the version history.
4. **Consistency:** Team members are held to the exact same standards programmatically, reducing friction and trivial comments in code review processes.
