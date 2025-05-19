# MLOPS-DVC-DataVersion

This repo was made for learning and implementing DVC in my journey to learn MLOps

# Git + DVC Versioned Data Project

This repository demonstrates a simple workflow for managing versioned data using **Git** and **DVC (Data Version Control)**. It includes a Python script that generates a CSV file and tracks its changes over time using DVC. A local folder `s3/` is used to simulate remote storage.

## Project Structure

```
MLOPS-DVC-DataVersion/
├── data/              # Contains CSV data (tracked via DVC)
├── mycode.py          # Python script to generate/update CSV file
├── data.dvc           # DVC tracking file for the data directory
├── s3/                # Simulated DVC remote storage
├── .dvc/              # DVC internal files
├── .git/              # Git metadata
├── .gitignore         # Ignores data/ folder so it's only tracked via DVC
├── .dvcignore         # DVC ignore rules
└── README.md          # Project overview and workflow instructions
```

## Workflow Summary

### Initial Setup

1. Initialize Git and DVC.
2. Create `data/` and generate CSV using `mycode.py`.
3. Commit everything to Git.
4. Set up a local DVC remote using the `s3/` directory.

### Data Versioning Steps

- **V1**: Initial data generation and tracking with DVC.
- **V2**: Script updated to append a new row → data re-committed and pushed.
- **V3**: Another row appended → re-tracked and pushed.

## Key Commands

```bash
# Initialize project
git init
dvc init

# Create and track data
python mycode.py
dvc add data/
git rm -r --cached data/
git add .gitignore data.dvc
git commit -m "Track data with DVC"

# Set up remote
mkdir s3
dvc remote add -d myremote s3

# Commit to DVC and push
dvc commit
dvc push

# Version updates
# (Modify mycode.py, re-run script)
dvc status
dvc commit
dvc push
git add data.dvc
git commit -m "Updated data version"
```

## Requirements

- Python 3.x
- [pandas](https://pypi.org/project/pandas/)
- [DVC](https://dvc.org/)

```bash
pip install pandas dvc
```

---

Version your data like you version your code
