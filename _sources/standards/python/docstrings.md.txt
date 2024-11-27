## Docstrings

### Docstring Style

Use Google style docstrings as these are easier to read than reStructuredText or
the Numpy style. An example can be found
[here](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html).

### Return Value(s)

Document a single return value as follows (note the indentation levels):

```python
"""
Returns:
    <rtype>:
        <Description>
"""
```

The RTD theme will detect the return type automatically.

Where the value is an iterable, give the shape in the description e.g.

```python
"""
Returns:
    numpy.array:
        A numpy array of shape (n_classes, n_classes) representing the input.
"""
```
