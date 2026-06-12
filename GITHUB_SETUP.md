# 🚀 GitHub Setup Guide

## Prerequisites

Before pushing to GitHub, ensure you have:

1. **Git installed** - Download from https://git-scm.com/download/win
2. **GitHub account** - Create one at https://github.com
3. **GitHub CLI (optional)** - Easier authentication: https://cli.github.com/

---

## Step 1: Install Git (if not already installed)

### Option A: Download from git-scm.com
- Go to https://git-scm.com/download/win
- Run the installer
- Use default settings
- Restart your terminal/PowerShell

### Option B: Using Windows Package Manager
```powershell
winget install Git.Git
```

### Option C: Using Chocolatey
```powershell
# First install Chocolatey if needed
choco install git
```

**Verify installation:**
```powershell
git --version
```

---

## Step 2: Configure Git

```powershell
# Set your name and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --global --list
```

---

## Step 3: Create GitHub Repository

1. Go to https://github.com/new
2. **Repository name**: `netflix-recsys` (or your preferred name)
3. **Description**: Netflix Recommendation System with SVD and NeuMF models
4. **Visibility**: Public (or Private if preferred)
5. **Initialize**: Do NOT initialize with README (we already have one)
6. Click "Create repository"

**Copy the repository URL** - You'll need it in the next step

---

## Step 4: Push Your Code to GitHub

```powershell
# Navigate to your project folder
cd d:\open_project\netflix

# Initialize git (if not already initialized)
git init

# Configure for this repository only (optional)
git config user.name "Your Name"
git config user.email "your.email@example.com"

# Add all files
git add .

# Create initial commit
git commit -m "Netflix recommendation system: SVD & NeuMF models with full results"

# Rename branch to main (if needed)
git branch -M main

# Add remote repository (replace with YOUR repository URL)
git remote add origin https://github.com/YOUR_USERNAME/netflix-recsys.git

# Push to GitHub
git push -u origin main
```

---

## Step 5: Verify on GitHub

1. Go to your repository URL: `https://github.com/YOUR_USERNAME/netflix-recsys`
2. You should see all your files including:
   - `netflix_recsys_complete (1).ipynb`
   - `RESULTS_SUMMARY.md`
   - `results/` folder with outputs
   - `requirements (3).txt`
   - `README (6).md`

---

## Common Issues & Solutions

### Issue: "fatal: not a git repository"
**Solution**: Run `git init` first, then try again

### Issue: "fatal: Could not read Username"
**Solution**: Set your git credentials
```powershell
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Issue: Authentication fails
**Solution**: Use GitHub CLI for easier auth
```powershell
# Install GitHub CLI
winget install GitHub.cli
# Or use this in PowerShell
gh auth login
```

### Issue: "The remote does not support push"
**Solution**: Verify your remote URL
```powershell
git remote -v
git remote set-url origin https://github.com/YOUR_USERNAME/netflix-recsys.git
```

### Issue: Large files rejected by GitHub
**Solution**: Git LFS (Large File Storage)
```powershell
git lfs install
git lfs track "*.pkl" "*.pt"
git add .gitattributes
git commit -m "Add LFS tracking for large files"
git push
```

---

## Future Updates

To push new changes after execution:

```powershell
# Make sure all changes are saved
git status

# Add changed files
git add .

# Commit with descriptive message
git commit -m "Update: improved model results with new hyperparameters"

# Push to GitHub
git push origin main
```

---

## Recommended GitHub Settings

1. **Add a proper README** - Document your project
2. **Add LICENSE** - Choose MIT, Apache, or GPL
3. **Add CONTRIBUTING.md** - Guidelines for contributors
4. **Enable GitHub Pages** - Showcase results
5. **Add GitHub Actions** - Automate model training (optional)

---

## Quick Reference Commands

```powershell
# Check status
git status

# View history
git log --oneline -5

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# View remote URL
git remote -v

# Create a new branch
git checkout -b feature-name

# Switch branches
git checkout main

# Merge branches
git merge feature-name

# Delete branch
git branch -d feature-name
```

---

## Need Help?

- GitHub Docs: https://docs.github.com
- Git Documentation: https://git-scm.com/doc
- GitHub CLI: https://cli.github.com/

Happy coding! 🎉
