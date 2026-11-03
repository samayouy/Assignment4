
# Assignment 4 — Team Collaboration Guide


**Important:**
- Always work on your own branch.

## 2. First-Time Branch Setup (Only Once)

Everyone has already cloned the repository. **Do not clone it again.**

The three personal branches have already been created on GitHub. You only need to connect your local repository to your assigned branch.

### Step 1: Open the project folder

Open PowerShell, Git Bash, or VS Code Terminal.

Navigate to your existing `Assignment4` folder.

For example, on Windows:

```powershell
cd "$HOME\Assignment4"
```

On macOS/Linux:

```bash
cd ~/Assignment4
```

If your repository is located somewhere else, navigate to that folder instead.

### Step 2: Fetch the existing GitHub branches

```bash
git fetch origin
```

This downloads information about all branches from GitHub without changing your files.

### Step 3: Switch to your assigned branch

Replace `YOUR_BRANCH_NAME` with your actual branch name on GitHub.

```bash
git switch --track origin/YOUR_BRANCH_NAME
```

For example, if your assigned branch is `Stanley-Wang`:

```bash
git switch --track origin/Stanley-Wang
```

This creates a local working branch connected to your **already existing remote branch** on GitHub.

You are not creating another branch on GitHub.

If your local branch already exists, simply use:

```bash
git switch YOUR_BRANCH_NAME
```

### Step 4: Verify your branch

```bash
git branch --show-current
```

The output should show your own branch name, not `main`.

**You only need to complete this setup once.**

**Note:** If Git prevents you from switching branches because of uncommitted changes, save or commit those changes first. Do not discard your existing work.

---

## 3. Every Time You Want to Edit

Follow these steps **every time you start a new editing session**.

### Step 1: Open a terminal in the project folder

Navigate to the `Assignment4` folder.

On Windows:

```powershell
cd "$HOME\Assignment4"
```

On macOS/Linux:

```bash
cd ~/Assignment4
```

### Step 2: Switch to your own branch

```bash
git switch YOUR_BRANCH_NAME
```

Verify your branch:

```bash
git branch --show-current
```

**Make sure you are on your own branch before editing.**

### Step 3: Pull the latest changes from your branch

```bash
git pull --ff-only origin YOUR_BRANCH_NAME
```

This downloads any changes previously uploaded to your branch.

Make sure you have committed or safely saved your previous work before pulling.

### Step 4: Synchronize with the latest main branch

Other members may have merged their work into `main` since your last editing session.

To download their latest changes:

```bash
git fetch origin
git merge origin/main
```

If your branch is already up to date, Git will display:

```
Already up to date.
```

If Git reports a merge conflict, stop and resolve it before continuing. Do not overwrite your teammates' changes.

You do not need to merge if `main` has not changed, but checking for updates is recommended.

### Step 5: Start Julia

From inside the `Assignment4` folder, run:

```bash
julia
```

### Step 6: Launch Jupyter Notebook

Inside the **Julia REPL (not PowerShell)**, run:

```julia
using IJulia
notebook(dir=pwd())
```

This launches Jupyter Notebook in your current `Assignment4` folder.

Open:

```
A04.ipynb
```

### Step 7: Edit and save

Work on your assigned exercises.

Remember to **save the notebook** before committing your changes.

---

## 4. Every Time You Finish Editing: Upload Your Changes

After saving your notebook, open another terminal in the same `Assignment4` folder.

### Step 1: Check your branch and changes

```bash
git branch --show-current
git status
```

Make sure you are on your own branch.

### Step 2: Stage your changes

If you only edited the notebook:

```bash
git add A04.ipynb
```

If you also want to upload other modified files:

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

Use a meaningful commit message describing your work.

### Step 4: Push to your own branch

```bash
git push origin YOUR_BRANCH_NAME
```

Replace `YOUR_BRANCH_NAME` with your assigned branch name.

**Done!** Your changes have now been uploaded to your personal branch on GitHub.

You can repeat this process as often as needed.

**Important:** Pushing to your own branch does not modify `main`.

---

## 5. How to Merge Your Work into Main (Pull Request)

When your work is complete and ready to become part of the final assignment:

1. Open the GitHub repository:
   https://github.com/samayouy/Assignment4
