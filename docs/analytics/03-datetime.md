# Date & Time

## Get formatted today date

```python
import datetime

date = datetime.datetime.today()
formatted_date = date.strftime("%Y%m%d")
```

## Parse date string

```python
from dateutil import parser
datetime_obj = parser.parse('2018-02-06T13:12:18.1278015Z')
print datetime_obj
# output: datetime.datetime(2018, 2, 6, 13, 12, 18, 127801, tzinfo=tzutc())
```

:warning: Can be slow...

## Convert Pandas string to datetime

```python
import pandas as pd
import datetime

data = pd.DataFrame([{"str_date": "20210101"}, {"str_date": "20210201"}])

parsed_data = (
    data
    .assign(date=lambda x: pd.to_datetime(x["str_date"], format="%Y%m%d", errors="ignore"))
)