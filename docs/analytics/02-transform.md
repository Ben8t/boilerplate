# Transform


## Pandas group-by

```python
import pandas as pd

data = pd.read_csv('https://raw.githubusercontent.com/mwaskom/seaborn-data/master/iris.csv')

transformed_data = (
    data
    .groupby(["species"])
    .agg(
        mean_sepal_length=("sepal_length", "mean"),
        mean_sepal_width=("sepal_width", "mean"),
        max_petal_length=("petal_length", "max")
    )
    .reset_index()
)
```

## Pandas JSON Normalize

```python
import pandas as pd

data = [
    {
    "category": "car",
    "release_date": 2012,
    "assets": [
        {"key": "seat", "value": 4, "quality": 3}, 
        {"key": "seat", "value": 6, "quality": 9},
        {"key": "gear", "value": 4, "quality": 1}
    ]
    },
    {
    "category": "truck",
    "release_date": 2018,
    "assets": [
        {"key": "wheels", "value": 6, "quality": 2}, 
        {"key": "seat", "value": 3, "quality": 10},
        {"key": "gear", "value": 6, "quality": 8}
    ]
    }
]

pd.json_normalize(data, "assets", ["category", "release_date"])

#       key  value  quality category release_date
# 0    seat      4        3      car         2012
# 1    seat      6        9      car         2012
# 2    gear      4        1      car         2012
# 3  wheels      6        2    truck         2018
# 4    seat      3       10    truck         2018
# 5    gear      6        8    truck         2018
```