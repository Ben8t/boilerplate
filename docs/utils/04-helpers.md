# Helpers

## Flatten list of lists

```python
def flat_list(lists: list) -> list:
    return [item for sublist in lists for item in sublist]
```

## Logging

```python
import logging

logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)
logger.addHandler(logging.StreamHandler())
```

## Script arguments

```python
import argparse

parser = argparse.ArgumentParser(description="Some description")
parser.add_argument("--some_flag", default=False, action="store_true")
parse.add_argument("--another_flag", type="integer") 
args = parser.parse_args()
```

## Fake Pandas Dataframe

```python
import numpy as np
import pandas as pd
import string
row_num = 10000
col_num = 5
col_names = list(string.ascii_uppercase)[0:col_num]
df = pd.DataFrame(np.random.randint(0,row_num,size=(row_num, col_num)), columns=col_names)
```

## Import subdirectory in Jupyter Notebook

```python
import os
import sys
import inspect

currentdir = os.path.dirname(os.path.abspath(inspect.getfile(inspect.currentframe())))
parentdir = os.path.dirname(currentdir)
sys.path.insert(0, parentdir) 
```