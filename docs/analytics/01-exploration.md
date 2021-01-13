# Exploration

## Read data with Pandas

```python
import pandas as pd
import numpy as np

data_file = "..."
data = pd.read_csv(data_file)
num_columns = len(data.columns)
pd.set_option("display.max_columns", num_columns)
data.head(30)
```

## Plot value counts

```python
import seaborn as sns
titanic = sns.load_dataset("titanic")
ax = sns.countplot(x="class", data=titanic)
```