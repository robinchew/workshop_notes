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
