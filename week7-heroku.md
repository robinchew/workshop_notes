Heroku
======

- Sign up and log in in heroku.com and create a new app, pick a name (eg. my-fuelwatch-app)and any country with no pipeline.
- Install the CLI tool as specified under the 'Deploy' tab.
- Follow the rest of the instructions under "Deploy using Heroku Git", you can `git init` but do NOT just do `git add. ` because that will add the .pyc and .sqlite files which is not what you want in the Git repository. So `git add` the .py and .html files one by one and commit.
- Remember to run `heroku login` to login.
- then do `heroku git:remote -a my-fuelwatch-app`
- and finally `git push heroku master`.

ERROR!
======

Your push failed! Saying something about:

    No default language could be detected for this app.

You got to add extra things to your project to satisfy heroku. One which is a file named `Procfile` (Note capital letter) in your project root directory, and it must contain the following line BUT sustitute `<PROJECT>` with your 'project app' name::

    web: gunicorn <PROJECT>.wsgi --log-file -

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

With the above example, `my_django_project` is the 'project' name, while `main` is the 'project app' name, and it is typical for the 'project' name and 'project app' name to be the same.
