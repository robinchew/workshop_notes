Traversing the DOM elements
===========================

```html
<html>
    <body>
        <ul>
            <li class="coll">One</li>
            <li id="second" class="col2">Two</li>
            <li class="col3">Three</li>
        </ul>
    </body>
</html>
```

Walk down the tree
------------------

Start from the body and try to reach the element containing `Two`.

```html
<script>
    var body = document.body;
    var list = body.children[0] // <ul>
    var firstItem = list.children[0] // <li>One</li>

    // Get second item from 'ul' element
    console.log(list.children[1]);

    // Or
    // Get second item from first 'li' element
    console.log(firstItem.nextElementSibling);
</script>
```

Walk up the tree
----------------

Start from element containing `Two`.

```javascript
var secondItem = document.getElementById('second')

// Get 'ul' element.
console.log(secondItem.parentNode);


// Get 'body' element.
var list = secondItem.parentNode;
var body = list.parentNode;
console.log(body);
```

For loop
========

```python
# Python
for i in l:
    print(i+1)
```

```javascript
// JavaScript
for(var i=0; i<l.length; i++) {
    console.log(l[i]+1);
}
```

Or

```javascript
// JavaScript
l.forEach(function(i) {
    console.log(i+1);
})
```

If statement
============

```python
# Python
name = 'John'
is_male = True

if name != '':
    if name == 'John':
        colour = 'blue'
    elif name == 'Alex' and not is_male:
        colour = 'pink'
    else:
        colour = 'red'
```

```javascript
// JavaScript
var name = 'John';
var is_male = true;
var colour = '';

if (name != '') {
    if (name == 'John') {
        colour = 'blue';
    }
    else if (name == 'Alex' && ! is_male) {
        colour = 'pink';
    }
    else {
        colour = 'red';
    }
}
```
