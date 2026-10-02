# Big Data Week 5 Notebook

Week 5 Lab — **Advanced Python + NumPy** for *Introduction to Big Data Analytics* (AUCA).
The lab covers list comprehensions, `lambda`, NumPy arrays, boolean masking, and anomaly/trend analysis on 60 days of Kigali weather data (Sept–Oct 2026).

## Repository contents

| File | Description |
| --- | --- |
| `Lab 3.pdf` | The Week 5 lab instructions |
| `Week5_YourName.ipynb` | The lab notebook (Parts 1–6) |
| `Untitled.ipynb` | Scratch notebook with early practice cells |
| `week5_kigali_weather.xlsx` | The Kigali weather dataset. The notebook loads `week5_kigali_weather.csv`, so save/export the sheet as CSV into the same folder as the notebook before running it |

## Running the notebook

```bash
git clone https://github.com/Big-Data-Group-A/Big_Data_Week_5_Notebook.git
cd Big_Data_Week_5_Notebook

python3 -m venv .venv
source .venv/bin/activate
pip install numpy jupyter

jupyter notebook
```

The virtual environment folders (`venv/`, `.venv/`) are git-ignored — never commit them.

## ⚠️ The `main` branch is protected

**You cannot commit or push directly to `main`.** GitHub rejects any direct push, and the rule applies to everyone, including repository admins. Force-pushes and deleting `main` are also blocked.

All changes must go through a **pull request (PR)** from a separate branch.

### How to contribute

1. **Get the latest `main`**

   ```bash
   git switch main
   git pull origin main
   ```

2. **Create your own branch** (never work on `main` itself). Use a short, descriptive name such as `yourname/short-description`:

   ```bash
   git switch -c yourname/part4-masking
   ```

3. **Make your changes and commit them** on your branch:

   ```bash
   git add <files you changed>
   git commit -m "Describe what you changed"
   ```

4. **Push your branch** (not `main`):

   ```bash
   git push -u origin yourname/part4-masking
   ```

5. **Open a pull request** on GitHub with `main` as the base branch and your branch as the compare branch. The "Compare & pull request" button appears on the repo page right after you push.

6. **Merge the PR** on GitHub once it is ready. After it is merged, update your local copy:

   ```bash
   git switch main
   git pull origin main
   ```

### If you committed to `main` by mistake

Your local commits are safe — the push to `main` will simply be rejected. Move them onto a branch and reset your local `main`:

```bash
git switch -c yourname/my-changes   # keeps your commits on a new branch
git branch -f main origin/main      # resets local main to match GitHub
git push -u origin yourname/my-changes
```

Then open a pull request from `yourname/my-changes`.

### Notes

- Do not commit virtual environments, `.ipynb_checkpoints/`, or large generated files.
- Before committing a notebook, make sure it runs top to bottom without errors (**Kernel → Restart & Run All**).
