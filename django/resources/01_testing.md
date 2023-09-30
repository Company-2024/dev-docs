# Testing

"Code without tests is broken as designed." &mdash; Jacob Kaplan-Moss

## pytest

pytest is adopted over Django’s built-in test-execution framework, which uses
Python's
[unittest](https://docs.python.org/3/library/unittest.html#module-unittest)
because:

<!-- Do more research on pytest vs. Django. -->

## pytest-django

pytest-django provides an alternative to using Django `manage.py`'s test
command. The following are the advantages, copied directly from the
[pytest-django documentation homepage](https://pytest-django.readthedocs.io/en/latest/),
of using pytest-django, :

## Configuring pytest Settings

## Organising Testing Code

There are three possible ways that one may organise Django testing code, which
are:

- placing all testing code in a monolithic `tests.py` file (not recommended),
- including testing code within each directory for each app, also known as
  embedding, and
- creating a `tests` directory at the project root and then replicating the
  directory structure for all the apps but only placing test files in the
  subdirectories of the `tests` directory, also known as mirroring
  (recommended).

Mirroring is the recommended way to organise the testing code because there is
also need for API tests and integration tests etc. which cannot, necessarily, be
embedded into the apps directories; therefore, centralising all tests is just
more logical.
