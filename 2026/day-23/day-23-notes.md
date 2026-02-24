#
# Day 23 – Git Branching & Working with GitHub

## Task 1: Understanding Branches

### 1. What is a branch in Git?
A branch in Git is a separate line of development. It allows you to work on new features or fixes without affecting the main code.

### 2. Why do we use branches instead of committing everything to main?
We use branches to:
- Keep main stable
- Develop features safely
- Fix bugs without breaking production
- Work in parallel with other developers

### 3. What is HEAD in Git?
HEAD is a pointer that refers to the current branch and the latest commit on that branch.

### 4. What happens to your files when you switch branches?
When you switch branches, Git changes the working directory to match the files from that branch’s latest commit.

---

## Task 2: Branching Commands – Hands-On

### Commands Used:

- `git branch`  
  Lists all branches.

- `git branch feature-1`  
  Creates a new branch.

- `git switch feature-1`  
  Switches to feature-1 branch.

- `git switch -c feature-2`  
  Creates and switches to a new branch in one command.

- `git checkout feature-1`  
  Older way to switch branches.

Difference between `git switch` and `git checkout`:
- `git switch` is used only for branch switching.
- `git checkout` can switch branches and restore files.
- `git switch` is safer and clearer.

I created a commit on `feature-1` and confirmed it was not visible on `main`.

- `git branch -d feature-2`  
  Deletes a branch.

---

## Task 3: Push to GitHub

### Steps:

1. Created new repo on GitHub (without README).
2. Connected local repo:

   `git remote add origin <repo-url>`

3. Pushed main branch:

   `git push -u origin main`

4. Pushed feature branch:

   `git push -u origin feature-1`

Verified both branches are visible on GitHub.

### What is the difference between origin and upstream?

- `origin` → Default remote name for your repository.
- `upstream` → Refers to the original repository (used in forked repos).

---

## Task 4: Pull from GitHub

Made a change directly on GitHub and pulled it locally using:

`git pull origin main`

### Difference between git fetch and git pull:

- `git fetch` → Downloads changes but does not merge.
- `git pull` → Downloads and merges changes automatically.

---

## Task 5: Clone vs Fork

### What is the difference between clone and fork?

- Clone → Creates a local copy of a repository.
- Fork → Creates a copy of someone else's repository under your GitHub account.

### When to use clone vs fork?

- Clone → When you have direct access to the repository.
- Fork → When contributing to someone else's project.

### How to keep fork in sync?

1. Add upstream remote:
   `git remote add upstream <original-repo-url>`

2. Fetch upstream changes:
   `git fetch upstream`

3. Merge changes:
   `git merge upstream/main`


   ;;;;;;;;;;;;;;;;;;;;
   git branch - List all branches
git branch <name> - Create new branch
git switch <name> - Switch branch
git switch -c <name> - Create & switch branch
git checkout <name> - Switch branch (older method)
git branch -d <name> - Delete branch
git remote add origin <url> - Connect local repo to GitHub
git push -u origin <branch> - Push branch to GitHub
git pull origin <branch> - Pull changes from GitHub
git fetch - Download changes without merging
git clone <url> - Clone repository
git remote add upstream <url> - Add original repo reference
