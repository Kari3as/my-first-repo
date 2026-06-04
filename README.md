<div align="center">

![Git & GitHub Zero to Hero](https://capsule-render.vercel.app/api?type=waving&color=0:1a472a,100:2E80DC&height=200&section=header&text=Git%20%26%20GitHub&fontSize=60&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Zero%20to%20Hero%20Cheatsheet&descAlignY=55&descSize=22)

[![Beginner Friendly](https://img.shields.io/badge/Beginner-Friendly-2E80DC?style=for-the-badge&logo=git&logoColor=white)](https://git-scm.com)
[![GitHub](https://img.shields.io/badge/GitHub-Required-1a472a?style=for-the-badge&logo=github&logoColor=white)](https://github.com)
[![VS Code](https://img.shields.io/badge/VS%20Code-Recommended-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)](https://code.visualstudio.com)
[![License MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)
[![Modules](https://img.shields.io/badge/Modules-14-orange?style=for-the-badge)]()

# 🐙 Git & GitHub — Zero to Hero Cheatsheet

> *"Every expert was once a beginner. Every pro was once an amateur."* 🌱

A **complete, practical guide** to Git & GitHub — from your very first commit to CI/CD pipelines and open source contributions. Built from real hands-on learning, written for humans. 🧑‍💻

</div>

---

## 📋 Table of Contents

| Phase | Module | Topic |
|-------|--------|-------|
| 🌱 **Beginner** | [01](#-module-1--what-is-git--github) | What is Git & GitHub? |
| 🌱 **Beginner** | [02](#️-module-2--installing--configuring-git) | Installing & Configuring Git |
| 🌱 **Beginner** | [03](#-module-3--file-lifecycle--staging--committing) | File Lifecycle — Staging & Committing |
| 🌱 **Beginner** | [04](#-module-4--navigating-history) | Navigating History |
| 🌱 **Beginner** | [05](#-module-5--remote-repos--github) | Remote Repos & GitHub |
| 🌿 **Intermediate** | [06](#-module-6--branches--merging) | Branches & Merging |
| 🌿 **Intermediate** | [07](#-module-7--pull-requests--issues) | Pull Requests & Issues |
| 🌿 **Intermediate** | [08](#️-module-8--vs-code-git-integration) | VS Code Git Integration |
| 🌿 **Intermediate** | [09](#-module-9--github-pages--deployment) | GitHub Pages & Deployment |
| 🔥 **Advanced** | [10](#-module-10--advanced-git-commands) | Advanced Git Commands |
| 🔥 **Advanced** | [11](#️-module-11--merge-conflicts-in-depth) | Merge Conflicts in Depth |
| 🔥 **Advanced** | [12](#-module-12--github-actions--cicd) | GitHub Actions & CI/CD |
| 🏆 **Hero** | [13](#-module-13--open-source--team-collaboration) | Open Source & Team Collaboration |
| 🏆 **Hero** | [14](#-module-14--pro-tips-aliases--copilot) | Pro Tips, Aliases & Copilot |

---

## 🌱 Module 1 — What is Git & GitHub?

> 💡 **Analogy:** Git is like the **Save Game** button — it records your exact state at any moment. GitHub is the **cloud server** that stores all your saves and lets teammates play the same game with you.

### The Problem Git Solves
Without Git → files named `project_final_v2_REAL_final3.zip` with no idea what changed.  
With Git → every change tracked with date, author, and message. Revert any mistake instantly. ✅

### Git vs GitHub

| Feature | Git | GitHub |
|---------|-----|--------|
| What is it? | Tool on your computer | Website / cloud service |
| Works offline? | ✅ Yes | ❌ No |
| Made by | Linus Torvalds (2005) | Microsoft-owned (2018) |
| Purpose | Track changes locally | Share & collaborate online |

### The 3-Stage Flow
```
💻 Working Directory → git add → 📦 Staging Area → git commit → 📚 Local Repo → git push → ☁️ GitHub
```

> 🤯 **Fun fact:** Linus Torvalds built Git in just **10 days** in 2005. It's now used by 94% of professional developers worldwide.

---

## ⚙️ Module 2 — Installing & Configuring Git

### Install Git
| OS | Command |
|----|---------|
| **Windows** | Download from [git-scm.com](https://git-scm.com) → run installer |
| **macOS** | Run `git --version` → macOS prompts auto-install |
| **Linux** | `sudo apt install git` |

### Configure Your Identity (Do This Once!)
```bash
# Tell Git who you are
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Verify settings
git config --list
```

> 💡 **Tip:** Use the same email as your GitHub account — this links commits to your profile and fills your contribution graph!

### Create Your First Repo
```bash
mkdir my-project
cd my-project
git init                          # Initialize Git in this folder
echo "# My Project" > README.md  # Create a README
git status                        # Check what Git sees
```

### GitHub Authentication — Personal Access Token (PAT)
GitHub no longer accepts passwords. Use a PAT instead:
1. GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
2. Generate new token → tick `repo` + `workflow` scopes
3. Copy it immediately — GitHub won't show it again!

```bash
# Add token to your remote URL
git remote set-url origin https://USERNAME:YOUR_TOKEN@github.com/USERNAME/repo.git
```

---

## 📦 Module 3 — File Lifecycle: Staging & Committing

> 💡 **Analogy:** `git add` = put items in a box 📦. `git commit` = seal and label the box. `git push` = ship the box to GitHub ☁️.

### File States
```
Untracked (red) → git add → Staged (green) → git commit → Committed ✅
```

### Essential Commands
```bash
git status                          # See what changed (red = unstaged, green = staged)
git add filename.txt                # Stage one file
git add .                           # Stage ALL changed files
git commit -m "Your message here"   # Commit with a message
git commit -am "Fix typo"           # Add + commit tracked files in one step
```

### Writing Great Commit Messages

| ❌ Bad | ✅ Good |
|--------|---------|
| `fix stuff` | `Fix login button not responding on mobile` |
| `update` | `Update navbar: add dark mode toggle` |
| `changes` | `Refactor database queries for 30% speed boost` |
| `asdfgh` | `Add user authentication with JWT tokens` |

> 💡 **Formula:** `[verb] [what] [where/why]` — Start with: Add, Fix, Update, Remove, Refactor, Create. Keep under 72 characters.

---

## 🕰️ Module 4 — Navigating History

> 💡 **Analogy:** A commit is like taking a **photograph** of your project. Git stores every photo, and you can scroll through your album anytime.

### Viewing History
```bash
git log                   # Full history with details
git log --oneline         # Compact one-line history ← use this daily!
git log --oneline --graph --decorate --all  # Visual branch graph 🌳
git show abc1234          # See what changed in a specific commit
git diff                  # See changes in working directory
```

### Reading git log Output
```
e8bdc10 (HEAD -> main, origin/main) Adding another line to README
3064fe7 Add README file
```
- `e8bdc10` → commit hash (unique fingerprint)
- `HEAD -> main` → you are currently here 📍
- `origin/main` → GitHub's version at this commit

### Reading Diff Output
```diff
--- a/README.md       ← old version
+++ b/README.md       ← new version
- removed line        ← shown in red
+ added line          ← shown in green
  unchanged line      ← context only
```

> 💡 **Tip:** `/dev/null` in a diff means the file was **brand new** — it didn't exist before that commit.

### Key Concept: HEAD
`HEAD` is a pointer — your "You Are Here" pin on the commit map. 📍  
It always points to your current position in history.

---

## ☁️ Module 5 — Remote Repos & GitHub

> 💡 **Analogy:** `origin` = saving a contact in your phone. Instead of typing the full URL every time, you save it once with the nickname `origin`.

### Key Concepts
- **`origin`** = nickname for your GitHub URL
- **`main`** = your default branch name (older Git used `master`)

### The Complete First Push Workflow
```bash
# 1. Stage your files
git add .

# 2. Make your first commit
git commit -m "Initial commit"

# 3. Link to GitHub
git remote add origin https://github.com/USERNAME/repo.git

# 4. Rename branch to main
git branch -M main

# 5. Push! (-u sets upstream so future pushes just need 'git push')
git push -u origin main
```

### Everyday Sync Commands
```bash
git push              # Send commits UP to GitHub ⬆️
git pull              # Bring GitHub changes DOWN to you ⬇️
git fetch             # Download changes without merging
git remote -v         # See all remote connections
```

> ⚠️ **Remember:** The `-u` flag in `git push -u origin main` only needed ONCE per branch. After that, just use `git push`.

### README.md Best Practices
Every repo should have a README with:
```markdown
# Project Name
Short description

## Installation
## Usage  
## Contributing
## License
```

---

## 🌿 Module 6 — Branches & Merging

> 💡 **Analogy:** A branch is a **parallel universe** of your project. Experiment freely. If it works → merge it. If it fails → delete it. Main stays safe either way!

### Branch Naming Convention
```
feature/dark-mode      ← new functionality
fix/login-bug          ← bug fixes  
hotfix/payment-crash   ← urgent production fixes
docs/update-readme     ← documentation only
```

### Essential Branch Commands
```bash
git branch                        # List all local branches (* = current)
git branch -a                     # List ALL branches including remote
git switch -c feature/new-page    # Create AND switch to new branch ← modern way
git switch main                   # Switch to main branch
git branch -d feature/new-page    # Delete branch (after merging)
git push origin --delete feature/new-page  # Delete branch from GitHub
```

### The Complete Branch Workflow
```bash
# 1. Create feature branch
git switch -c feature/about-page

# 2. Do your work, commit
git add .
git commit -m "Add about page"

# 3. Push branch to GitHub
git push -u origin feature/about-page

# 4. Switch back to main
git switch main

# 5. Merge your feature
git merge feature/about-page

# 6. Push updated main
git push

# 7. Clean up
git branch -d feature/about-page
git push origin --delete feature/about-page
```

### Merge Strategies
```
Fast-forward merge:   main: A-B → feature: A-B-C → merged: A-B-C (clean!)
3-way merge:          Creates an extra merge commit M
```

> 💡 **Golden rule:** Always work on a feature branch. Never commit directly to main in a team!

---

## 📬 Module 7 — Pull Requests & Issues

> 💡 **Analogy:** A Pull Request is like submitting homework for review. You've done the work — now you're asking teammates: *"Can you check this before we add it to the main project?"*

### git pull vs Pull Request — NOT the same thing!
| | `git pull` | Pull Request (PR) |
|--|--|--|
| What? | Terminal command | GitHub website feature |
| Does? | Downloads changes to local | Requests code review before merging |

### Opening a PR on GitHub
1. Push your branch → `git push -u origin feature/your-branch`
2. Go to GitHub → click **"Compare & pull request"** banner
3. Write clear title and description
4. Tag reviewers in the right sidebar
5. Click **"Create pull request"**

### Auto-close Issues with Commits
```bash
# Write this in your PR description or commit message:
Closes #42
# GitHub automatically closes issue #42 when PR merges! ✅
```

### After PR is Merged
```bash
git switch main          # Go back to main
git pull                 # Sync GitHub's merged changes locally ⬇️
git branch -d feature/your-branch  # Delete local branch
```

> 💡 **Pro tip:** Never just write "LGTM" on every PR. Thoughtful reviews make the codebase stronger!

---

## 🖥️ Module 8 — VS Code Git Integration

VS Code has built-in Git — no terminal needed for everyday tasks!

### VS Code File Indicators
| Letter | Meaning |
|--------|---------|
| `U` | Untracked — Git has never seen this file |
| `M` | Modified — file changed since last commit |
| `A` | Added — staged and ready to commit |

### VS Code Source Control Panel
Click the **branch icon** in the left sidebar (or `Ctrl+Shift+G`):

| VS Code Action | Terminal Equivalent |
|----------------|---------------------|
| Click `+` next to file | `git add filename` |
| Type in message box + click Commit | `git commit -m "message"` |
| Click Sync Changes | `git push` |
| Discard Changes button | `git restore filename` |

### Bottom Status Bar
- `⬆️ 2` = 2 commits waiting to be pushed
- `⬇️ 1` = 1 commit on GitHub waiting to be pulled
- Branch name = your current branch (click to switch!)

---

## 🌐 Module 9 — GitHub Pages & Deployment

GitHub Pages turns your repo files into a **live website** — for free! 🌍

### Enable GitHub Pages
1. Repo → **Settings** → **Pages**
2. Source → **Deploy from branch** → select `main` → `/ (root)`
3. Click **Save**
4. Wait 1-2 minutes → your site is live!

### Your URLs
```
Personal site (1 per account):  https://USERNAME.github.io
Project sites (unlimited!):     https://USERNAME.github.io/repo-name
```

> 💡 **Tip:** Repo must be **public** for GitHub Pages to work on free accounts.

### What GitHub Pages Renders
- `README.md` → renders as homepage automatically
- `index.html` → your custom homepage
- `about.html` → `yourusername.github.io/repo/about.html`

---

## 🔥 Module 10 — Advanced Git Commands

### 🗄️ git stash — The Pause Button
> 💡 **Analogy:** A temporary drawer. Hide unfinished work, do something urgent, come back later.

```bash
git stash              # ⏸️ Hide all uncommitted changes
git stash pop          # ▶️ Restore hidden changes
git stash list         # 📋 See all stashes (you can have multiple!)
git stash drop         # 🗑️ Delete a stash without restoring
git stash clear        # 🗑️ Delete ALL stashes

# Pop a specific stash
git stash pop stash@{1}
```

> ⚠️ **Important:** Stashes are LOCAL only — never pushed to GitHub!

### 🍒 git cherry-pick — Steal One Commit
> 💡 **Analogy:** Pick only the best cherries from the tree — not the whole branch!

```bash
git cherry-pick abc1234    # Copy ONE specific commit to current branch
```

**When to use:** You need ONE complete, tested commit from another branch — not the whole branch.  
**When NOT to use:** Commit is incomplete or needs review → use a PR instead!

> 💡 **Note:** Cherry-pick creates a NEW hash — it's a copy, not a move. Original commit stays untouched.

### 🔄 git rebase — Clean History
> 💡 **Analogy:** Instead of a messy merge commit, rebase **replays** your commits on top of the latest main — like they were written after, not before.

```bash
# Update your feature branch with latest main (clean way)
git switch main
git pull                          # Get latest from GitHub
git switch feature/my-work
git rebase main                   # Replay your commits on top of main
```

| | `git merge main` | `git rebase main` |
|--|--|--|
| Creates merge commit? | ✅ Yes (messy) | ❌ No (clean!) |
| Hashes change? | ❌ No | ✅ Yes |
| Safe for shared branches? | ✅ Always | ⚠️ Own branches only |

> ⚠️ **Golden rule:** Never rebase a branch other people are working on — it changes hashes and breaks their repos!

### 🔍 git bisect — Find the Bug Commit
> 💡 **Analogy:** Binary search for your codebase. Finds the exact commit that broke something in just ~7 steps even across 1000 commits!

```bash
git bisect start              # Start detective mode 🕵️
git bisect bad                # Current version is broken
git bisect good abc1234       # This old commit was working

# Git jumps to middle commit → you test → tell Git the result
git bisect good               # This version works ✅
git bisect bad                # This version is broken ❌
# Repeat until Git finds the exact bad commit!

git bisect reset              # Exit bisect mode, return to HEAD
```

---

## ⚔️ Module 11 — Merge Conflicts in Depth

### When Do Conflicts Happen?
When **two branches edit the exact same line** in the same file — Git can't decide which version to keep. It asks YOU to decide.

```
✅ Different lines edited → Git merges automatically
❌ Same line edited → CONFLICT! You must resolve manually
```

### Reading Conflict Markers
```
<<<<<<< HEAD (your current branch)
background-color: dark;
=======
background-color: light;
>>>>>>> feature/light-mode (incoming branch)
```

### Resolving in VS Code
VS Code shows clickable buttons above conflicts:
- **Accept Current Change** → keep YOUR version
- **Accept Incoming Change** → keep THEIR version  
- **Accept Both Changes** → keep both versions

After choosing:
```bash
git add filename.css                           # Stage the resolved file
git commit -m "Resolve merge conflict in filename.css"
git push
```

### git revert vs git reset

| | `git revert` | `git reset --hard` |
|--|--|--|
| Erases history? | ❌ No — adds new commit | ✅ Yes — deletes commits |
| Safe for shared repos? | ✅ Always safe | ⚠️ Dangerous on shared branches |
| Creates new commit? | ✅ Yes | ❌ No |
| **Use when** | Undoing on `main` | Undoing on your local branch |

```bash
git revert abc1234        # Safely undo a commit (keeps history) ✅
git reset --hard abc1234  # Erase commits completely ⚠️
git restore filename.txt  # Discard uncommitted changes in a file
```

> ⚠️ **Never** use `git push --force` on main — it erases your teammates' commits!

---

## 🤖 Module 12 — GitHub Actions & CI/CD

> 💡 **Analogy:** GitHub Actions is a **robot assistant** inside your repo. Write instructions (workflows) and it automatically acts whenever something happens.

**CI** = Continuous Integration → auto-run tests on every push  
**CD** = Continuous Deployment → auto-deploy when tests pass

### Workflow File Location
```
.github/
  workflows/
    ci.yml    ← your automation instructions
```

### Your First CI Workflow
```yaml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest    # Free GitHub virtual machine
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

### Common GitHub Actions Use Cases
| Use Case | What it does |
|----------|-------------|
| 🧪 Run tests | Auto-test on every push — block merge if tests fail |
| 🚀 Auto deploy | Push to main → website updates automatically |
| 🔍 Code linting | Check code style on every PR |
| 📦 Release | Tag a version → auto-publish to npm |

> 💡 **Tip:** GitHub Actions needs `workflow` scope in your Personal Access Token!

---

## 🌍 Module 13 — Open Source & Team Collaboration

### Fork vs Clone
- **Fork** = your personal COPY of someone else's repo on GitHub
- **Clone** = download a repo to your computer

### The Complete Open Source Contribution Workflow
```bash
# 1. Fork on GitHub (click Fork button)

# 2. Clone YOUR fork
git clone https://github.com/YOUR_USERNAME/repo.git

# 3. Add original repo as upstream
git remote add upstream https://github.com/ORIGINAL_OWNER/repo.git

# 4. Verify remotes
git remote -v
# origin   → your fork
# upstream → original repo

# 5. Keep your fork up to date
git switch main
git fetch upstream
git merge upstream/main

# 6. Create a branch and make changes
git switch -c fix/your-fix
# ... make changes ...
git add .
git commit -m "Fix: describe what you fixed"

# 7. Push to YOUR fork
git push -u origin fix/your-fix

# 8. Open PR from your fork → original repo on GitHub
```

### Essential Repo Files
| File | Purpose | When? |
|------|---------|-------|
| `README.md` | Project overview, install, usage | Always ✅ |
| `LICENSE` | How others can use your code | Always ✅ |
| `.gitignore` | Files Git should never track | Always ✅ |
| `CONTRIBUTING.md` | How to contribute | Open source |
| `CHANGELOG.md` | Version history | Releases |

### Branch Protection Rules
Protect your `main` branch so nobody can push directly:  
Settings → Branches → Add classic branch protection rule → tick:
- ✅ Require pull request before merging
- ✅ Block force pushes
- ✅ Restrict deletions

> ⚠️ **Important:** Always `pwd` before cloning — never clone a repo inside another repo!

---

## ⭐ Module 14 — Pro Tips, Aliases & Copilot

### ⚡ Git Aliases — Work at Lightning Speed
```bash
# Set up shortcuts (run once)
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.sw switch
git config --global alias.lg "log --oneline --graph --decorate --all"

# Now use them:
git st          # instead of: git status
git lg          # beautiful visual branch graph 🌳
git sw main     # instead of: git switch main
```

### 🙈 .gitignore — Never Push These Files!
```bash
# Mac system files
.DS_Store

# Environment variables — NEVER push these!
.env
.env.local

# Node modules — auto generated, huge!
node_modules/

# Build output
dist/
build/

# Logs
*.log

# VS Code settings
.vscode/
```

> ⚠️ **Critical:** Never push `.env` files! They contain passwords and API keys. If you accidentally do — change all secrets immediately!

### 🔧 Fix Last Commit Message
```bash
git commit --amend -m "Corrected commit message"
git push --force origin feature/your-branch  # Only on YOUR branch, never main!
```

### 🤖 GitHub Copilot Tips
- Write a comment describing what you want → Copilot writes the code
- Press `Tab` to accept a suggestion
- Press `Esc` to reject
- `Ctrl+Enter` → see multiple suggestions
- Always review Copilot's code — it's impressive but not always correct!

**Get Copilot free:**
- Students: [education.github.com](https://education.github.com) → free Pro access
- Everyone: [github.com/settings/copilot](https://github.com/settings/copilot) → free tier (2000 completions/month)

### 👤 Profile README
Create a repo named **exactly** your GitHub username → README.md shows on your profile!
```
Kari3as/Kari3as/README.md → shows at github.com/Kari3as
```

### 🏅 Quick Reference — Most Used Commands
```bash
# Daily workflow
git status                    # What changed?
git add .                     # Stage everything
git commit -m "message"       # Save snapshot
git push                      # Send to GitHub
git pull                      # Get from GitHub

# Branching
git switch -c feature/name    # Create + switch branch
git switch main               # Go back to main
git merge feature/name        # Merge branch into current
git branch -d feature/name    # Delete local branch

# History
git log --oneline             # See commits
git show abc1234              # See a specific commit
git diff                      # See uncommitted changes

# Fixing mistakes
git restore filename          # Discard file changes
git revert abc1234            # Safely undo a commit
git stash                     # Temporarily hide changes
git stash pop                 # Bring changes back
```

---

<div align="center">

## 🏆 You Made It — Zero to Hero!

If this cheatsheet helped you, please ⭐ **star this repo** so others can find it!

[![GitHub](https://img.shields.io/badge/Made%20by-Kari3as-1a472a?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Kari3as)
[![LinkedIn Learning](https://img.shields.io/badge/Course-LinkedIn%20Learning-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/learning)

> *"The best time to start was yesterday. The second best time is now."* 🚀

**Built with ❤️ through real hands-on learning — every command in this guide was actually typed, tested, and debugged.**

</div>
