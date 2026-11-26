# Student Performance Prediction using Logistic Regression

A Machine Learning project that predicts whether a student belongs to the **Pass / Higher Performance** group or the **Fail / Lower Performance** group using student-related factors such as study hours, attendance, previous scores, sleep, tutoring, and learning environment.

## 👨‍💻 Author

[![GitHub](https://img.shields.io/badge/GitHub-complexiota-black?logo=github)](https://github.com/complexiota)

GitHub Profile: [https://github.com/complexiota](https://github.com/complexiota)

## 📌 Project Overview

This project uses **Logistic Regression** to classify students into two groups:

- `0` — Fail / Lower Performance
- `1` — Pass / Higher Performance

The target column `Pass_Fail` is created from the dataset's `Exam_Score` using the median exam score as the threshold. In this dataset, the median is **67**. Students with an exam score greater than or equal to 67 are assigned `1`; students scoring below 67 are assigned `0`.

**Note:** This is a dataset-based classification label created for this project. It should not be treated as an official school pass/fail rule.

## 📂 Project Files

| File | Description |
|---|---|
| `logistic_regression_model.ipynb` | Jupyter Notebook containing data loading, preprocessing, model training, evaluation, and prediction for a new student |
| `StudentPerformanceFactors.csv` | Dataset containing student performance factors and exam scores |

## 📊 Dataset Information

- **Rows:** 6,607 students
- **Columns:** 20
- **Input features:** 19 student-related features
- **Original score column:** `Exam_Score`
- **Target created in the notebook:** `Pass_Fail`

The input features include:

- Hours studied and attendance
- Parental involvement and access to resources
- Extracurricular activities and sleep hours
- Previous scores and motivation level
- Internet access and tutoring sessions
- Family income, teacher quality, and school type
- Peer influence and physical activity
- Learning disabilities and parental education level
- Distance from home and gender

The notebook removes `Exam_Score` and `Pass_Fail` from the input features before training. The `Pass_Fail` column is used as the target.

### Missing values

The supplied dataset contains missing values in these columns:

| Column | Missing values |
|---|---:|
| `Teacher_Quality` | 78 |
| `Parental_Education_Level` | 90 |
| `Distance_from_Home` | 67 |

The notebook handles missing values in the preprocessing pipeline:
- Numerical columns: missing values are filled with the median.
- Categorical columns: missing values are filled with the most frequent value.

## 🛠️ Technologies and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook / Google Colab

## ⚙️ Machine Learning Workflow

1. Import the required Python libraries.
2. Load `StudentPerformanceFactors.csv` using Pandas.
3. Inspect the dataset shape, columns, data types, and missing values.
4. Create the `Pass_Fail` target using the median of `Exam_Score`.
5. Separate the input features (`X`) and target (`y`).
6. Identify numerical and categorical columns.
7. Build preprocessing pipelines:
   - Numerical: median imputation and standard scaling.
   - Categorical: most-frequent imputation and one-hot encoding.
8. Split the dataset into training and testing sets using an 80:20 split, `random_state=42`, and stratification.
9. Train a Logistic Regression classifier with `max_iter=1000`.
10. Predict the classes for the test data.
11. Evaluate the model using accuracy, classification report, and confusion matrix.
12. Use the trained model to predict the class and pass probability for a new student.

## 🤖 Model Details

The notebook uses a Scikit-learn `Pipeline` that combines preprocessing and classification:

- **Numerical preprocessing:** `SimpleImputer(strategy="median")` followed by `StandardScaler()`
- **Categorical preprocessing:** `SimpleImputer(strategy="most_frequent")` followed by `OneHotEncoder(handle_unknown="ignore")`
- **Classifier:** `LogisticRegression(max_iter=1000)`

Using a pipeline ensures that the preprocessing steps are fitted on the training data and then applied consistently to test and new student data.

## 📈 Model Evaluation

With the notebook's 80:20 stratified split and `random_state=42`, the model produces the following results when run on the supplied CSV:

| Metric | Result |
|---|---:|
| Accuracy | 97.73% |

Classification report:

| Class | Precision | Recall | F1-score | Support |
|---|---:|---:|---:|---:|
| Fail / Lower Performance (0) | 0.98 | 0.97 | 0.97 | 577 |
| Pass / Higher Performance (1) | 0.98 | 0.98 | 0.98 | 745 |

Confusion matrix:

| Actual / Predicted | Fail (0) | Pass (1) |
|---|---:|---:|
| Actual Fail (0) | 561 | 16 |
| Actual Pass (1) | 14 | 731 |

These results are based on the supplied dataset and the specified split. They measure how well the model predicts the project's median-based label, not an independently verified real-world school pass/fail outcome.

## ▶️ How to Run the Project

### Option 1: Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `logistic_regression_model.ipynb`.
3. Upload `StudentPerformanceFactors.csv` to the Colab session.
4. Make sure the CSV is available at `/content/StudentPerformanceFactors.csv` if you are using that file path, or update the path in the notebook.
5. Run all notebook cells from top to bottom.

### Option 2: Run Locally

1. Download or clone this repository.
2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

3. Keep `StudentPerformanceFactors.csv` in the location expected by the notebook, or update the CSV path.
4. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `logistic_regression_model.ipynb` and run all cells.

## 🔮 Predict for a New Student

The notebook creates a sample student record and passes it to the trained model. The example uses:

- Hours studied: 25
- Attendance: 90
- Previous scores: 80
- Sleep hours: 7
- Tutoring sessions: 3
- Other categorical and student-related factors

The model returns:
- Predicted class: `PASS / HIGHER PERFORMANCE` or `FAIL / LOWER PERFORMANCE`
- Probability of the `Pass_Fail = 1` class

The probability is the model's estimated probability for the project's label, not a guarantee of a student's actual result.

## 🎯 Learning Outcomes

- Understand binary classification.
- Understand how Logistic Regression is used for classification.
- Create a target variable from an existing numerical column.
- Handle missing numerical and categorical values.
- Apply scaling and one-hot encoding.
- Use a Scikit-learn preprocessing and modelling pipeline.
- Split data into training and testing sets.
- Evaluate a classification model using accuracy, precision, recall, F1-score, and a confusion matrix.
- Make predictions for a new student record.

## 📝 Conclusion

This project demonstrates a complete beginner-level classification workflow using Logistic Regression. It uses student-related factors to predict a median-based performance category, with preprocessing, model training, evaluation, and prediction included in the Jupyter Notebook.

---

**Explore more projects and connect with me on GitHub:**

[https://github.com/complexiota](https://github.com/complexiota)
