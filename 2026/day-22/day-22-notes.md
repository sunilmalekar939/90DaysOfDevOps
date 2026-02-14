###
1️⃣ Verify Git Installation
git --version


If installed, you’ll see something like:

git version 2.xx.x


If not installed:

Mac: brew install git

Ubuntu: sudo apt install git

Windows: Download from git-scm.com

2️⃣ Set Your Git Identity
git config --global user.name "Sunil Malekar"
git config --global user.email "your-email@example.com"


Verify:

git config --global --list


This identity is attached to every commit you create.

✅ Task 2 – Create Your Git Project
1️⃣ Create Project Folder
mkdir devops-git-practice
cd devops-git-practice

2️⃣ Initialize Git
git init


Output:

Initialized empty Git repository in .../devops-git-practice/.git/

3️⃣ Check Status
git status


You will see:

On branch main
No commits yet
nothing to commit


👉 This tells you:

You are on branch main

No commits exist

No tracked files yet

4️⃣ Explore .git/ Folder
ls -la


You’ll see .git/

Go inside:

cd .git
ls


You will see:

HEAD

config

objects

refs

hooks

👉 This folder stores:

All commit history

Branch information

Configuration

Metadata

If you delete .git/ → your project stops being a Git repository and all history is lost.

✅ Task 3 – Create git-commands.md

Create file:

touch git-commands.md


Add this content inside:

📁 Setup & Config
git --version

Shows installed Git version
Example:

git --version

git config --global user.name

Sets your Git username
Example:

git config --global user.name "Sunil Malekar"

git config --global user.email

Sets your email
Example:

git config --global user.email "your@email.com"

🔄 Basic Workflow
git init

Initializes a Git repository
Example:

git init

git status

Shows current state of working directory
Example:

git status

git add

Stages changes
Example:

git add git-commands.md

git commit

Saves staged changes to repository
Example:

git commit -m "Add initial git commands reference"

👀 Viewing Changes
git log

Shows commit history
Example:

git log

git log --oneline

Shows compact commit history
Example:

git log --oneline

git diff

Shows unstaged changes
Example:

git diff

✅ Task 4 – Stage and Commit
Stage file
git add git-commands.md


Check staged:

git status

Commit
git commit -m "Add initial git commands documentation"

View history
git log --oneline


Example:

a1b2c3d Add initial git commands documentation

✅ Task 5 – Build Commit History (Minimum 3 Commits)

Now repeat:

1️⃣ Edit git-commands.md

Add new commands like:

git branch

git checkout

git restore

git show

2️⃣ Check changes
git diff

3️⃣ Stage & Commit Again
git add git-commands.md
git commit -m "Add branch and checkout commands"

Repeat Again

Make another update:

git commit -m "Expand viewing changes section"

View Compact History
git log --oneline


Expected output example:

f5e6d7c Expand viewing changes section
d4c3b2a Add branch and checkout commands
a1b2c3d Add initial git commands documentation


📸 Take screenshot of this output for submission.

✅ Task 6 – Create day-22-notes.md

Create:

touch day-22-notes.md


Add answers like this (in your own words):

📘 Day 22 Notes
1️⃣ Difference between git add and git commit

git add moves changes to the staging area.
git commit saves staged changes permanently in repository history.

2️⃣ What does staging area do?

The staging area allows us to select specific changes before committing. It gives control over what goes into a commit instead of committing everything directly.

3️⃣ What does git log show?

It shows:

Commit ID (hash)

Author name

Date

Commit message

4️⃣ What is .git folder?

The .git folder stores all repository data including commits, branches, and configuration. If deleted, Git history is permanently lost.

5️⃣ Working Directory vs Staging Area vs Repository

Working Directory → Where you edit files
Staging Area → Where changes wait before commit
Repository → Where committed changes are permanently stored

Then:

git add day-22-notes.md
git commit -m "Add day 22 Git workflow notes"

✅ Final Structure Should Look Like
devops-git-practice/
 ├── git-commands.md
 ├── day-22-notes.md
 └── .git/

🚀 Push to GitHub

If connected to remote:

git remote add origin <repo-url>
git push -u origin main
