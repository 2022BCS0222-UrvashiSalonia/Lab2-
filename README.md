# Lab 2: Automated Training and Metric Reporting Using GitHub Actions

## Student Details
- **Name:** Urvashi Salonia
- **Roll Number:** 2022BCS0222  

---

## Objective
This lab demonstrates how Continuous Integration (CI) can be used to automate machine learning experiments using **GitHub Actions**. Each experiment automatically trains a model, evaluates it, reports metrics, and stores results as artifacts.

---

## Dataset
- **Name:** Wine Quality Dataset (Red Wine)
- **Source:** UCI Machine Learning Repository  
  https://archive.ics.uci.edu/dataset/186/wine+quality
- **Target Variable:** `quality`
- **Features:** Physicochemical properties of wine

---

## Project Structure

```
lab2/
│── .github/
│   └── workflows/
│       └── train.yml
│── dataset/
│   └── winequality-red.csv
│── script/
│   └── train.py
│── output/
│   ├── model.pkl
│   └── metrics.json
│── requirements.txt
└── README.md
```

---

## Training Script (`train.py`)
The training script performs the following steps:

1. Loads the Wine Quality dataset
2. Applies preprocessing using `StandardScaler`
3. Splits data into training and testing sets
4. Trains a **Lasso Regression** model
5. Evaluates the model using:
   - Mean Squared Error (MSE)
   - R² Score
6. Saves:
   - Trained model (`model.pkl`)
   - Evaluation metrics (`metrics.json`)
7. Prints metrics to standard output

---

## GitHub Actions Workflow
The GitHub Actions workflow automatically:

- Triggers on:
  - Push to `main` branch
  - Pull request to `main`
- Sets up Python environment
- Installs required dependencies
- Runs the training script
- Displays evaluation metrics in the **Job Summary**
- Uploads trained model and metrics as artifacts

---

## Artifacts
Each workflow run uploads:
- `model.pkl` – trained model file
- `metrics.json` – evaluation results containing MSE and R² score

Artifacts can be downloaded from the **GitHub Actions run page**.

---

## Experiments
Multiple experiments were conducted by manually modifying the training script:
- Changing model hyperparameters
- Adjusting preprocessing steps
- Updating train-test split

Each experiment was committed with a meaningful message and triggered a separate workflow run.

---

## Analysis

### 1. How did GitHub Actions improve reproducibility?
GitHub Actions ensured consistent execution of experiments by automating the training and evaluation process for every code change.

### 2. How easy was it to compare results across runs?
Results were easy to compare since metrics were stored as artifacts and displayed in job summaries for each run.

### 3. What role does Git commit history play?
Each commit represents one experiment, allowing clear tracking of changes and outcomes.

### 4. Benefits compared to Lab 1
Automation reduced manual effort, improved traceability, and ensured consistent experiment execution.

### 5. Limitations
Hyperparameters must still be changed manually, and result comparison is limited without visualization tools.

---

## Repository Link
