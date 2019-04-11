Set Click Event
---------------
```
<button id="clickable">Click Me</button>
```
```
<script>
    var button = document.getElementById('clickable');
    button.onclick = function() {
        console.log('clicked and shown in developer console')
    }
</script>
```

Trigger Submit Event 
--------------------
```
<form id="product_form" action="/table" method="GET">
    <select id="product_select" name="product">
        {% for num, name in fuel_types %}
            <option value="{{ num }}"{% if selected_product == num %} selected {% endif %}>{{ name }}</option>
        {% endfor %}
    </select>
</form>
```
```        
<script>
    var form = document.getElementById('product_form');
    var selectBox = document.getElementById('product_select');

    function submit() {
        form.submit();
    }
    selectBox.onchange = submit;
</script>
```        

DOM element attributes
----------------------

```javascript
var element = document.getElementBy('clickable');

console.log(element.innerHTML);
console.log(element.innerText);
console.log(element.classList);

// Get CSS style attributes
console.log(element.style.display);
console.log(element.style.visibility);
console.log(element.style.backgroundColor);

// Set CSS style attributes
// Google these CSS styles to find out other values
element.style.display = 'none';
element.style.visibility = 'hidden';
element.style.backgroundColor = 'red';

// Change CSS style by adding/removing classes
element.classList.add('pretty');
element.classList.remove('pretty');
```
