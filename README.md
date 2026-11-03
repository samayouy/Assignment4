
# Assignment 4 — Team Collaboration Guide

This repository is shared by three group members. We use separate Git branches to work independently and Pull Requests to merge our work into `main`.

## 1. Branch Structure

| Branch | Purpose |
|---|---|
| `main` | Final version of the assignment |
| `Student1` | Student 1's working branch |
| `Student2` | Student 2's working branch |
| `Student3` | Student 3's working branch |

**Important rules:**
- Each student must work on their own branch.
- Do not commit or push directly to `main`.
- All changes to `main` should go through Pull Requests.
- We are working with the same `A04.ipynb` notebook. Separate branches allow independent editing, but Git merge conflicts may still occur if multiple people modify the same notebook.

## 2. First-Time Setup (Only Once)

Everyone has already cloned the repository, so **do not clone it again**.

### Step 1: Open the project folder

Open a terminal (PowerShell, Git Bash, or VS Code Terminal).

On Windows (if the repository is in your home directory):

```powershell
cd "$HOME\Assignment4"
```

On macOS/Linux:

```bash
cd ~/Assignment4
```

If you cloned the repository somewhere else, navigate to that folder instead.

### Step 2: Fetch all branches

```bash
git fetch origin
```

### Step 3: Switch to your assigned branch

Choose **only your own branch**.

Xuege Xu:

```bash
git switch --track origin/Xuege Xu
```

Chongwei Chen:

```bash
git switch --track origin/Chongwei Chen
```

Stanley Wang:

```bash
git switch --track origin/Stanley Wang
```

This creates a local branch that tracks the corresponding remote branch.

Verify your current branch:

```bash
git branch --show-current
```

The output should be your assigned branch name, not `main`.

You only need to perform this setup once.

---

## 3. Every Time You Want to Edit

Follow these steps **every time you start a new editing session**.

### Step 1: Open a terminal in the project folder

On Windows:

```powershell
cd "$HOME\Assignment4"
```

On macOS/Linux:

```bash
cd ~/Assignment4
```

### Step 2: Switch to your own branch

For example, Student 2 runs:

```bash
git switch Student2
```

Students 1 and 3 should replace `Student2` with their own branch names.

Check your branch:

```bash
git branch --show-current
```

**Always verify that you are on your own branch before editing.**

### Step 3: Download the latest changes

First, pull updates from your own remote branch:

```bash
git pull --ff-only origin Student2
```

Then fetch the latest information from GitHub:

```bash
git fetch origin
```

Merge any new changes from `main` into your own branch:

```bash
git merge origin/main
```

If `main` has not changed, Git will report `Already up to date.`

If a merge conflict occurs, resolve it before continuing. Do not overwrite your teammates' work.

**Note:** Replace `Student2` with your own branch name. Make sure your previous work has been committed before pulling or merging.

### Step 4: Start Julia

From inside the `Assignment4` folder, run:

```bash
julia
```

### Step 5: Launch Jupyter Notebook

In the **Julia REPL (not PowerShell)**, run:

```julia
using IJulia
notebook(dir=pwd())
```

This launches Jupyter Notebook in the current `Assignment4` folder.

Open `A04.ipynb`.

### Step 6: Edit and save

Make your changes in the notebook.

**Remember to save your notebook before uploading your changes.**

---

## 4. Every Time You Finish Editing: Upload Your Changes

After saving your notebook, open another terminal in the same `Assignment4` folder.

### Step 1: Check your current branch and changes

```bash
git branch --show-current
git status
```

Make sure you are on your own branch.

### Step 2: Stage your changes

```bash
git add A04.ipynb
```

If you also modified other files that should be uploaded, you can use:

```bash
git add .
```

### Step 3: Commit your changes

```bash
git commit -m "Describe what you changed"
```

For example:

```bash
git commit -m "Complete exercise 2"
```

### Step 4: Push to your own branch

For Student 2:

```bash
git push origin Student2
```

Replace `Student2` with your own branch name.

**Done!** Your changes are now uploaded to GitHub on your personal branch.

You can repeat this process as often as needed.

Your changes will not affect `main` until they are merged through a Pull Request.

---

## 5. How to Merge Your Work into Main (Pull Request)

When your work is ready to be included in the final assignment:

1. Go to the GitHub repository:
   https://github.com/samayouy/Assignment4
2. Click **Pull requests**.
3. Click **New pull request**.
4. Select:
   - **Base:** `main`
   - **Compare:** Your own branch (`Student1`, `Student2`, or `Student3`)
5. Review the changes.
6. Click **Create pull request**.
7. Ask another team member to review your changes.
8. After review, click **Merge pull request**.

**Important:**
- Do not delete your personal branch after merging.
- We will continue using the same three branches throughout the assignment.
- If GitHub reports merge conflicts, resolve them before merging.
- Do not merge a Pull Request if it contains unintended changes or removes a teammate's work.

---

## 6. How to Get Teammates' Latest Work

When another student's Pull Request has been merged into `main`, their changes become part of the shared final version.

To get those changes into your own branch, run:

```bash
git switch Student2
git fetch origin
git merge origin/main
```

If everything merges successfully, upload your updated branch:

```bash
git push origin Student2
```

Replace `Student2` with your own branch name.

This ensures your branch includes the latest work from `main`.

**Note:** Because everyone is editing `A04.ipynb`, merging may occasionally produce conflicts. If this happens, coordinate with teammates to resolve the conflicting notebook changes.

---

## 7. Team Collaboration Rules

1. **Always work on your own branch.** Never edit directly on `main`.
2. **Pull before editing.** Make sure your branch is up to date before starting Julia.
3. **Save before committing.** Always save your Jupyter Notebook before running Git commands.
4. **Commit and push regularly.** Do not leave all your changes uncommitted until the deadline.
5. **Use descriptive commit messages.** For example, `"Complete exercise 1"` rather than `"Update"`.
6. **Coordinate notebook editing.** Avoid modifying the same cells as another team member at the same time, even when using separate branches.
7. **Use Pull Requests.** Review changes before merging into `main`.
8. **Do not delete other members' work.** Resolve conflicts carefully.
9. **Keep `main` stable.** The final `main` branch should contain the complete, tested assignment.

---

## 8. Quick Reference: Daily Commands

Replace `Student2` with your assigned branch name.

### Before editing

```bash
cd Assignment4
git switch Student2
git pull --ff-only origin Student2
git fetch origin
git merge origin/main
julia
```

Then, inside Julia:

```julia
using IJulia
notebook(dir=pwd())
```

### After editing and saving

Open another terminal inside `Assignment4`:

```bash
git add A04.ipynb
git commit -m "Describe your changes"
git push origin Student2
```

**Workflow summary:**

`Switch to your branch → Pull & Sync → Start Julia → Edit → Save → Commit → Push → Pull Request → Merge into main`
