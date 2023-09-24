# Getting Started with Django Projects

## Configuring the Project

### Configure `PYTHONPATH`

To add directories in which the Python interpreter is to search for included
packages and modules, create a `<name>.pth` file in one of the appropriate
virtual environment directories e.g. a `venv.pth` file in the virtual
environment's `lib/pythonx/site-packages` directory and then add the directories
to the file.

The most important directory to add is the Django app root i.e. the directory
containing the `manage.py` file as this is used by the project for absolute
imports.

See [Configuring `PYTHONPATH`](#) for further details on and alternative methods
of configuring the `PYTHONPATH`.
