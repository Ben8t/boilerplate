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