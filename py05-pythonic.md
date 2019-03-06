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

List Comprehension
------------------

```
a = [11, 12, 13]
b = [
    v+5
    for v in a
]
```
`b` will equal `[16, 17, 18]`

Below also demonstrates list comprehension but with access to the index with `enumerate`.
```
klist = [
    {
        'price': entry['price'] + 10,
        'index': i,
    }
    for i, entry in enumerate(entries)
]
```

Joining list of string
----------------------

```
l = ['My', 'name', 'is', 'Robin']

s = ''
for word in l:
    s = s + word + ' '

s2 = ' '.join(l)
```
```
def capitalise(s):
    return s[0].upper() + s[1:]

sentence = ''

for word in l:
    sentence += captalise(word) + ' '

sentence = sentence.strip()
```

```
l2 = [capitalise(word) for word in l]
sentence = ' '.join(l2)
```
OR
```
sentence = ' '.join(capitalise(word) for word in l)
```
OR formatted differently as:
```
sentence = ' '.join(
    capitalise(word)
    for word in l
)
```

```
prices = [154.4, 158.2, 140.6, 124.5, 124.0, 120.0]

def cents_to_dollar(price):
    return '${}'.format(round(price) / 100)

top_5_sorted = sorted(prices, reverse=True)[0:5]

joined_prices = ', '.join(
    cents_to_dollar(price)
    for price in top_5_sorted)

'The top 5 most expensive  prices are {}'.format(joined_prices)
```
OR
```
'The top 5 most expensive prices are {}'.format(', '.join(
    '${}'.format(round(price) / 100)
    for price in sorted(prices, reverse=True)[0:5]))
```

Unpacking arguments
------------------- 

```
def plus(a, b):
    return a + b

plus(1, 2)

arg_list = [1, 2]

plus(arg_list[0], arg_list[1])

# Destructure first

a, b = arg_list
plus(a, b)
```

Unpack argument list

```python
plus(*arg_list)
plus(arg_list) # wrong

plus(*[1, 2])
plus(1, 2) # equivalent to line above
```

Unpack argument dictionary

```python
arg_dic = {'a': 1, 'b': 2}
plus(**arg_dic)
```

File handling with context processor
------------------------------------

```
f = open('index.html', 'w')
f.write(html_index)
f.close()
```

The close occurs after the `with` context processor block exits.

```
with open('index.html', 'w') as f:
    f.write(html_index)
```
