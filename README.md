2. Install [Julia](https://julialang.org/downloads/) and [Git](https://git-scm.com/downloads) if needed. Make sure you can run `julia` and `git --version` from a terminal.
3. Open **PowerShell** (Windows) or **Terminal** (macOS/Linux), and configure Git if this is your first time using it:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-github-email@example.com"
   ```

4. Clone the repository to your computer:

   ```bash
   git clone https://github.com/samayouy/Assignment4.git
   cd Assignment4
   ```

   On the first clone or push, Git may ask you to sign in to GitHub through your browser.

5. Start Julia from **inside the `Assignment4` folder**:

   ```bash
   julia
   ```

6. In the **Julia REPL** (not in PowerShell), run:

   ```julia
   using IJulia
   notebook(dir=pwd())
   ```

   If IJulia is not installed, run `import Pkg; Pkg.add("IJulia")` once in Julia and then retry. Open the assignment `.ipynb` file in the browser, and select the **Julia** kernel.

## 2. Every time you want to edit

**Before starting:** Confirm that no one else is currently editing the shared notebook. We will take turns editing **the same `.ipynb` file** to prevent Git merge conflicts.

1. Open a **new terminal** and enter the cloned project folder. On Windows, if you cloned it from your home directory as shown above:

   ```powershell
   cd "$HOME\Assignment4"
   ```

   On macOS/Linux, use `cd ~/Assignment4` (if cloned to your home directory).

2. Check your local state and download teammates' latest changes **before opening the notebook**:

   ```bash
   git status
   git pull
   ```

   Only run `git pull` if you have no uncommitted changes. If `git status` shows local changes, save/commit them or coordinate with the group first.

3. From that same folder, launch Julia:

   ```bash
   julia
   ```

4. In the Julia REPL:

   ```julia
   using IJulia
   notebook(dir=pwd())
   ```

5. Open the shared `.ipynb`, edit your assigned question(s), run/check your code, and **save (`Ctrl+S` / `Cmd+S`)**.

## 3. When you finish editing: share your changes

1. Make sure the notebook is saved in Jupyter.
2. Open **another terminal** in the same `Assignment4` folder (keep Jupyter running if needed).
3. Run:

   ```bash
   git status
   git add *.ipynb
   git commit -m "Complete Question X"
   git push
   ```

   Replace `X` with your question number (or describe your changes). `git add *.ipynb` stages notebook files in the project folder; use the exact notebook filename instead if there is more than one notebook.

4. Refresh the repository page on GitHub to confirm that your latest commit appears.
5. **Tell the group that you have pushed and the next person can start.**

> **Important:** Saving in Jupyter only saves the local file. The other group members will see your changes on GitHub **only after you `git commit` and `git push`**. They must run **`git pull`** to bring those changes to their own computers.

## 4. Collaboration rules

- **One editor at a time** for our shared `.ipynb` file. Coordinate in the group chat.
- **Pull before editing; commit and push after editing.**
- Close the notebook tab (and stop its kernel) before pulling someone else's changes; reopen the updated notebook afterward.
- Keep the original assignment questions and notebook structure intact. Only modify your assigned section unless we agree otherwise.
- **Never use `git push --force`** on the shared branch.
- If `git pull` or `git push` reports a conflict or rejected push, **stop and message the group**. Do not overwrite others' work.
- If the repo includes `Project.toml` (and optionally `Manifest.toml`), run `import Pkg; Pkg.activate("."); Pkg.instantiate()` in the notebook before using its packages.

## 5. Before final submission

The final reviewer should pull the latest version, open the notebook with the Julia kernel, **restart the kernel and run all cells in order**, check all answers/plots for errors, save, push any final corrections, and submit the `.ipynb` file required by the instructor.

### Quick reference

```text
START:  cd to Assignment4  →  git status  →  git pull  →  start Julia/Jupyter
EDIT:   edit + run notebook  →  save in Jupyter
FINISH: git add  →  git commit  →  git push  →  notify teammates
```
