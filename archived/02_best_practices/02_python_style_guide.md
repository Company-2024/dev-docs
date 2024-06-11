# Python Code Style Guide

<!-- https://stackoverflow.com/questions/52827463/collections-iterable-vs-typing-iterable-in-type-annotation-and-checking-for-iter -->

This style guide is an extension of the
[PEP 8](https://peps.python.org/pep-0008/) style guide for details not given in
[PEP 8](https://peps.python.org/pep-0008/).

## General Rules

- Use type hinting. See [type hinting section](#).
- Write docstrings for functions. See [documentation section](#).
- Comment your code. Some things may be easy to follow as you are working on the
  code but when you come back a year later, you will need to sit for an hour to
  understand it. I believe the "good code is self documenting" quote is only
  partly true.
- Do not leave any lines of code commented out because that is confusing as
  \_\_\_. If you really must, have another comment that states why it was
  commented out.
- Always use key word arguments for calling functions/methods you wrote
  yourself. This is because when you change things, you will need to alter that
  everywhere else you called the function. The situation becomes worse when the
  wrong arguments is of the same type as the new argument; then the function
  will happily use the wrong argument.

## Collections

- To check if sequences are empty, in accordance with
  [PEP 8](https://peps.python.org/pep-0008/), use the fact that empty sequences
  are false:

  ```python
  # Good:
  if not seq:
  if seq:

  # Bad:
  if len(seq):
  if not len(seq):
  ```

## Mixins

```python
class A:
    def __init__(self, a_arg, *args, **kwargs):
        # Re-add any used argument to arguments list
        kwargs["a_arg"] = "a_arg"

        # Forward unused arguments to next method in MRO
        super().__init__(*args, **kwargs)

        print(f"Hello from class A with arg {a_arg}.")

class B:
    def __init__(self, b_arg, a_arg, *args, **kwargs):
        print(f"Hello from class B with arg {b_arg}.")
        print(a_arg)


class C(A, B):
    def __init__(self, a_arg, b_arg):
        super().__init__(a_arg, b_arg)

c = C("a_arg", "b_arg")
```

## Docstrings

- For default values, add `Defaults to <value>` at the and of the argument
  description. Note that the value is code, therefore enclose in pairs of
  backticks, with the exception of numerical values. There is no need to add the
  quotes for strings as that is implied.

### Return

- For returns `None`, not that `None` is a keyword; therefore, enclose in pairs
  of backticks.

### Example

<!-- https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html -->

### References/ Citations

Bibliographies in docstrings are generated using the
[sphinxcontrib-bibtex extension](https://sphinxcontrib-bibtex.readthedocs.io/).
See the
[documentation](https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html)
for the extension on how use it.

In the docstring, you will need to use the following syntax:

```
See :cite:`Strunk1979` for an introduction to stylish blah, blah...
```

and then at the end of the docstring, place the directive:

```
..bibliography:: bibliography.bib
```

where `bibliography.bib` is a file containing a BibTex bibliography e.g.:

```
@book{Strunk1979Elements,
  title = {The Elements of Style},
  publisher = {Macmillan},
  year = {1979},
  author = {Strunk, Jr., William and E. B. White},
  edition = {Third}
}
```