2. Click **Pull requests**.
3. Click **New pull request**.
4. Select:
   - **Base:** `main`
   - **Compare:** Your own branch
5. Review the changes carefully.
6. Click **Create pull request**.
7. Ask another group member to review your changes.
8. Once everything is correct, click **Merge pull request**.
9. Click **Confirm merge**.

Your completed work is now part of `main`.

**Important:**
- Do not delete your personal branch after merging.
- We will continue using the same branches throughout the assignment.
- Do not merge if GitHub reports unresolved conflicts.
- Make sure your Pull Request does not accidentally remove another member's work.

---

## 6. How to Get Teammates' Latest Work

After another member merges their Pull Request into `main`, their changes become part of the shared final version.

To get these changes into your own branch, run:

```bash
git switch YOUR_BRANCH_NAME
git fetch origin
git merge origin/main
```

If the merge succeeds, update your branch on GitHub:

```bash
git push origin YOUR_BRANCH_NAME
```

Your branch now includes the latest changes from `main`.

**Note:** This synchronization is also included in the daily workflow in Section 3, so you can simply follow those steps before each editing session.

---

## 7. Important Notes About Jupyter Notebook Collaboration

We are working with the same `A04.ipynb` file.

Although separate branches allow us to edit independently, **merge conflicts can still occur** if multiple members modify overlapping parts of the same notebook.

To minimize conflicts:

1. Focus on your assigned exercises.
2. Avoid modifying another member's cells unless necessary.
3. Avoid unnecessary changes to notebook structure or cell order.
4. Save, commit, and push your work regularly.
5. Synchronize your branch with `main` before starting a new editing session.
6. Coordinate with teammates when resolving merge conflicts.
7. Do not force-push or overwrite another member's work.

If a notebook merge conflict occurs, ask the group before resolving it. Do not blindly accept one version, as this may delete another member's work.

---

## 8. Team Collaboration Rules

1. **Always work on your own branch.** Never push directly to `main`.
2. **Pull before editing.** Download the latest changes before starting Julia.
3. **Save before committing.** Always save `A04.ipynb` before using Git.
4. **Commit and push regularly.** Do not wait until the deadline.
5. **Use descriptive commit messages.** For example, `"Complete exercise 3"`.
6. **Use Pull Requests.** Completed work must be reviewed before merging into `main`.
7. **Keep personal branches.** Do not delete your assigned branch after merging.
8. **Respect other members' work.** Resolve conflicts carefully.
9. **Keep `main` stable.** The final `main` should contain the complete, tested assignment.

---

## 9. Quick Reference — Daily Workflow

Replace `YOUR_BRANCH_NAME` with your assigned branch name.

### Every time you start editing

Open a terminal in `Assignment4`:

```bash
git switch YOUR_BRANCH_NAME
git pull --ff-only origin YOUR_BRANCH_NAME
git fetch origin
git merge origin/main
julia
```

Inside Julia:

```julia
using IJulia
notebook(dir=pwd())
```

Open `A04.ipynb`, edit your exercises, and save.

### Every time you finish editing

Open another terminal in `Assignment4`:

```bash
git add A04.ipynb
git commit -m "Describe your changes"
git push origin YOUR_BRANCH_NAME
```

### When your work is ready for the final version

On GitHub:

1. Open **Pull requests → New pull request**.
2. Select `base: main` and `compare: YOUR_BRANCH_NAME`.
3. Create the Pull Request.
4. Review and merge it into `main`.

---

## 10. Complete Workflow Summary

**First time only:**

```
Open existing Assignment4 folder
    ↓
git fetch origin
    ↓
git switch --track origin/YOUR_BRANCH_NAME
    ↓
Local branch is ready
```

**Every editing session:**

```
Switch to your own branch
    ↓
Pull latest changes
    ↓
Synchronize with main
    ↓
Start Julia
    ↓
using IJulia; notebook(dir=pwd())
    ↓
Edit A04.ipynb
    ↓
Save
    ↓
Git add + commit + push
    ↓
Changes saved to your personal GitHub branch
```

**When ready to merge:**

```
Personal Branch
    ↓
Create Pull Request
    ↓
Review Changes
    ↓
Merge into main
    ↓
Other members synchronize their branches
```

**Remember: Always work on your assigned branch and use Pull Requests to update `main`.**
