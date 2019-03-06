Week 9 - Django Database Models
===============================

Your fuel application does not actually need a database to work. It's quite important to learn how to store data but you can actually skip this week if you want.

You django project directory will typically look like the following:

    my_django_project
    ├── db.sqlite3
    ├── main
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── templates
    │   │   └── prices.html
    │   ├── urls.py
    │   ├── views.py
    │   └── wsgi.py
    ├── manage.py
    ├── Procfile
    └── requirements.txt

You are going to create a database table (Django calls it a 'model') to store your fuel data, so that you don't have to call fuelwatch.wa.gov.au all the time and also to keep historical prices. Lets call this model `FuelPrice` and you are going to create it in a file that must be named `models.py` and must be put under `main` (assuming that's what your main Django app is called).

my_django_project/main/models.py

    from django.db import models

    class FuelPrice(models.Model):
        price = models.DecimalField(max_digits=8, decimal_places=2)
        fuel_type = models.IntegerField()
        address = models.CharField(max_length=100)

        # Add more fields here... 
        
        
Fuelwatch uses integers to represent fuel types, so you can follow suit or perhaps use string instead with `models.CharField()`


So you got your first model created, but it's just a Python class, the database table has not been created yet. You need to create a migration file, this file acts like an instruction on how to convert your `FuelPrice` python model class into a real SQL table. Django provides the command to do so.

    python manage.py makemigrations

You will notice that `my_django_project/main/migrations` would have been created with your first `0001_*` migration file. Now lets do the actual migration. 

    python manage.py migrate

Your project directory will something like the following now, with `models.py` and `migrations`):

    my_django_project
    ├── db.sqlite3
    ├── main
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── models.py
    │   ├── migrations
    │   │   └── 0001_something_something.html
    │   ├── templates
    │   │   └── prices.html
    │   ├── urls.py
    │   ├── views.py
    │   └── wsgi.py
    ├── manage.py
    ├── Procfile
    └── requirements.txt

Let's start creating, updating and listing the `FuelPrice` in your view::

    from main.models import FuelPrice

    def my_fuel_prices_view(request):

        # Create
        price = FuelPrice(price=154.98, fuel_type=1, address='12 street')
        price.save()

        # Update
        price.fuel_type = 2
        price.save()

        # List
        all_prices = FuelPrice.objects.all()
         
        return render(request, 'prices.html', {
            'fuel_prices': all_prices,
        })

It doesn't make sense for a page that does create, update, and listing at the same time. They each should be in their own view. If you try to view this page you will notice a new fuel price added on each page load. 
