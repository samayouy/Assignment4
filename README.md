
1. Clone the repository to your computer:

   ```bash
   git clone https://github.com/samayouy/Assignment4.git
   cd Assignment4
   ```

2. Start Julia from **inside the `Assignment4` folder**:

   ```bash
   julia
   ```

3. In the **Julia** (not in PowerShell), run:

   ```julia
   using IJulia
   notebook(dir=pwd())
   ```

## Every time you want to edit

**Before starting:** Confirm that no one else is currently editing the shared notebook. We will take turns editing **the same `.ipynb` file** to prevent Git merge conflicts.

1. Open a **new terminal** and enter the cloned project folder. On Windows, if you cloned it from your home directory as shown above:

   ```powershell
   cd "$HOME\Assignment4"
   ```

   On macOS/Linux, use `cd ~/Assignment4` (if cloned to your home directory).

2. Make sure to download teammates' latest changes **before opening the notebook**:

   ```bash
   git pull
   ```

3. From that same folder, launch Julia:

   ```bash
   julia
   ```

4. In the Julia REPL:

   ```julia
   using IJulia
   notebook(dir=pwd())
   ```

5. Edit and **save**.

## 3. When finish: upload your changes

1. Open **another terminal** in the same `Assignment4` folder.
2. Run:

   ```bash
   git add A04.ipynb
   commit -m （做了哪些更新）
   git push
   ```
