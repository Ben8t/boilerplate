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