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

