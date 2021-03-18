# Helpers

## Flatten list of lists

```python
def flat_list(lists: list) -> list:
    return [item for sublist in lists for item in sublist]
```