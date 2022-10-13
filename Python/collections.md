<h1>Collections in Python</h1>
<b>Counter</b>  is used to count the occurrence of item.

```python
from collections import Counter

i="aaaaabbbbbbccdddd"
my_counter=Counter(i) # Counter({'b': 6, 'a': 5, 'd': 4, 'c': 2})
my_items=my_counter.items() # dict_items([('a', 5), ('b', 6), ('c', 2), ('d', 4)])
my_keys=my_counter.keys() # dict_keys(['a', 'b', 'c', 'd'])
my_value=my_counter.values() # dict_values([5, 6, 2, 4])
my_common_value=my_counter.most_common(1)[0][0] # 6 if [0][1] then b
my_elements=list(my_counter.elements()) # ['a', 'a', 'a', 'a', 'a', 'b', 'b', 'b', 'b', 'b', 'b', 'c', 'c', 'd', 'd', 'd', 'd']
```

<b> Named Tuple</b>

```python
from collections import namedtuple

Point = namedtuple('Point','x,y')
pt=Point(1,2) # Point(x=1, y=2) pt.x pt.y
```
<b> Default Dictionary</b> is like regular dictonary, but remember the insertion order

```python
from collections import namedtuple

Point = namedtuple('Point','x,y')
pt=Point(1,2) # Point(x=1, y=2) pt.x pt.y
```
