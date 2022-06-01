# Date & Time

## Get formatted today date

```python
import datetime

date = datetime.datetime.today()
formatted_date = date.strftime("%Y%m%d")
```

## Parse date string

If your string is already in iso-format (`%Y-%m-%d`)

```python
from datetime import date
date_variable = date.fromisoformat('2019-12-04')
```

if you have other format

```python
from datetime import datetime
new_date = datetime.strptime('20190109', '%Y%m%d')
```

or
 
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
```

## Manipulate date with [Operation](https://ben8t.github.io/operation/03-operation-list.html)

Remove 120 days from a given date :

```bash
operation date -d 2021 01 01 0 0 120 --sub
```

Add 2 years, 1 month and 15 days to a given date

```bash
operation date -d 2021 01 01 2 1 15 --add
```


## Create range of date

```python
import pandas as pd

pd.date_range('2021-02-01','2021-12-01', freq='MS').strftime("%Y%m%d").tolist()
```
