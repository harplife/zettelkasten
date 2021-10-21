---
aliases: [Get current time in KST, How to add to datetime]
tags: [python, code, example, how-to]
status: ongoing
edited: 2021-10-11
---

# How to add to datetime
A code example for [[python|Python]].

## Using Datetime
```python
from datetime import datetime, timedelta

now_kst = (datetime.now() + timedelta(hours=9)).strftime('%Y-%m-%d %H:%M:%S KST')
```

## Using Pandas
```python
import pandas as pd

today = '10/11/2021'
a_week_from_tdoay = pd.to_datetime(today) + pd.DateOffset(days=7)