Change fuel type with URL query string
======================================

```python
from django.shortcuts import render
from django.http import HttpResponse

from fuel_scraper import get_fuel_data, gen_fuel, fuel_types, regions, day

def index(request):
    # Getting fuel type from URL query string
    product_num = request.GET['product']

    # Getting fuel prices
    urls = gen_fuel([product_num], regions, day)
    fuel_data = get_fuel_data(urls)

    for value in fuel_data:
        fuel_data_rows_string += """
            <tr>
                <td>{price} </td><td>{address} </td><td>{location} </td><td>{brand}</td>
            </tr>
        """.format(**value)

    # Formats the html.
    fuel_data_html = "<table>" + fuel_data_rows_string + "</table></tbody></body></html>"
    return HttpResponse(fuel_data_html)
```

Default dictionary key value
-----------------------------

If you apply the code above, you will find that you will be getting `KeyError`.

If you try to run the following code, there is no problem.
```python
d = {'preferred_colour': 'red'}
colour = d['preferred_colour']
```

If you do this, you will get the `KeyError`.
```python
d = {}
colour = d['preferred_colour']
```

Let's say you want to default to 'blue' if a preferred colour is not specified, you can do:
```
if 'preferred_colour' in d:
  colour = d['preferred_colour']
else:
  colour = 'blue'
```

Which is same as:

```colour = d.get('preferred_colour', 'blue')```

Change fuel type with Form 
==========================

Changing the form actually changes the URL

```python
from django.shortcuts import render
from django.http import HttpResponse

from fuel_scraper import get_fuel_data, gen_fuel, fuel_types, regions, day

def index(request):
    product_num = request.GET['product']

    # Getting fuel prices
    urls = gen_fuel([product_num], regions, day)
    fuel_data = get_fuel_data(urls)

    fuel_data_rows_string = """
        <form>
            <select name="product">
                <option value="1">Unleaded</option>
                option value="2">Premium Unleaded</option>
            </select>
            <button type="submit">Filter</button>
        </form>
    """
    for value in fuel_data:
        fuel_data_rows_string += """
            <tr>
                <td>{price} </td><td>{address} </td><td>{location} </td><td>{brand}</td>
            </tr>
        """.format(**value)

    # Formats the html.
    fuel_data_html = "<table>" + fuel_data_rows_string + "</table></tbody></body></html>"
    return HttpResponse(fuel_data_html)
```
