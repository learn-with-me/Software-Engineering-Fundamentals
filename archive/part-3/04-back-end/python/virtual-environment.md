# Virtual Environment

Python Virtual environments are great to work with. When you're working with multiple projects, there is always a change of having conflict in packages, especially if you are new to the language.

From my personal experience, its just easier to setup a virtual environment, install dependencies, complete development and then get rid of that environment if you don't need it anymore. Maybe Docker is a better choice for experienced developers, however, since virtual environments are light-weight, we can't ignore their use completely.

### Setting up a virtual environment

There are couple of ways we can do it:

#### venv

    # Setting up the environment
    $ python -m venv ~/projects/project_name

    This creates a `pyvenv.cfg` file based on the python version available in your local machine.
    This file defines the root folder of the environment and is mainly responsible for version,
    Python interpreter's path and site-packages configuration.

    # Activating the environment
    $ sh ./bin/activate





