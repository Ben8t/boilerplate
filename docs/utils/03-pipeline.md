# Pipeline

## Build chunks

```python
def build_chunks(items: list, batch_size: int) -> list:
    """Split data into chunks.

    Args:
        items (list): list of items to split.
        batch_size (int): batch size.
    
    Returns:
        (list): list of splitted elements (through a generator).
    """
    for i in range(0, len(items), batch_size):
        yield items[i:i + batch_size]
```