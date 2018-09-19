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
