# Unit Test

## Pytest fixture

```python
import pytest

@pytest.fixture
def fake_data():
    return [1, 2, 3, 4, 5]


def test_data_length(fake_data):
    assert len(fake_data) == 5
```