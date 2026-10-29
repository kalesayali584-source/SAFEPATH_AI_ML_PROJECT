# SafePath AI: Road Safety Score Prediction Using XGBoost

## About the Project

SafePath AI is a machine learning project that predicts road safety scores using road characteristics and nearby infrastructure. It compares Random Forest Regressor and XGBoost Regressor to estimate a numerical safety score.

The project evaluates model performance using R² Score, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE). `RandomizedSearchCV` with five-fold cross-validation is used to tune XGBoost hyperparameters.

## Problem Statement

Road safety can be influenced by speed limits, road type, road length, number of lanes, and proximity to facilities such as police stations and hospitals. This project explores how machine learning can learn patterns from these attributes and predict a road safety score.

## Objectives

- Load and preprocess road-network data.
- Select relevant road attributes for model training.
- Train Random Forest and XGBoost regression models.
- Tune XGBoost using `RandomizedSearchCV`.
- Evaluate models using R², MAE, and RMSE.
- Examine feature importance.
- Save the selected model for future use.

## Dataset


Input features used by the model:

- `maxspeed`
- `oneway`
- `length`
- `lanes`
- `police_distance`
- `hospital_distance`
- `restaurant_count`
- `busstop_count`
- `highway_primary`
- `highway_residential`
- `highway_secondary`
- `highway_tertiary`
- `highway_trunk`



## Tools and Libraries

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Joblib
- Jupyter Notebook / JupyterLab

## Methodology

1. Load the dataset using Pandas.
2. Preprocess values, convert suitable columns to numeric formats, and handle missing values as implemented in the notebook.
3. Use 13 road-related features as model inputs and `safety_score` as the target.
4. Split the data into 80% training and 20% testing subsets using `random_state=42`.
5. Train Random Forest and XGBoost regression models.
6. Apply five-fold cross-validation and `RandomizedSearchCV` to search XGBoost hyperparameters.
7. Compare models using training/testing R², MAE, and RMSE.
8. Inspect feature importance and save the selected model with Joblib.

## Hyperparameter Tuning

`RandomizedSearchCV` samples a set number of parameter combinations rather than testing every possible combination. In this project, 20 sampled XGBoost configurations were evaluated using five-fold cross-validation with R² scoring.

The best parameters recorded in the notebook were:

```python
{
    'subsample': 0.7,
    'n_estimators': 300,
    'min_child_weight': 5,
    'max_depth': 3,
    'learning_rate': 0.05,
    'gamma': 0.3,
    'colsample_bytree': 1.0
}
```

## Results

The tuned-model results recorded in the notebook are:

| Metric | Random Forest | Tuned XGBoost |
|---|---:|---:|
| Training R² Score | 0.9666 | 0.9666 |
| Testing R² Score | 0.9185 | **0.9231** |
| MAE | 4.1507 | **4.0102** |
| RMSE | 5.0898 | **4.9451** |




### Interpretation

- The tuned XGBoost model achieved a test R² score of approximately 0.9231.
- Its MAE was approximately 4.01 score points.
- Its RMSE was approximately 4.95 score points.
- On the recorded test metrics, tuned XGBoost performed slightly better than the tuned Random Forest model.

These results reflect this experiment's dataset and split. They do not, by themselves, establish that the predictions are suitable for real-world road-safety decisions.

## Project Structure

```text
SafePath-AI/
├── README.md
├── requirements.txt
├── Model_Training.ipynb
└── road_safety_dataset_final.csv
```

The notebook and dataset filenames shown above are examples; use the actual filenames in your repository.

## Installation and Usage

### 1. Clone the repository

Replace the placeholder with your GitHub repository URL:

```bash
git clone <https://github.com/kalesayali584-source/SAFEPATH_AI_ML_PROJECT>
cd SafePath-AI
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```



### 3. Load  Dataset



### 4. Run the notebook

```bash
jupyter notebook
```

Open the model-training notebook and run its cells in order.

## Limitations

- Model quality depends on dataset accuracy and representativeness.
- Predicted scores are estimates, not verified measures of actual road safety.
- Independent geographic and time-based validation would be needed before practical use.
- This repository covers model training and evaluation; it is not a deployed application or a complete route-recommendation system.

## Future Scope

- Test the model on independent road-network datasets.
- Explore additional road, traffic, and environmental features when reliable data is available.
- Develop a user interface for viewing predicted scores.
- Investigate integration into a broader road-safety analysis tool after further validation.
- Monitor model performance as new data becomes available.

## Conclusion

SafePath AI demonstrates a machine learning workflow for predicting road safety scores. Random Forest and XGBoost were trained and evaluated, and XGBoost was tuned with `RandomizedSearchCV` and five-fold cross-validation. Based on the results recorded in the notebook, tuned XGBoost achieved the best performance among the two evaluated models.

## Author

**Sayali Jitendra Kale**  
Roll No.: CS3157  
Computer Engineering  
JSPM's Rajarshi Shahu College of Engineering, Tathawade

---

*Academic machine learning project.*
