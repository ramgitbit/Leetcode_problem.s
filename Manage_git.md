# GitHub + VS Code LeetCode Setup

## 🎯 Goal

Connect a GitHub LeetCode repository with VS Code and push **one LeetCode solution every day**.

```text
GitHub Repository
       ↓
   Clone Locally
       ↓
      VS Code
       ↓
Solve LeetCode
       ↓
 Add → Commit → Push
       ↓
   GitHub 🔥
```

---

## 1. Check Git Installation

Open **VS Code → Terminal → New Terminal**

```bash
git --version
```

If it shows a Git version, Git is installed.

---

## 2. Clone Your GitHub Repository

Copy your repository URL from:

```text
GitHub → Repository → Code → HTTPS → Copy
```

Then run:

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

Example:

```bash
git clone https://github.com/ramgitbit/Leetcode_problem.s.git
```

---

## 3. Go Inside the Repository

```bash
cd Leetcode_problem.s
```

Check:

```bash
git status
```

If you see:

```text
On branch main
Your branch is up to date with 'origin/main'.
```

✅ Your local repository is connected to GitHub.

---

## 4. Open Repository in VS Code

Inside the repository folder:

```bash
code .
```

`.` means **current folder**.

---

## ⚠️ Common Errors

### `cd Desktop` Error

If:

```bash
cd Desktop
```

gives:

```text
Cannot find path ... Desktop
```

Don't worry. You can clone the repository from your current location.

---

### `not a git repository`

If:

```bash
git status
```

gives:

```text
fatal: not a git repository
```

You are outside the repository.

Go inside it:

```bash
cd Leetcode_problem.s
```

Then:

```bash
git status
```

---

### `destination path already exists`

If:

```text
destination path 'Leetcode_problem.s' already exists
```

The folder already exists.

Don't delete it immediately.

Run:

```bash
cd Leetcode_problem.s
git status
```

If Git shows:

```text
On branch main
Your branch is up to date with 'origin/main'.
```

✅ The repository is already connected.

---

# 🔥 Daily LeetCode Workflow

After solving one question:

```bash
git status
git add .
git commit -m "Solve LeetCode #1 - Two Sum"
git push
```

### Meaning:

```text
git status   → Check changes
git add .    → Stage changes
git commit   → Save changes locally
git push     → Upload to GitHub
```

---

# 📌 Useful Commands

```bash
git status       # Check changes
git add .        # Stage all changes
git commit -m "" # Create a commit
git push         # Push to GitHub
git pull         # Get latest changes
git remote -v    # Check GitHub connection
code .           # Open current folder in VS Code
```

---

## 🏆 Golden Rule

```text
1 LeetCode Question
        ↓
    1 Solution
        ↓
    1 Commit
        ↓
      Push
        ↓
   GitHub Streak 🔥
```

**Focus on consistency: One problem every day.**