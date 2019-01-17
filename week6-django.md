Week 6 - Django
===============

Open your terminal (not python shell):

```
pip install django
django-admin startproject my_django_project
cd my_django_project
python manage.py runserver
```
Now your django server is running, open your browser, and type:

    localhost:8000

You can exit the running server with `ctrl + c` (You might need to press that more than once).

Lets create a super user to login to admin at `localhost:8000/admin`.

But creating a user requires the database to contain the user table, so you need to run migrate to create the default tables:

    python manage.py migrate

Now create a super user and follow the prompts:

    python manage.py createsuperuser

File Structure
--------------
```
my_django_project (project)
├── db.sqlite3
├── manage.py
└── my_django_project (app)
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```
Notice there are 2 folders named `my_django_project`, one is the **project** folder, the other is **app**.

Views without Templates
-----------------------

Save the following view code in your **app** folder `my_django_project/views.py`

```python
from django.http import HttpResponse

def index(request):
    num = 1
    return HttpResponse('<p>My favourite number is {}</p>'.format(num))
```

URLS
----

You have a view but no way to access them from the URL.

So you have to set the route in `my_django_project/urls.py`

```python
from django.urls import re_path
from my_django_project.views import index

urlpatterns = [
    path('admin/', admin.site.urls),
    re_path('^$', index),
    # Equivalent to below
    # path('', index),
]
```
Just to teach a bit of regular expressions, we are using `re_path` instead of `path`. The characters inside `r''` are regular expressions. `^` means start of line and `$` means end of line.

Render Fuelwatch Table
----------------------

Before going any future, you should be able to import code from your fuelwatch in order to generate the table and render in views.

With Templates
--------------

For templates to work, don't forget to install your `my_django_project` app in `my_django_project/settings.py`:

    INSTALLED_APPS = [
        'django.contrib.blah',
        'django.contrib.blah',
        'django.contrib.blah',
        'my_django_project',
    ]

So now whatever HTML file (say `index.html`) you put in the app `my_django_project/templates/`, it would be recognised when you use `render` in your view:

```python
from django.shortcuts import render
def index(request):
    return render(request, 'index.html', {
        'num': 123,
    })
```

Assuming your template contains the following:

    <p>My favourite number is {{ num }}</p>

Then your browser will render:

    My favourite number is 123
