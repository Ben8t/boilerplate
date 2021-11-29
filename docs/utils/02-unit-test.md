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

## Mocker

```python
def test_with_mock(mocker):
    mocker.patch.object(<object>, "<object_method>", auto_spec=True)
    handler = <object>(params)

    assert handler...
```