# PINL
This project applies machine learning regression models to predict the boiling points of chemical compounds using molecular descriptors. It includes data cleaning, feature exploration, visualization, multiple regression techniques, and model hyperparameter tuning.


## Team Members

- Mujtaba-4T4
- TurboGlitch
- Hydroxymeth


## Dataset

The dataset contains **777 molecular descriptors** for 5431 molecules, along with their **boiling point values (`BP`)**. These descriptors capture structural, topological, physicochemical, and electronic properties of molecules.

### Important Descriptors Used in Analysis

| Descriptor ID | Descriptor Name |
|---------------|------------------|
| D004          | Molecular Weight |
| D368          | LogP (octanol-water partition coefficient) |
| D294          | TPSA (Topological Polar Surface Area) |
| D555          | Number of Hydrogen Bond Donors |
| D556          | Number of Hydrogen Bond Acceptors |
| D557          | Number of Rotatable Bonds |
| D553          | Number of Ring Atoms |
| D559          | Number of Aromatic Rings |
| D370          | AlogP |
| D560          | Formal Charge |
| D373          | Fraction Csp3 |

The dataset file used: `chem_data.csv`

## Workflow Summary

### 1. Data Preparation
- Dropped unnamed or null columns
- Split dataset by `Subset` column into train, validation, and test sets
- Standardized the feature values using `StandardScaler`

### 2. Feature Exploration
- Correlation matrix between features and boiling point
- Scatter plots between each key descriptor and boiling point

### 3. Base Models
- **Linear Regression** using selected features
- Evaluation using Mean Absolute Error (MAE)

### 4. Additional Regression Models
The following regressors were implemented and tested:

- Ridge Regression
- Lasso Regression
- ElasticNet Regression
- K-Nearest Neighbors Regressor
- Support Vector Regressor (SVR)
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor

Each model was trained and evaluated using the validation set.

### 5. Hyperparameter Tuning
Grid search was used with cross-validation to find optimal hyperparameters:

- Ridge Regression: {'alpha': 10}
- Lasso Regression: {'alpha': 0.1}
- ElasticNet Regression: {'alpha': 0.1, 'l1_ratio': 0.9}
- K-Nearest Neighbors Regressor: {'n_neighbors': 5, 'p': 1, 'weights': 'distance'}
- Support Vector Regressor: {'C': 1, 'gamma': 'scale', 'kernel': 'linear'}
- Decision Tree Regressor: {'max_depth': 10, 'min_samples_leaf': 4, 'min_samples_split': 2}
- Random Forest Regressor: {'max_depth': 20, 'min_samples_split': 2, 'n_estimators': 200}
- Gradient Boosting Regressor: {'n_estimators': 200, 'learning_rate': 0.1, 'max_depth': 5}

### 6. Results
**Boiling Point (BP)** prediction was evaluated using three key metrics:  
- **MAE**: Mean Absolute Error  
- **MSE**: Mean Squared Error  
- **R²**: Coefficient of Determination  
> *Note: BP is measured in degrees Celsius.*

| Model                      | MAE    | MSE      | R² Score |
|----------------------------|--------|----------|----------|
| Linear Regression          | 25.60  | 1213.80  | 0.820    |
| Ridge Regression           | 16.17  | 519.43   | 0.921    |
| Lasso Regression           | 14.27  | 430.53   | 0.935    |
| ElasticNet Regression      | 14.16  | 429.01   | 0.935    |
| K-Nearest Neighbors        | 19.64  | 781.71   | 0.882    |
| Support Vector Regressor   | 14.57  | 441.36   | 0.933    |
| Decision Tree Regressor    | 20.68  | 923.34   | 0.860    |
| Random Forest Regressor    | 14.60  | 470.16   | 0.929    |
| Gradient Boosting Regressor| 14.79  | 464.63   | 0.930    |

** Best Model**  
ElasticNet Regression performed the best overall, achieving the lowest MAE (**14.16**) and highest R² score (**0.935**).


## Libraries and Tools Used

- `pandas`, `numpy`, `matplotlib`, `sklearn`
