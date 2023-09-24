# Configuring `PYTHONPATH`

PYTHONPATH is an environment variable that specifies a list of directories to
search for Python modules when importing them.

<!-- Set PYTHONPATH in the terminal
You can set PYTHONPATH in the terminal before running a Python script. Here's an example −

$ export PYTHONPATH=/path/to/my/modules/
$ python my_script.py
Set PYTHONPATH in the script
You can set PYTHONPATH in your Python script using the os module. Here's an example −

import os
import sys
sys.path.insert(0, os.path.abspath("/path/to/my/modules/"))
Append to PYTHONPATH
You can append a directory to PYTHONPATH in your Python script using the os module. Here's an example −

import os
import sys
sys.path.append(os.path.abspath("/path/to/my/modules/"))
Use a .pth file
A path configuration file is a file whose name has the form name.pth and exists in one of the four directories mentioned above; its contents are additional items (one per line) to be added to sys.path. Non-existing items are never added to sys.path, and no check is made that the item refers to a directory rather than a file. No item is added to sys.path more than once. Blank lines and lines beginning with # are skipped. Lines starting with import (followed by space or tab) are executed. https://docs.python.org/3/library/site.html
You can create a .pth file in a directory that contains the directories to be added to PYTHONPATH. Here's an example −

$ cat /path/to/my/modules/my_modules.pth
$/path/to/my/modules/
Use a virtual environment
When you create a virtual environment with venv or virtualenv, it automatically sets PYTHONPATH to include the virtual environment's site-packages directory.Here's an example −

$ python -m venv my_virtualenv
$ source my_virtualenv/bin/activate
Use a .env file
You can use a .env file to set environment variables, including PYTHONPATH, for your project. First, install the python-dotenv package using

pip install python-dotenv
Then, create a .env file in the root directory of your project and add the following line to set PYTHONPATH −

PYTHONPATH=/path/to/my/modules/
Finally, load the environment variables from the .env file in your Python script −

from dotenv import load_dotenv
import os
load_dotenv()
sys.path.insert(0, os.getenv("PYTHONPATH"))
Use a package directory structure
You can create a package directory structure where each subdirectory represents a package, and the subdirectories are automatically added to PYTHONPATH. Here's an example:

import my_package.my_module
And import my_submodule like this:

import my_package.my_subpackage.my_submodule
PYTHONPATH is an environment variable that specifies a list of directories to search for Python modules when importing them. This can be useful when you have custom Python libraries that you do not want to install in the global default location. There are several ways to set PYTHONPATH, including setting it in the terminal, setting it in your Python script using the os module, appending to it using the os module, using a .pth file, using a virtual environment, and using a .env file. By using PYTHONPATH effectively, you can organize your Python code more efficiently and make it easier to maintain.

In conclusion, these are some ways to use PYTHONPATH to specify directories to search for Python modules. The method you choose depends on your needs and preferences, but using a virtual environment or a package directory structure are commonly used methods. -->
