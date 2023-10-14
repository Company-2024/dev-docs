# Django Project Testing

<!--
- Store providers in Python file for speed.
-->

"Code without tests is broken as designed." &mdash; Jacob Kaplan-Moss

Use a collection of tests – a test suite – to solve, or avoid, a number of
problems:

- When you’re writing new code, you can use tests to validate your code works as
  expected.
- When you’re refactoring or modifying old code, you can use tests to ensure
  your changes haven’t affected your application’s behavior unexpectedly.

The pytest framework makes it easy to write small, readable unit tests, and can
scale to support complex functional testing for applications and libraries.

## Testing Libraries

### pytest and pytest-django

[pytest](https://docs.pytest.org/en/7.4.x/) is adopted over Django’s built-in
test-execution framework, which uses Python's
[unittest](https://docs.python.org/3/library/unittest.html#module-unittest).
According the
[pytest-django documentation](https://pytest-django.readthedocs.io/en/latest/)
and the
[Testing Your Django App With Pytest - djangostars](https://djangostars.com/blog/django-pytest-testing)
article, the advantages of using pytest over Django's testing mechanism include
the following:

- Less boilerplate: no need to import unittest, create a subclass with methods.
  Just write tests as regular functions.
- Manage test dependencies with fixtures (explicit, modular, scalable).
- Additional features of fixtures (auto-use, scope, request object, nested,
  finalizers, etc.).
- Run tests in multiple processes for increased speed.
- There are a lot of other nice plugins available for pytest.
- Easy switching: Existing unittest and nose test suites tests will still work
  without any modifications.
- Assert statements (no need to remember `self.assert*` names).
- Detailed information on failures.
- [Marks](https://doc.pytest.org/en/latest/how-to/mark.html#mark).
- [Parameterizing](https://docs.pytest.org/en/latest/how-to/parametrize.html)

[pytest-django](https://pytest-django.readthedocs.io/en/latest/) is a plugin for
pytest, created by the pytest developers, that provides a set of useful tools
for testing Django applications and projects.

The rest of this section discusses how to use pytest for unit testing in a
Django project. Refer to the
[pytest documentation](https://docs.pytest.org/en/stable/contents.html) and
[pytest-django documentation](https://pytest-django.readthedocs.io/en/latest/)
for further details.

The core elements of pytest are as follows:

- Writing and report assertions in tests
- [Fixtures](https://docs.pytest.org/en/stable/how-to/fixtures.html)
- Marking test functions with attributes
- Parametrizing fixtures and test functions
- Using temporary directories and files in tests
- Monkeypatch/mock modules and environments
- Doctests
- Re-running failed tests and maintaining state between test runs

### factory_boy

The purpose of
[factory_boy](https://factoryboy.readthedocs.io/en/stable/introduction.html#basic-usage)
is to provide a default way of getting a new instance, while still being able to
override some fields on a per-call basis.

This is adopted over Model Bakery.

<!--
- Strong relationship between faker and factory-boy.
-->

### Faker

[Faker](https://faker.readthedocs.io/en/master/) is a Python package that
generates fake data for you.

This is installed when you install factory_boy.

## Using pytest for Testing

### Installation

```
pip install pytest-django
```

Installing pytest-django will also automatically install the latest version of
pytest. pytest-django uses pytest’s plugin system and can be used right away
after installation, there is nothing more to configure.

### Configuring pytest Settings

Create a file, at the project root, named `pytest.ini` containing configurations
for your testing.

Point pytest to your settings file by defining the `DJANGO_SETTINGS_MODULE` in
the configuration file e.g.:

```
[pytest]
DJANGO_SETTINGS_MODULE = yourproject.settings
```

Django settings can also be specified by setting the `DJANGO_SETTINGS_MODULE`
environment variable or specifying the `--ds=yourproject.settings` command-line
flag when running the tests. See the full documentation on
[Configuring Django settings](https://pytest-django.readthedocs.io/en/latest/configuring_django.html#configuring-django-settings).

### Writing the Tests

We use Django's testing philosophy i.e. test grouping, setting up, teardown
etc.: it's almost as though we are writing code for testing with Django's
in-built testing functionality.

#### Models

For each model create a `Test<ModelName>` class which groups tests for that
model.

```python
@pytest.mark.django_db
class TestCategoryModel:
    """Unit tests for the ``Category`` model."""

    @pytest.fixture(autouse=True)
    def setup_test_db(self, db):
```

- `setup_test_db` is an
  [autouse fixture](https://docs.pytest.org/en/stable/how-to/fixtures.html#autouse-fixtures-fixtures-you-don-t-have-to-request).

## Using factory_boy and Faker for Testing

In an app, create a `factories` directory where you define factory_boy factories
for the model.

```
import factory
from . import base

class UserFactory(factory.Factory):
    class Meta:
        model = base.User

    firstname = "John"
    lastname = "Doe"
```

## Best Practices

### Organising Testing Code

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

### What to Test

You should test all aspects of **your own** code, but not any libraries or
functionality provided as part of Python or Django i.e. test aspects which could
be changed by another developer from your code base.

## Troubleshooting

[pytest ScopeMismatch error](https://stackoverflow.com/questions/51783757/pytest-scopemismatch-error-how-to-use-fixtures-properly)

## Links

[Django Tutorial Part 10: Testing a Django web application - Mozilla](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Testing)
[Testing Your Django App With Pytest - djangostars](https://djangostars.com/blog/django-pytest-testing)
