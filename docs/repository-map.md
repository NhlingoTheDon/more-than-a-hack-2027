# Repository Structure & File Guide

## 1. Purpose

This document explains the structure of the More Than A Hack 2027 repository and identifies the purpose of its important files.

Its purpose is to help team members understand where to find existing functionality and where to contribute.

## 2. Main Repository Structure

```text
more-than-a-hack-2027/
│
├── data/                  # Downloaded match assets
├── evaluation/            # Scoring, validation and ground truth
├── starter/               # Data loaders, baselines and notebooks
├── docs/                  # Team documentation
│
├── games.py               # Match configuration and frame alignment
├── README.md              # Main project documentation
├── CHALLENGE.md           # Challenge description
├── DATA.md                # Dataset documentation
├── EVALUATION.md          # Scoring documentation
├── SUBMISSION.md          # Submission requirements
├── RULES.md               # Competition rules
├── FAQ.md                 # Frequently asked questions
├── OVERVIEW.md            # Competition overview
│
├── requirements.txt       # Main dependencies
├── requirements-starter.txt
├── .gitignore
├── LICENSE
└── CITATION.cff
```

## 3. Important Directories

### evaluation/

Responsible for evaluating and validating possession predictions.

| File | Responsibility |
|---|---|
| possession_metrics.py | Defines the evaluation metrics |
| run_evaluation.py | Runs the scoring process |
| validate_submission.py | Validates prediction CSV files |
| gt/ | Contains public ground-truth labels |
| results/ | Stores baseline and prediction CSV files |

### starter/

Contains the reference implementation and tools for exploring the match data.

| File | Responsibility |
|---|---|
| baseline.py | Generates reference predictions |
| load_atd.py | Loads and aligns tracking data |
| load_smart_tagging.py | Loads tactical tagging information |
| load_homography.py | Loads pitch coordinate transformations |
| utils.py | Provides plotting utilities |
| 01_smart_tagging.ipynb | Explores tactical tagging |
| 02_tracking_atd.ipynb | Explores tracking data |
| 03_first_submission.ipynb | Demonstrates the first submission workflow |

### data/

Stores downloaded match assets.

The data is distributed separately and should not be committed to Git.

### docs/

Stores additional team documentation, including this repository map.

## 4. Important Root-Level Files

| File | Responsibility |
|---|---|
| games.py | Defines match configuration, asset paths and frame alignment |
| README.md | Main project introduction and setup |
| CHALLENGE.md | Explains the prediction problem |
| DATA.md | Describes the available datasets |
| EVALUATION.md | Explains evaluation metrics |
| SUBMISSION.md | Defines submission requirements |
| RULES.md | Defines competition restrictions |
| FAQ.md | Answers common questions |
| OVERVIEW.md | Provides competition context |
| requirements.txt | Main Python dependencies |
| requirements-starter.txt | Additional starter dependencies |
| .gitignore | Defines ignored files and folders |

## 5. Where Should We Work?

| Development activity | Location |
|---|---|
| New prediction algorithms | starter/ |
| Tracking data loading | starter/load_atd.py |
| Tactical information | starter/load_smart_tagging.py |
| Pitch coordinate processing | starter/load_homography.py |
| Baseline predictions | starter/baseline.py |
| Evaluation | evaluation/run_evaluation.py |
| Evaluation metrics | evaluation/possession_metrics.py |
| Submission validation | evaluation/validate_submission.py |
| Prediction comparisons | evaluation/results/ |
| Match configuration | games.py |
| Team documentation | docs/ |

## 6. Basic Project Workflow

1. Load match information using the starter loaders.
2. Process the tracking, tactical and other available information.
3. Develop an algorithm to predict possession.
4. Generate a prediction CSV.
5. Validate the prediction using `evaluation/validate_submission.py`.
6. Evaluate the prediction using `evaluation/run_evaluation.py`.
7. Compare results against the provided baselines.

## 7. Important Notes

- The tactical video is the reference for submission frame numbering.
- `games.py` handles the alignment between tracking IDs and video frames.
- Match data is downloaded separately and must not be committed.
- The public ground truth is for checking the pipeline, not training or tuning.
- The evaluation scripts should be treated as the scoring reference.

## 8. Quick Reference

**starter/** = Build predictions.

**evaluation/** = Validate and score predictions.

**evaluation/results/** = Store and compare prediction files.

**games.py** = Shared match configuration and frame alignment.

**data/** = Match assets.

**docs/** = Team documentation.

---

This document is intended as a quick reference for all team members contributing to the project.