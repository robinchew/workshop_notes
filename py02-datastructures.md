Notes on list and dictionaries
==============================

Dictionary & List
-----------------

```python
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

person1 = {
    'name': 'John',
    'age': 44,
}

person2 = {
    'name': 'Robin',
    'age': 11,
    'friends': [
        person1,
        {
            'name': 'Mary',
            'age': 65,
        },
    ],
}
```

Looping Lists
-------------

```python
for friend in person2['friends']:
    just_names.append(friend['name'])
```

Concatenating Lists (Joining Lists)
-----------------------------------

Note that l1 and l2 does not change but l3 contains 6 items.
```python
l1 = [1, 2 ,3]
l2 = [10, 11 ,12]
l3 = l1 + l2 # Now l3 contains [1, 2, 3, 10, 11, 12]
```

Changing Lists
--------------

Note that l1 changes from 3 to 4 items.
```python
l1 = [1, 2 ,3]
l1.append(4) # will result in l1 containing [1, 2, 3, 4]

l1[2] = 4 # results [1, 2, 4]
l1[3] = 5 # Exception!
```

Changing Dictionaries
---------------------

Update an existing key value.

```python
person = {
    'name': 'Robin',
    'age': 99,
}

person['age'] = 100 # Person (Robin) is now changed to 100 years old
```

Add a new key value.

```python
person['favourite_colour'] = 'red' # You get {'name': 'Robin', 'age': 100, 'favourite_colour': 'red'}
```

Functions
---------

```python
def get_fuel(product_id):
    data = feedparser.parse('http://www.fuelwatch.wa.gov.au/fuelwatch/fuelWatchRSS?Product='+str(product_id)+'&Suburb=Cloverdale')
    return data['entries']
```

Sorting
-------

```python
l1 = [{'name': 'Robin', 'age': 44}, {'name': 'John', 'age': 22}, {'name': 'Mary', 'age': 33}]

def by_age(item):
   return item['age']

sorted_l1 = sorted(l1, key=by_age)
```
`sorted_l1` will contain:
```python
[{'name': 'John', 'age': 22}, {'name': 'Mary', 'age': 33}, {'name': 'Robin', 'age': 44}]
```
