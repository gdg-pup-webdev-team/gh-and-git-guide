# Git and GitHub Guide

A step-by-step guide for contributing to GDG on Campus PUP projects using Git and GitHub. Follow this workflow for all your contributions.

---

## Prerequisites

Before you start, make sure you have:

- Git installed on your machine
- A GitHub account
- The repository URL

---

## Workshop Overview

This guide covers the essential Git and GitHub collaborative workflow, progressing from setup to submitting contributions:

1. [Collaborative Workflow: Fork and Clone](#collaborative-workflow-fork-and-clone)
2. [Understanding Branches](#understanding-branches)
3. [Staging and Committing Changes](#staging-and-committing-changes)
4. [Commits as Communication](#commits-as-communication)
5. [Writing Clear and Meaningful Commit Messages](#writing-clear-and-meaningful-commit-messages)
6. [Best Practices for Commit Frequency](#best-practices-for-commit-frequency)
7. [Pull Requests](#pull-request-explained)

Let's break down each topic.

---

## Collaborative Workflow: Fork and Clone

**Purpose:** Set up your own copy of the project so you can contribute without affecting the main repository.

### What Is a Fork?

A fork is your own copy of someone else's repository. When contributing to a shared project, you fork the repository, make your changes, and then propose merging them back via a Pull Request.

### Why Fork?

- **Safe collaboration:** You work on your own copy without affecting the main project
- **Proper permissions:** You can only push to your own fork
- **Clear workflow:** Pull Requests provide a formal review process
- **Community standard:** This is how open-source collaboration works

### Step 1: Fork the Repository

1. Go to the main repository on GitHub
2. Click the **Fork** button (top-right corner)
3. GitHub creates a copy under your account

### Step 2: Clone YOUR Fork (Not the Original)

Clone your forked repository:

```bash
git clone https://github.com/YOUR-USERNAME/gh-and-git-guide.git
cd gh-and-git-guide
```

**⚠️ Important:** Clone YOUR fork URL, not the original repository URL.

### Step 3: Add the Upstream Remote

To keep your fork updated with the original repository:

```bash
git remote add upstream https://github.com/geraldsberongoy/gh-and-git-guide.git
```

**Verify your remotes:**

```bash
git remote -v
```

You should see:

- `origin` → your fork (where you push)
- `upstream` → original repository (where you pull from)

### Step 4: Keep Your Fork Updated

Before creating a feature branch, update your local copy:

```bash
git fetch upstream
git checkout dev
git merge upstream/dev
git push origin dev
```

---

## Understanding Branches

### What Are Branches?

A branch is a separate line of development. Think of it like creating a parallel universe where you can work on your feature without affecting the main project.

### Branch Structure

| Branch      | Purpose                                | Example                      |
| ----------- | -------------------------------------- | ---------------------------- |
| **main**    | Production-ready code, stable releases | Main branch for deployment   |
| **dev**     | Development branch, testing ground     | Staging before main          |
| **feature** | New features and improvements          | `feature/add-personal-page`  |
| **bugfix**  | Bug fixes                              | `bugfix/fix-form-validation` |

### Creating and Switching Branches

**Create a new branch:**

```bash
git checkout -b feature/feature-name
```

**Switch to an existing branch:**

```bash
git checkout feature-name
```

**List all branches:**

```bash
git branch
```

### Branch Workflow

```bash
# Always start from dev
git checkout dev
git pull origin dev

# Create your feature branch
git checkout -b feature/add-personal-page

# Make your changes, commit, and push
git add .
git commit -m "feat(profile): add personal page template"
git push origin feature/add-personal-page
```

---

## Staging and Committing Changes

### Check Your Changes

First, see which files have been modified:

```bash
git status
```

This will show:

- Files you've modified (in red)
- Files you've staged for commit (in green)

### View What Changed

To see the actual changes in your files:

```bash
git diff
```

### Stage Your Changes

**Stage all changes:**

```bash
git add .
```

**Stage a specific file:**

```bash
git add <file-name>
```

### Commit Your Changes

Once staged, create a commit with a meaningful message:

```bash
git commit -m "<type>(<scope>): <description>"
```

---

## Commits as Communication

A commit is not just a code change—it's a message to your team. Each commit tells a story about what changed and why.

**Think of commits as:**

- A record of progress
- A communication tool for your team
- A snapshot of your work at a point in time
- A way to track the history of your project

Good commits make it easier for others to understand your work and for you to debug issues in the future.

---

## Writing Clear and Meaningful Commit Messages

### Commit Message Format

We follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/):

```
<type>(<scope>): <description>
```

### Commit Types

| Type         | Description                                           | Example                                |
| ------------ | ----------------------------------------------------- | -------------------------------------- |
| **feat**     | A new feature                                         | `feat(profile): add user profile page` |
| **fix**      | A bug fix                                             | `fix(nav): fix broken mobile menu`     |
| **docs**     | Documentation changes                                 | `docs(readme): update setup guide`     |
| **style**    | Code style changes (formatting, etc.)                 | `style(css): reformat spacing`         |
| **refactor** | Code changes that neither fix a bug nor add a feature | `refactor(api): simplify logic`        |
| **test**     | Adding or modifying tests                             | `test(auth): add login tests`          |
| **chore**    | Maintenance and other minor tasks                     | `chore(deps): update packages`         |

### Tips for Great Commit Messages

✅ **DO:**

- Use present tense: "Add feature" not "Added feature"
- Be specific about what changed
- Keep it concise but descriptive

❌ **DON'T:**

- Use vague messages like "update", "fix", "work"
- Write in past tense
- Make the message too long

**Examples:**

```bash
git commit -m "feat(profile): add user profile page with bio"
git commit -m "fix(navbar): resolve mobile menu alignment"
git commit -m "docs(readme): update installation instructions"
```

---

## Best Practices for Commit Frequency

### Why Commit Often?

- **Easier to debug:** Smaller changes are easier to trace if something breaks
- **Better history:** Your team can understand the progression of your work
- **Easier to review:** Small commits are easier to review in pull requests
- **Simpler merging:** Frequent commits reduce merge conflicts

### Commit Frequency Guidelines

**Commit when:**

- You complete a logical piece of work
- You fix a bug
- You finish a new feature
- You've made a meaningful change

**Not every keystroke!** Aim for commits that tell a story.

### Example Workflow

```bash
# Make a small change
# Test it locally
git add .
git commit -m "feat(profile): add name field validation"

# Make another related change
# Test it
git add .
git commit -m "feat(profile): add email field to form"

# Fix a styling issue
git add .
git commit -m "style(profile): improve form spacing"
```

---

## Pull Request Explained

### What Is a Pull Request?

A Pull Request (PR) is a way to propose changes to a project. It allows others to review your code, suggest improvements, and eventually merge your work into the main project.

**Think of it as saying:** "Hey team, I've made some changes. Please review them and let me know if they're good to merge."

### Why Use Pull Requests?

- **Code Review:** Team members can review and improve your code
- **Discussion:** Collaborate and discuss changes before merging
- **Quality Control:** Catch bugs and issues before they reach production
- **Documentation:** PRs create a record of why changes were made

### Creating a Pull Request

**Step 1: Push Your Branch to YOUR Fork**

```bash
git push origin feature/your-feature-name
```

**Step 2: Create PR on GitHub**

1. Go to the **original repository** (not your fork)
2. You'll see a banner suggesting **"Compare & pull request"** — click it
3. If you don't see it, go to the **Pull Requests** tab and click **New Pull Request**
4. Click **compare across forks**
5. Select:
   - Base repository: original repo, branch `dev` (or `main`)
   - Head repository: your fork, branch `feature/your-feature-name`
6. Add a clear title and description
7. Click **Create Pull Request**

### PR Title and Description Format

**Title:**

```
<type>(<scope>): <short description>
```

**Description:**

```markdown
## What Changed?

Brief explanation of what was added or changed.

## Screenshots (if applicable)

Add relevant screenshots or gifs.

## Checklist

- [ ] Code tested locally
- [ ] Follows project conventions
- [ ] No breaking changes
```

### Review and Merge

**For contributors:**

- Wait for team members to review your PR
- Respond to feedback and make requested changes
- Once approved, a maintainer will merge your PR

**For maintainers:**

- Review the code changes
- Leave constructive comments if needed
- Once approved, merge the PR
- Delete the branch after merging

---

## Activity: Create Your Personal Page

### Objective

Apply what you've learned by creating a personal page in the workshop repository and submitting a pull request.

### Steps

1. **Fork the repository**
   - Go to https://github.com/geraldsberongoy/gh-and-git-guide
   - Click the **Fork** button (top-right corner)
   - GitHub creates a copy under your account

2. **Clone YOUR fork (not the original)**

   ```bash
   git clone https://github.com/YOUR-USERNAME/gh-and-git-guide.git
   cd gh-and-git-guide
   ```

3. **Add the upstream remote**

   ```bash
   git remote add upstream https://github.com/geraldsberongoy/gh-and-git-guide.git
   ```

4. **Update your fork from upstream**

   ```bash
   git fetch upstream
   git checkout dev
   git merge upstream/dev
   git push origin dev
   ```

5. **Create a feature branch**

   ```bash
   git checkout -b feature/add-personal-page-your-name
   ```

6. **Add your personal page**
   - Copy the personal page template from the `templates/personal-page-template.md` file
   - Create a new file: `personal-pages/your-name.md`
   - Fill in your information (name, bio, interests, GitHub profile, etc.)

7. **Commit your changes**

   ```bash
   git add personal-pages/your-name.md
   git commit -m "feat(profile): add personal page for [Your Name]"
   ```

8. **Push to YOUR fork**

   ```bash
   git push origin feature/add-personal-page-your-name
   ```

9. **Create a Pull Request**
   - Go to the **original repository** (geraldsberongoy/gh-and-git-guide)
   - Click **Compare & pull request**
   - Select: base repo `dev` ← compare your fork's `feature/add-personal-page-your-name`
   - Add a title: `feat(profile): add personal page for [Your Name]`
   - Add a description explaining who you are
   - Click **Create Pull Request**

10. **Wait for Review**
    - A team member will review your PR
    - Make any requested changes
    - Once approved, your PR will be merged!

### Tips

- **Always fork first** — this lets you create PRs without write permissions
- Keep your personal page concise and professional
- Use the template provided to ensure consistency
- Review your changes locally before pushing
- Be responsive to feedback during the review process

---

## Common Git Commands

Here's a quick reference for commands you'll use often:

| Command                    | Purpose                                  |
| -------------------------- | ---------------------------------------- |
| `git status`               | Check the status of your files           |
| `git add <file>`           | Stage a specific file                    |
| `git add .`                | Stage all changes                        |
| `git commit -m "message"`  | Commit staged changes                    |
| `git push origin <branch>` | Push changes to your fork                |
| `git pull origin dev`      | Pull latest changes from your fork       |
| `git fetch upstream`       | Fetch updates from original repository   |
| `git merge upstream/dev`   | Merge upstream changes into local branch |
| `git checkout -b <branch>` | Create and switch to a new branch        |
| `git checkout <branch>`    | Switch to an existing branch             |
| `git branch`               | List all branches                        |
| `git log`                  | View commit history                      |
| `git diff`                 | See changes before staging               |

---

## Additional Resources

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)

---

**Ready to contribute to GDG on Campus PUP projects? Start by forking, cloning your fork, and submitting your first pull request today!**
