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

Lets create a super user to login to admin at localhost:8000/admin.

But creating a user requires the database to contain the user table, so you need to run migrate to create the default tables:

    python manage.py migrate

Now create a super user and follow the prompts:

    python manage.py createsuperuser

Templates
---------

For templates to work, don't forget to install your `my_django_project` app in `my_django_project/settings.py`:

    INSTALLED_APPS = [
        'django.contrib.blah',
        'django.contrib.blah',
        'django.contrib.blah',
        'my_django_project',
    ]

So now whatever HTML file (say index.html) you put in `my_django_project/templates/`, it would be recognised when you use `render` in your view:

    from django.shortcuts import render
    def index(request):
        return render(request, 'index.html', {
            'num': 123,
        })

Assuming your template contains the following:

    <p>My favourite number is {{ num }}</p>

Then your browser will render:

    My favourite number is 123
