# Python in Heroku

##### Setup verification

```
python --version or python -V
pip --version
pipenv --version and pipenv check
which psql
```

##### Configuration

```
Procfile
web: gunicorn gettingstarted.wsgi --log-file -

Pipfile
A configuration file used by Python's dependency manager Pip (just like package.json for node)
Heroku recognizes an app as a Python app by the existence of a Pipfile or requirements.txt file in the root directory.
Heroku installs the appropriate Python dependencies using the pipenv install --system --skip-lock command.

To do this locally, use Pipenv to create a virtualenv and install your dependencies
pipenv --three
pipenv install

Stuck at this installation due to local.......
```



