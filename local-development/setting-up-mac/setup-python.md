# Python

##### Installation

```
MacOS comes pre-installed with Python 2.x. If something goes wrong
> brew install python         // Installs Python 2.x
> brew install python3        // Installs Python 3.x
```

##### Commands

```
> python -m site --user-base            // Find the user base binary directory
```

> Homebrew doesn't know how to install pip or distribute. Luckily both can be easily installed with python scripts available on web.

##### Package Manager

```
There are few package managers specific for Python, and pip is the preferred one.

Installation
> curl -O https://raw.github.com/pypa/pip/master/contrib/get-pip.py
> python get-pip.py

Version check
> pip -V
> pip2 -V
> pip3 -V

> pip install -U pip            // Upgrading pip
```

##### Packages

```
> pip install numpy            // Vectors and matrices in Python
> pip install scipy            // Other scientific computing tools
> pip install pandas           // Dataframes in Python!
> pip install biopython        // Most commonly used Biocomputing Python library
> pip install jupyter          // IPython Notebook is part of Jupyter now. Another populate Biocomputing tool
```



