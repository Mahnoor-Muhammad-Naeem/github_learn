# Learn Git & GitHub — Beginner → Pro
---

## Table of Contents
- [Quick Start (5 minutes)](#quick-start-5-minutes)
- [Core Concepts](#core-concepts)
- [Daily Workflow](#daily-workflow)
- [Cheat Sheet](#cheat-sheet)
- [Working with GitHub](#working-with-github)
- [Branching Strategy](#branching-strategy)
- [Undo & Recovery](#undo--recovery)
- [Conflicts (and how to fix them)](#conflicts-and-how-to-fix-them)
- [`.gitignore` Essentials](#gitignore-essentials)
---

## Quick Start (5 minutes)
**Install Git** (if not already): [git-scm.com](https://git-scm.com/)

Initialize a new project locally and push to GitHub:
```bash
# 1) Configure once per machine
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# 2) Start a project
mkdir hello-git && cd hello-git
echo "# Hello Git" > README.md

git init
git add README.md
git commit -m "chore: initial commit"

# 3) Create an empty repo on GitHub, then link it
# Replace <YOUR-URL> with the HTTPS/SSH URL from GitHub
git remote add origin <YOUR-URL>

# 4) Push it!
git branch -M main
git push -u origin main
```

---

## Core Concepts
- **Repository (repo):** A project folder tracked by Git.
- **Commit:** A snapshot of changes with a message.
- **Branch:** A line of development (e.g., `main`, `feature/login`).
- **Remote:** A server repo (like GitHub) your local repo syncs with.
- **Pull Request (PR):** A request to merge changes from one branch to another (usually feature → main).

---

## Daily Workflow
```bash
# Create & switch to a new feature branch
git checkout -b feature/amazing-thing

# Edit files → stage → commit
git add .
git commit -m "feat: build amazing thing"

# Sync with GitHub
git push -u origin feature/amazing-thing

# Open a Pull Request on GitHub → request review → address feedback → merge
```

Pro tips:
- Keep commits **small** and messages **clear**: `type(scope): summary` (e.g., `fix(api): handle 500 errors`).
- One feature per branch. Delete merged branches to stay tidy.

---

## Cheat Sheet
### Repo & Config
```bash
git init                      # start tracking the current folder
git clone <URL>               # copy a remote repo locally
git remote -v                 # list remotes
git remote add origin <URL>   # connect to GitHub
```

### Status, Stage, Commit
```bash
git status                    # what changed?
git add <file> | .            # stage changes
git commit -m "message"       # save a snapshot
```

### Branching
```bash
git branch                    # list branches
git checkout -b feat/x        # create & switch
git switch <branch>           # switch branches
git branch -d feat/x          # delete local branch
```

### Syncing
```bash
git pull                      # fetch + merge from remote
git fetch                     # fetch only
git push                      # upload commits to remote
```

### Inspect & Compare
```bash
git log --oneline --graph --decorate --all
git diff                      # show unstaged changes
git diff --staged             # show staged changes
```

### Stash (save WIP without committing)
```bash
git stash                     # stash changes
git stash pop                 # reapply last stash
```

---

## Working with GitHub
**Create a repository:** New → name → public/private → create.

**Fork vs. Clone**
- **Clone** your own repo to work locally.
- **Fork** someone else’s repo (your copy) → clone your fork → PR back to the original.

**Open a Pull Request (PR)**
1. Push your branch to GitHub.
2. Click **Compare & pull request**.
3. Fill title/description (link issues if any: `Fixes #123`).
4. Request review → address feedback → **Merge** (Squash for cleaner history).

**Issues:** Track bugs/tasks; use labels (bug, feature), assignees, and milestones.

---

## Branching Strategy
- `main`: always deployable.
- `feature/*`: one feature per branch; PR into `main`.
- Optional: `hotfix/*` for urgent production fixes.

Keep PRs small (≤ 300 lines changed when possible) for fast reviews.

---

## Undo & Recovery
```bash
git restore <file>            # discard unstaged changes to a file
git restore --staged <file>   # unstage

git reset --soft HEAD~1       # undo last commit, keep changes staged
git reset --mixed HEAD~1      # undo last commit, keep changes unstaged
git reset --hard HEAD~1       # undo last commit AND changes (destructive)

git revert <commitSHA>        # create a new commit that reverses an old one

git reflog                    # browse all moves; recover lost commits
```

---

## Conflicts (and how to fix them)
1. Run `git pull` (or merge a PR) and Git shows conflicts.
2. Open the files; look for markers `<<<<<<<`, `=======`, `>>>>>>>`.
3. Decide the correct final content; remove markers.
4. `git add .` → `git commit` → continue merge or push the resolution.

Use your editor’s merge tools (VS Code: “Accept Current/Incoming/Both”).

---

## `.gitignore` Essentials
Create a `.gitignore` in your repo root to avoid committing junk (builds, secrets, venvs, node_modules).

**Python example**
```
__pycache__/
*.py[cod]
.env
.venv/
*.ipynb_checkpoints/
```

**Node.js example**
```
node_modules/
.env
coverage/
dist/
```

Find ready templates: https://github.com/github/gitignore

---


Happy committing!

