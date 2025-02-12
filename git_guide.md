# Git Guide

Git is a powerful distributed version control system used by developers worldwide. Whether you’re just starting or you’re deep into complex workflows, this guide provides a clear overview of basic Git operations and solutions to common (and not-so-common) scenarios.

> **Resources:**
>
> - [Git Official Documentation](https://git-scm.com/doc)
> - [GitHub Guides](https://guides.github.com/)
> - [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
> - [Google's Git Best Practices](https://google.github.io/git-review/)

---

## 1. Basic Git Usage

### 1.1 Installation

- **Windows:**  
  Download and run the installer from [git-scm.com/download/win](https://git-scm.com/download/win).

- **macOS:**  
  Via Homebrew:

  ```bash
  brew install git
  ```

  Or download directly from [git-scm.com/download/mac](https://git-scm.com/download/mac).

- **Linux:**  
  For Debian/Ubuntu:
  ```bash
  sudo apt-get update
  sudo apt-get install git
  ```
  For Fedora:
  ```bash
  sudo dnf install git
  ```

### 1.2 Initial Setup

Configure your identity to ensure that your commits are correctly attributed:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Verify your configuration with:

```bash
git config --list
```

### 1.3 Cloning a Repository

Clone an existing repository using HTTPS:

```bash
git clone https://github.com/username/repository.git
```

Or using SSH:

```bash
git clone git@github.com:username/repository.git
```

### 1.4 Basic Workflow: Add, Commit, and Push

1. **Check Repository Status:**
   ```bash
   git status
   ```
2. **Stage Changes:**
   ```bash
   git add .
   # Or add a specific file:
   git add filename
   ```
3. **Commit Changes:**
   ```bash
   git commit -m "Descriptive commit message"
   ```
4. **Push to Remote:**
   ```bash
   git push origin main
   ```
   _Tip:_ If you’re on a feature branch, simply:
   ```bash
   git push
   ```

### 1.5 Branching Essentials

- **Create and Switch to a New Branch:**
  ```bash
  git checkout -b feature-branch
  ```
- **Switch Branches:**
  ```bash
  git checkout main
  ```
- **Merge a Branch:**
  ```bash
  git checkout main
  git merge feature-branch
  ```

---

## 2. Realistic Git Scenarios and Solutions

Below are common (and some advanced) Git scenarios, with step-by-step solutions.

### Scenario 1: Push Rejected – “failed to push some refs”

**Issue:**  
When pushing, you see:

```plaintext
error: failed to push some refs to 'https://github.com/user/repo.git'
hint: Updates were rejected because the remote contains work that you do not have locally.
```

**Solution:**

1. **Rebase Your Local Changes:**
   ```bash
   git pull --rebase origin main
   ```
2. **Resolve Merge Conflicts (if any):**
   ```bash
   # Edit the conflicted files, then:
   git add <resolved-file>
   git rebase --continue
   ```
3. **Push Your Changes:**
   ```bash
   git push origin main
   ```

---

### Scenario 2: Wrong Author Details in a Commit

**Issue:**  
Committed with an incorrect author name or email.

**Solution:**

- **For the Last Commit:**
  ```bash
  git commit --amend --author="Correct Name <correct-email@example.com>"
  git push --force-with-lease
  ```
- **For All Commits (Advanced; Use with Caution):**
  ```bash
  git filter-branch --env-filter '
  if [ "$GIT_COMMITTER_EMAIL" = "wrong-email@example.com" ]; then
      export GIT_COMMITTER_NAME="Correct Name"
      export GIT_COMMITTER_EMAIL="correct-email@example.com"
  fi
  if [ "$GIT_AUTHOR_EMAIL" = "wrong-email@example.com" ]; then
      export GIT_AUTHOR_NAME="Correct Name"
      export GIT_AUTHOR_EMAIL="correct-email@example.com"
  fi
  ' --tag-name-filter cat -- --branches --tags
  git push --force --all
  git push --force --tags
  ```

---

### Scenario 3: Committed a Secret/API Key by Mistake

**Issue:**  
Sensitive data, such as an API key, has been pushed to the remote repository.

**Solution:**

1. **Immediately Revoke the API Key** at the provider.
2. **Remove the Secret from History:**
   ```bash
   git filter-branch --force --index-filter \
   'git rm --cached --ignore-unmatch path/to/file-with-secret' \
   --prune-empty --tag-name-filter cat -- --all
   ```
3. **Force Push the Cleaned History:**
   ```bash
   git push --force
   ```
4. **Add the File to `.gitignore`:**  
   Prevent future accidental commits of this file.

---

### Scenario 4: Committed to the Wrong Branch

**Issue:**  
You made commits on `main` instead of on your feature branch.

**Solution:**

1. **Create and Switch to the Correct Branch:**
   ```bash
   git branch feature-branch
   git checkout feature-branch
   ```
2. **Reset the `main` Branch to Its Previous State:**
   ```bash
   git checkout main
   git reset --hard origin/main  # Only if the changes are pushed
   ```

---

### Scenario 5: Merge Conflicts After Pulling Changes

**Issue:**  
After pulling updates, conflicts appear:

```plaintext
CONFLICT (content): Merge conflict in file.txt
Automatic merge failed; fix conflicts and then commit the result.
```

**Solution:**

1. **Resolve Conflicts in the File:**
   Edit the file to choose the correct version between:
   ```plaintext
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
   ```
2. **Stage the Resolved File:**
   ```bash
   git add file.txt
   ```
3. **Commit and Push:**
   ```bash
   git commit -m "Resolved merge conflict in file.txt"
   git push origin main
   ```

---

### Scenario 6: Undoing a `git reset --hard`

**Issue:**  
You accidentally lost changes after running `git reset --hard`.

**Solution:**

1. **Find the Lost Commit:**
   ```bash
   git reflog
   ```
2. **Restore the Commit:**
   ```bash
   git reset --hard <commit-hash>
   ```
3. **For Uncommitted Work (if applicable):**
   ```bash
   git fsck --lost-found
   ls .git/lost-found/
   ```

---

### Scenario 7: Removing a Commit Without Affecting Later Commits

**Issue:**  
A commit in the middle of your history needs to be removed.

**Solution:**

1. **Interactive Rebase:**
   ```bash
   git rebase -i HEAD~5  # Adjust the number to include the target commit.
   ```
2. **In the Editor:**  
   Change `pick` to `drop` for the commit to be removed.
3. **Force Push the Updated History:**
   ```bash
   git push --force
   ```

---

### Scenario 8: Pushed to the Wrong Remote Branch

**Issue:**  
Changes were pushed to `main` instead of a feature branch.

**Solution:**

1. **Revert the Incorrect Push:**
   ```bash
   git reset --hard origin/main
   git push --force origin main
   ```
2. **Push to the Correct Branch:**
   ```bash
   git checkout feature-branch
   git push origin feature-branch
   ```

---

### Scenario 9: Changing the Last Commit Message

**Issue:**  
You need to update the last commit message without modifying its content.

**Solution:**

```bash
git commit --amend -m "Updated commit message"
git push --force-with-lease
```

---

### Scenario 10: Switching from HTTPS to SSH

**Issue:**  
You cloned a repository using HTTPS but prefer SSH.

**Solution:**

```bash
git remote set-url origin git@github.com:user/repo.git
```

---

### Scenario 11: Handling Local Changes vs. Outdated Remote Branch

**Issue:**  
Local changes exist while the remote branch has advanced.

**Solution:**

1. **Stash Your Local Changes:**
   ```bash
   git stash save "WIP changes"
   ```
2. **Pull the Latest Changes:**
   ```bash
   git pull origin main
   ```
3. **Reapply Your Stashed Changes:**
   ```bash
   git stash pop
   ```
4. **Resolve Any Conflicts, Then Commit and Push:**
   ```bash
   git add .
   git commit -m "Merged local changes after pulling updates"
   git push origin main
   ```

---

### Scenario 12: Undoing a Merge Before Committing

**Issue:**  
You merged a branch but want to cancel the merge before it’s committed.

**Solution:**

- **Abort the Merge:**
  ```bash
  git merge --abort
  ```
- **If Already Committed but Not Pushed:**
  ```bash
  git reset --hard HEAD~1
  ```

---

### Scenario 13: Reverting a Pushed Commit

**Issue:**  
A commit introduced a bug and must be undone.

**Solution:**

```bash
git revert <commit-hash>
git push origin main
```

_Note:_ This creates a new commit that reverses the changes without rewriting history.

---

### Scenario 14: Removing a Large File from History

**Issue:**  
A huge file was accidentally committed, bloating the repository.

**Solution:**

```bash
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch largefile.zip' --prune-empty --tag-name-filter cat -- --all
git push --force
```

---

### Scenario 15: Pushed Confidential Code to a Public Repository

**Issue:**  
Sensitive code was mistakenly pushed to a public repository.

**Solution:**

1. **Immediately Delete the Repository (if possible) or Make It Private.**
2. **Revoke Exposed Credentials Immediately.**
3. **Rewrite History to Remove the Sensitive File:**
   ```bash
   git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch secret-file.env' --prune-empty --tag-name-filter cat -- --all
   git push --force
   ```

---

## Additional Scenarios and Advanced Techniques

### Scenario 16: Using Git Stash for Work in Progress

**Issue:**  
You need to switch branches but have uncommitted work.

**Solution:**

1. **Stash Your Changes:**
   ```bash
   git stash save "WIP: brief description"
   ```
2. **List Stashes:**
   ```bash
   git stash list
   ```
3. **Reapply the Stashed Changes:**
   ```bash
   git stash pop
   ```

---

### Scenario 17: Cherry-Picking Specific Commits

**Issue:**  
You want to apply a particular commit from one branch into another.

**Solution:**

```bash
git checkout target-branch
git cherry-pick <commit-hash>
```

_Resolve any conflicts if they arise._

---

### Scenario 18: Using Git Bisect to Identify a Bug

**Issue:**  
A bug was introduced, and you need to pinpoint the problematic commit.

**Solution:**

1. **Start Bisect:**
   ```bash
   git bisect start
   ```
2. **Mark the Current Commit as Bad and a Known Good Commit:**
   ```bash
   git bisect bad
   git bisect good <good-commit-hash>
   ```
3. **Test and Mark Each Commit:**
   ```bash
   git bisect good  # or git bisect bad
   ```
4. **End the Bisect Session:**
   ```bash
   git bisect reset
   ```

---

### Scenario 19: Managing Submodules

**Issue:**  
Your project relies on external dependencies maintained as submodules.

**Solution:**

1. **Add a Submodule:**
   ```bash
   git submodule add https://github.com/user/submodule-repo.git path/to/submodule
   ```
2. **Initialize and Update Submodules:**
   ```bash
   git submodule update --init --recursive
   ```

---

### Scenario 20: Squashing Commits for a Clean History

**Issue:**  
Multiple small commits need to be consolidated before merging to keep the history tidy.

**Solution:**

1. **Interactive Rebase to Squash:**
   ```bash
   git rebase -i HEAD~n  # Replace n with the number of commits to squash.
   ```
2. **In the Editor:**  
   Change `pick` to `squash` (or `fixup`) for commits to be combined.
3. **Force Push the Squashed Commits:**
   ```bash
   git push --force-with-lease
   ```

---

## Best Practices

- **Commit Frequently:** Keep your commits small and meaningful.
- **Use Descriptive Commit Messages:** Summarize what each commit does.
- **Leverage Branches:** Separate features, bug fixes, and experiments.
- **Avoid Unnecessary Force Pushes:** When collaborating, use `--force-with-lease` to safeguard others’ work.
- **Review Code via Pull Requests:** Encourage collaboration and code quality.
- **Backup Your Work:** Regularly push to remote repositories (e.g., GitHub, GitLab, Bitbucket).

---
