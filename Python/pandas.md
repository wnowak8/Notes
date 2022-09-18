<h1>Pandas</h1>
1. Rename column's name:

```python
df.rename(columns={'old_col1':'new_col1', 'old_col2':'new_col2'}, errors="raise", inplace=True)
```
2. Get tomorrow date:
```python
from datetime import date
import time
import pandas as pd

today = time.strftime("%Y-%m-%d")
tomorrow = pd.to_datetime(today, format="%Y-%m-%d") + pd.DateOffset(days=1)
```
3. Write logs:
```python   
with open('logs.csv',mode='w') as logsFile:
    writer=csv.writer(logsFile)
    writer.writerow(header)
    writer.writerow(data)
```
4. Upper item in list:
```python   
[e.upper() for e in item_list]
```
5. Selecting rows based on condition
```python  
new_df = df.loc[df['col1'] != 95]

options = ['Math', 'Commerce']
new_df = df[df['col1'].isin(options)]
```
6. Apply function on all rows in column:
```python  
df['col1'] = df['col1'].apply(<some_function>)
```