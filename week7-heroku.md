Heroku
======

- Sign up and log in in heroku.com and create a new app, pick a name (eg. my-fuelwatch-app)and any country with no pipeline.
- Install the CLI tool as specified under the 'Deploy' tab.
- Follow the rest of the instructions under "Deploy using Heroku Git", you can `git init` but do NOT just do `git add. ` because that will add the .pyc and .sqlite files which is not what you want in the Git repository. So `git add` the .py and .html files one by one and commit.
- `cd` into your local django project folder and run `heroku login` to login.
- then do `heroku git:remote -a my-fuelwatch-app`
- and finally `git push heroku master`.

ERROR!
------

Your push failed! Saying something about:

    No default language could be detected for this app.

You got to add extra things to your project to satisfy heroku.


requirements.txt
----------------

One file named `requirements.txt` is required in the project root directory and must contain:

    Django
    gunicorn

These are the libraries that heroku will install when you deploy. Note that the newest version of the libraries will install.


Procfile
--------

Another which is a file named `Procfile` (Note capital letter) in your project root directory, and it must contain the following line BUT sustitute `<PROJECT_APP>` with your 'project app' name (Note the deliberate '-' at the end of the line):

    web: gunicorn <PROJECT_APP>.wsgi --log-file -

But what is the 'project app' name?

Your file structure could look something this:

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

With the above example, `my_django_project` is the 'project' name, while `main` is the 'project app' name. Our example shows the 'project' and 'project app' to have the same name but it is typical for the 'project' name and 'project app' name to be the same.

Almost there
------------

You got to now remember to `git add` the Procfile and requirements.txt, or else those files are not pushed to Heroku.
