# Git & GitHub Setup Guide

## Initial Git Installation

### 1. Download and Install Git
- Navigate to https://git-scm.com/downloads
- Download version for your platform (Windows, Mac, or Linux)
- Perform "push-through" install accepting all default options

**Alternative installs:**
- RedHat/CentOS/AlmaLinux: `sudo dnf install git`
- Ubuntu: `sudo apt install git`
- MacOS (with Homebrew): `brew install git`

### 2. Configure Git
Open terminal in VS Code (Ctrl + `)

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@students.westerntc.edu"
```

## Creating a GitHub Account

1. Visit https://github.com
2. Click "Sign up" in upper-right corner
3. Provide: username, email, password
4. Verify email address
5. Complete account setup

## Linking GitHub to Local Git (SSH Setup)

### 1. Generate SSH Key
Open Git Bash terminal in VS Code

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- Press Enter to accept default location
- Set passphrase or leave blank

### 2. Start SSH Agent

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

### 3. Add SSH Key to GitHub

Copy your public key:
```bash
cat ~/.ssh/id_rsa.pub
```

On GitHub:
- Go to Settings → SSH and GPG keys
- Click "New SSH key"
- Paste key into "Key" field
- Add title (e.g., "DevOps SSH Key")
- Click "Add SSH key"

### 4. Verify Connection

```bash
ssh -T git@github.com
```

Should see: "You've successfully authenticated"

## Creating a Local Repository

### 1. Create Project Directory

```bash
mkdir -p devops/lab1
cd devops/lab1
```

### 2. Initialize Repository

```bash
git init
```

Creates hidden .git folder storing version history

### 3. Add Files to Repository

```bash
git add .              # Adds all files
git add filename.ext   # Adds specific file
```

## Making Commits

### 1. Create/Modify Files

```bash
code -r TOC.MD         # Opens file in VS Code
```

### 2. Stage Changes

```bash
git add .              # Stage all changes
git add TOC.MD         # Stage specific file
```

### 3. Commit Changes

```bash
git commit -m "initial files"
git commit -m "Added markdown to table of contents"
```

### 4. View Commit History

```bash
git log
```

## Creating a GitHub Repository

### 1. Create Repository on GitHub
- Click green "New" button in dashboard
- Name repository (e.g., "my-first-repo")
- Choose public or private
- Check "Add a README file"
- Click "Create repository"

### 2. Clone Repository Locally

```bash
git clone git@github.com:username/repo-name.git
cd repo-name
```

### 3. Verify Files

```bash
ls                     # List files in directory
```

## Pushing Changes to GitHub

### 1. Modify Files
Edit files in your text editor

### 2. Stage, Commit, and Push

```bash
git add .
git commit -m "Updated README.md with project description"
git push origin main
```

### 3. Verify on GitHub
Refresh repository page on GitHub to see changes

## Common Commands Quick Reference

| Command | Purpose |
|---------|---------|
| `git init` | Initialize new repository |
| `git clone [url]` | Clone existing repository |
| `git add .` | Stage all changes |
| `git add [file]` | Stage specific file |
| `git commit -m "[message]"` | Commit staged changes |
| `git push origin main` | Push commits to GitHub |
| `git log` | View commit history |
| `git status` | Check repository status |
| `cd ..` | Navigate up one directory |
| `mkdir [name]` | Create directory |
| `ls` | List directory contents |

## Navigation Tips

- Open terminal in VS Code: `Ctrl + `` (backtick)
- Navigate up one folder: `cd ..`
- Create folder with spaces: `mkdir "Folder Name"`
- Navigate into folder: `cd "Folder Name"`

## Troubleshooting

**SSH key issues:**
- Ensure you copied the entire public key (starts with `ssh-rsa`)
- Verify email matches GitHub account
- Check SSH agent is running

**Push fails:**
- Verify remote URL: `git remote -v`
- Check you have write access to repository
- Ensure you're on correct branch

**Commit fails:**
- Check files are staged: `git status`
- Ensure commit message is in quotes
- Verify git config is set (name and email)