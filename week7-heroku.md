Heroku
======

- Sign up and log in in heroku.com and create a new app, pick a name (eg. my-fuelwatch-app)and any country with no pipeline.
- Install the CLI tool as specified under the 'Deploy' tab.
- Follow the rest of the instructions under "Deploy using Heroku Git", you can `git init` but do NOT just do `git add. ` because that will add the .pyc and .sqlite files which is not what you want in the Git repository. So `git add` the .py and .html files one by one and commit.
- Remember to run `heroku login` to login.
- then do `heroku git:remote -a my-fuelwatch-app`
- and finally `git push heroku master`.
