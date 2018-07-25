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
