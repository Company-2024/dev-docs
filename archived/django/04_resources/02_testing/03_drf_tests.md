# Django REST Framework Testing

Again, we will use pytest.

This doumentation serves to give only a simple blueprint for testing Django REST
framework (DRF) related code in the context of E-commerce-23 projects. Ensure
you have read through and understood the detailed
[Django REST Framework documentation on testing](https://www.django-rest-framework.org/api-guide/testing/)

## Viewsets

To validate our view behavior we use the
[DRF `APIClient`](https://www.django-rest-framework.org/api-guide/testing/#apiclient).
This class acts like a dummy web browser that we can use to simulate GET and
POST requests on a URL and observe the response. We can see almost everything
about the response, from low-level HTTP (result headers and status codes)
through to the template we're using to render the HTML and the context data
we're passing to it. We can also see the chain of redirects (if any) and check
the URL and status code at each step. This allows us to verify that each view is
doing what is expected.

The
[DRF `APIRequest Factory`](https://www.django-rest-framework.org/api-guide/testing/#apirequestfactory)
may also be considered. However, it is rarely used.

These extend the Django `Client` and `RequestFactory` classes respectively.

According to
[this SO answer](https://stackoverflow.com/questions/30992377/django-test-requestfactory-vs-client),
The `RequestFactory` is only a factory to create request objects. Nothing more,
nothing less.

The `Client` is used to fake a complete request-response cycle. It will create a
request object, which it then passes through a WSGI handler. This handler
resolves the url, calls the appropriate middleware, and runs the view. It then
returns the response object. It has the added benefit that it gathers a lot of
extra data on the response object that is extremely useful for testing.

## Links

[Testing - Django REST Framework](https://www.django-rest-framework.org/api-guide/testing/)
