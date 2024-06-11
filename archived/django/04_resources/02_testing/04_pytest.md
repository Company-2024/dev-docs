# PyTest

The `@pytest.mark.django_db decorator` is used to ensure that the test runs in a
database transaction so that any changes made during the test are rolled back
after the test is complete.
