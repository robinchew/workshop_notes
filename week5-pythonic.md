Idiomatic Python
================

While loop vs for loop
----------------------

```
entries = [
    {'price': 11},
    {'price': 12},
]
```
```
klist = []

i = 0
while i < len(entries):
    klist.append({
        'price': entries[i]['price'] + 10,
    })
    i += 1
```

```
klist contains:
[
    {'price': 21,},
    {'price': 22}
]
```
```
klist = []

for entry in entries:
    klist.append({
        'price': entry['price'] + 10
    })
```

If you insist on using `i`:

```
klist = []

for i, entry in enumerate(entries):
    klist.append({
        'price': entry['price'] + 10,
        'index': i,
    })
```

```
klist contains:
[
    {'price': 21, 'index': 0},
    {'price': 22, 'index': 1}
]
```
