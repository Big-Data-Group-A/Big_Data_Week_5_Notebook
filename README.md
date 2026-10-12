# Week 5 Big Data Lab

This repository supports the fifth lab for the Introduction to Big Data Analytics course at AUCA. The work focuses on practical Python data skills, especially list comprehensions, `lambda` functions, NumPy arrays, boolean filtering, and identifying anomalies or trends in a weather dataset.

The dataset covers 60 days of Kigali weather observations from September to October 2026 and is used to practice exploratory analysis with real-world time-series data.

## Project contents

| File | Purpose |
| --- | --- |
| `Lab 3.pdf` | Week 5 assignment instructions and task sheet |
| `Week5_YourName.ipynb` | Main lab notebook containing Parts 1–6 |
| `Untitled.ipynb` | A scratch notebook used for early experiments and practice |
| `week5_kigali_weather.xlsx` | Source weather data file. The notebook expects a CSV version, so export the sheet as `week5_kigali_weather.csv` in the same directory before running it |

## Running the notebook locally

```bash
git clone https://github.com/Big-Data-Group-A/Big_Data_Week_5_Notebook.git
cd Big_Data_Week_5_Notebook

python3 -m venv .venv
source .venv/bin/activate
pip install numpy jupyter

jupyter notebook
```

Keep local environment folders such as `venv/` and `.venv/` out of version control. They are intentionally ignored by Git and should never be committed.

## Working on the repository safely

### Protected `main` branch

Direct commits and pushes to `main` are not allowed. GitHub blocks this for everyone, including administrators, and force-pushing or deleting `main` is also restricted.

All updates must be submitted through a separate branch using a pull request.

### Contribution workflow

1. Start from the latest `main` branch:

   ```bash
   git switch main
   git pull origin main
   ```

2. Create your own working branch instead of editing `main` directly. Use a short, clear name such as `yourname/part4-masking`:

   ```bash
   git switch -c yourname/part4-masking
   ```

3. Make your edits and save them in a commit on that branch:

   ```bash
   git add <files you changed>
   git commit -m "Describe what you changed"
   ```

4. Push the branch to GitHub:

   ```bash
   git push -u origin yourname/part4-masking
   ```

5. Open a pull request with `main` as the target branch and your feature branch as the source branch. The "Compare & pull request" button appears automatically after the push.

6. After the PR is reviewed and merged, update your local repository:

   ```bash
   git switch main
   git pull origin main
   ```

### If you accidentally committed to `main`

Your local commits are still safe. The remote push to `main` is simply rejected. The usual fix is to move those changes onto a branch and reset your local `main` to the remote version:

```bash
git switch -c yourname/my-changes   # preserves your work on a new branch
git branch -f main origin/main      # resets local main to match GitHub
git push -u origin yourname/my-changes
```

Then open a pull request from `yourname/my-changes` into `main`.

## Notes

- Do not commit virtual environments, `.ipynb_checkpoints/`, or other large generated artifacts.
- Before committing a notebook, verify it runs from start to finish without errors by using **Kernel → Restart & Run All**.
