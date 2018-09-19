

```
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
