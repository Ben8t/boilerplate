# Scikit-Learn


## Split dataset

```python
from sklearn.model_selection import train_test_split

split_size = 0.3
target = [...]
x = data.drop(target, axis=1)
y = data[target]
x_train, x_validation, y_train, y_validation = train_test_split(x, y, test_size=split_size)
```

## Metric evaluation

### Regression

```python
import numpy as np
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

def compute_regression_metrics(y_true, y_pred):
    return {
        "mae": mean_absolute_error(y_true, y_pred),
        "rmse": np.sqrt(mean_squared_error(y_true, y_pred)),
        "r2": r2_score(y_true, y_pred)
    }
```

Example:
```python
y_true = [1, 2, 3, 4, 5]
y_pred = [0.9, 2, 3, 4.2, 5.6]
regression_metrics = compute_regression_metrics(y_true, y_pred)
mae = regression_metrics.get("mae")
rmse = regression_metrics.get("rmse")
r2 = regression_metrics.get("r2")
```

### Classification

```python
from sklearn.metrics import accuracy_score, precision_score, recall_score

def compute_classification_metrics(y_true, y_pred):
    return {
        "accuracy": accuracy_score(y_true, y_pred),
        "precision": precision_score(y_true, y_pred),
        "recall_score": recall_score(y_true, y_pred)
    }
```

Example:
```python
y_true = [1, 0, 1, 1, 0]
y_pred = [0, 0, 1, 0, 0]
classification_metrics = compute_classification_metrics(y_true, y_pred)
accuracy = classification_metrics.get("accuracy")
precision = classification_metrics.get("precision")
recall = classification_metrics.get("recall_score")
```

## Data Preprocessing Pipeline

Example for numeric and categorical features set :
```python
from sklearn.compose import ColumnTransformer
from sklearn.ensemble import RandomForestClassifier
from sklearn.impute import SimpleImputer
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler, OneHotEncoder


def build_preprocessor(numeric_features: list, categorical_features: list) -> ColumnTransformer:
    numeric_transformer = Pipeline(steps=[("scaler", SimpleImputer())])
    categorical_transformer = Pipeline(steps=[
            ("nan_resolve", SimpleImputer(strategy="constant", fill_value=0)), 
            ("onehot", OneHotEncoder(handle_unknown="ignore"))
        ]
    )

    preprocessor = ColumnTransformer(
        transformers = [
            ("numeric", numeric_transformer, numeric_features),
            ("categorical", categorical_transformer, categorical_features)
        ]
    )

    return preprocessor


# numeric_features, categorical_features = [...], [...]
# preprocessor = build_preprocessor(numeric_features, categorical_features)
# classifier = RandomForestClassifier()
# model = Pipeline(steps=[("preprocessor", preprocessor), ("classifier", classifier)])
```