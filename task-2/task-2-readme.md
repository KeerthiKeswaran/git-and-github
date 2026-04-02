# Task 2: Using .gitignore and Tracking Files

## Objective
- Set up a `.gitignore` file to exclude certain files or directories from version control.
- Verify that ignored files are not tracked by Git using `git status`.

## Steps Performed

### 1. Creating Ignored Files
Created an environment variable file (`.env`) which typically contains sensitive information and should not be tracked.
- **File created:** `task-2/.env`

### 2. Setting Up .gitignore
Created a `.gitignore` file with rules to ignore the `.env` file, as well as temporary files (`*.tmp`) and logs (`*.log`).
- **File created:** `task-2/.gitignore`
- **Content:**
  ```text
  # environment variables — never commit secrets
  .env

  # log files
  *.log
  logs/

  # temporary files and folders
  *.tmp
  temp/
  ```

### 3. Verifying Ignored Files
Used `git status` to verify that the `.env` file is completely ignored by Git and only the `.gitignore` and `task-2-readme.md` files show up as untracked.

- **Command:** `git status`
- **Execution Result:**
  ```text
  On branch task-2
  Untracked files:
    (use "git add <file>..." to include in what will be committed)
          .gitignore
          task-2-readme.md

  nothing added to commit but untracked files present (use "git add" to track)
  ```
  *(Notice that `.env` does not appear in the untracked files list because it is successfully ignored).*
