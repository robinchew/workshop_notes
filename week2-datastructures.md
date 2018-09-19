Notes on list and dictionaries
==============================

Dictionary & List
-----------------

```
d = {
    'key1': 1,
    'key2': 2,
}

l = [1, 2]

l[0] # 1

l = [
    {'key1': 1, 'key2': 2, 'key1': 3},
    {'key1': 11, 'key2': 22},
]

d['key1']

len(l) # Returns 2

person1 = {'name': 'Robin', 'friends': [person2, {'name': 'Mary', 'age': 65}]}
```

Looping Lists
-------------

```
for friend in person1['friends']:
    just_names.append(friend['name'])
```

Concatenating Lists (Joining Lists)
-----------------------------------

Note that l1 and l2 does not change but l3 contains 6 items.
```
l1 = [1, 2 ,3]
l2 = [10, 11 ,12]
l3 = l1 + l2 # Now l3 contains [1, 2, 3, 10, 11, 12]
```

Appending to Lists
------------------

Note that l1 changes from 3 to 4 items.
```
l1 = [1, 2 ,3]
l1.append(4) # will result in l1 containing [1, 2, 3, 4]
```

Functions
---------

```
def get_fuel(product_id):
    data = feedparser.parse('http://www.fuelwatch.wa.gov.au/fuelwatch/fuelWatchRSS?Product='+str(product_id)+'&Suburb=Cloverdale')
    return data['entries']
```
