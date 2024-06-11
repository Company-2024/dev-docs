# Documentation

<!-- best_practices_more_general_no_style_guide_just_best_practices_and_add_your_styles_in_there_not_redefining_style_guides_like_PEP -->

## Move to Python -- Docstrings

Writing good documentation for classes and functions or methods, through
docstrings, is imperative.

`Important` heading in docstring.

- Use correct punctuation in docstrings even for parameter descriptions albeit
  not being full sentences with a predicte. The only exception is when you don't
  have a full sentence is for single words? See
  [example](https://www.sphinx-doc.org/en/master/usage/extensions/example_google.html)
- Use Google style docstrings as this is the most readable form. See
  [Example Google Style Python Docstrings](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html)
  and
  [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html).
- Inline code:
  https://stackoverflow.com/questions/10870719/inline-code-highlighting-in-restructuredtext
- For code snippets:
  https://stackoverflow.com/questions/64451966/python-sphinx-how-to-embed-code-into-a-docstring
- Doctests:
  https://stackoverflow.com/questions/31227892/python-docstrings-and-inline-code-meaning-of-the-syntax
- [Sphinx](https://www.sphinx-doc.org/en/master/index.html) is used for
  generating documentation and ensure that your docstrings follow the
  [Sphinx](https://www.sphinx-doc.org/en/master/index.html) rules.
- Example.: #https://stackoverflow.com/questions/44577360/google-style-docstring-example-section-is-not-rendering-as-a-code-snippet
- Use LaTeX markup for mathematics. You may use the rST directives `:math:` and
  `.. math::` for inline and display equations e.g.:

  ```
  Inline:
  Since Pythagoras, we know that :math:`a^2 + b^2 = c^2`.
  ```

  ```
  Display:
  .. math::

          x = \\frac{-b \\pm \\sqrt{b^2 - 4ac}}{2a}
  ```

  See
  [documentation](https://sphinx-rtd-trial.readthedocs.io/en/latest/ext/math.html)
  for further details.

- Multiple types in a type field should be separated by the word `or` e.g.:

  ```
  x (int or str): A value.
  ```

  or

  ```
  Returns:
      pathlib.Path or None: The path to the created subdirectory
          if creation of the subdirectory was successful otherwise
          None.
  ```

  See
  [Sphinx documentation on the subject](https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#info-field-lists:~:text=Multiple%20types%20in,float%20or%20str).

- Use `optional` if the user does not need to pass in that argument. This is
  slightly different from `typing.Optional` which means `some_type or None`. In
  fact, if an argument is both optional and can also be `None`, use
  `(some_type or None, optional)`.

### Types

<style>
    table {
        margin-left: auto;
        margin-right:auto;
        width: 90%;
    }
</style>
<table>
<thead>
  <tr>
    <th style="width:25%;">Type</th>
    <th style="width:25%;">Description</th>
    <th style="width:50%;">Example Usage</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>str</code></span></td>
    <td>String</td>
    <td></td>
  </tr>
  <tr>
    <td><code>dict[dtype, dtype]</code></span></td>
    <td>Dictionary</td>
    <td>
        <pre>
        """
        Returns:
            dict: A dict mapping keys to the corresponding table row data fetched. Each row is represented as a tuple of strings. For example:<br>
            {b'Serak': ('Rigel VII', 'Preparer'),
            b'Zim': ('Irk', 'Invader'),
            b'Lrrr': ('Omicron Persei 8', 'Emperor')}<br>
            Returned keys are always bytes.  If a key from the keys argument is missing from the dictionary, then that row was not found in the table (and require_all_keys must have been False).
        """
        </pre>
    </td>
  </tr>
  <tr>
    <td><code>tuple[dtype, dtype, dtype]</code></span></td>
    <td>Tuple</td>
    <td>
        <pre>
        """
        ...
        Returns:
            tuple[list[str], str]: A tuple containing, in that order, the following:<br>
                - The first return value.
                - The second return value.
        """
        </pre>
    </td>
  </tr>
  <tr>
    <td><code>iterable[dtype]</code></span></td>
    <td>Anything that can be iterated over e.g. list, set etc.</td>
    <td></td>
  </tr>
  <tr>
    <td><code>array-like[dtype]</code></span></td>
    <td>Less preferred alternative to <code>iterable</code>.</td>
    <td></td>
  </tr>
  <tr>
    <td><code>Union[dtype]</code></span></td>
    <td>Anything that can be iterated over e.g. list, set etc.</td>
    <td></td>
  </tr>
</tbody>
</table>

### Class Docstring

https://stackoverflow.com/questions/37019744/is-there-a-consensus-on-what-should-be-documented-in-the-class-and-init-docs

### Rules

- For optional arguments and default values do the following:

  ```
  """
  ...
  Args:
      param_1 (int, optional): The first parameters. Defaults to 10.
  ...
  """
  ```

- For consistency with examples given in both
  [PEP 8](https://peps.python.org/pep-0008/) and the
  [Google style guide](https://google.github.io/styleguide/pyguide.html), do not
  skip a line after the opening set of quotes:

  ```
  # Good
  """Does something cool.

  Returns:
      None
  """
  ```

  ```
  # Bad
  """
  Does something cool.

  Returns:
      None
  """
  ```

- For consistency with examples in [PEP 8](https://peps.python.org/pep-0008/),
  use the infinitive form rather than the third person singular form for
  function summaries e.g.:

  ```
  # Good
  def connect():
      """Connect to the next available port."""
  ```

  ```
  # Bad
  def connect():
      """Connects to the next available port."""
  ```

  This is the most popular practice. See libraries such as
  [Django](https://github.com/django/django/tree/main),
  [Scikit-learn](https://github.com/scikit-learn/scikit-learn) etc. Note that
  the [Google style guide](https://google.github.io/styleguide/pyguide.html)
  uses the third person singular form.

- Your types should be lowercase and for composite data types use something like
  `list[str]`. See Sphinx
  [documentation on this](https://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html).

- Give data types where applicable. This is also done by libraries such as
  [Matplotlib](https://matplotlib.org/stable/api/index.html).

- When returning a tuple, based on
  [this SO answer](https://stackoverflow.com/questions/29221551/can-sphinx-napoleon-document-function-returning-multiple-arguments),
  do something like the following:

- Use articles such as 'the', 'a' and 'an' e.g.:

  ```
  # Good
  """
  Args:
      param_1 (int): The first parameter.
  """
  ```

  ```
  # Bad
  """
  Args:
      param_1 (int): First parameter.
  """
  ```

- You must always give a return type. This is an exception to the examples in
  the [Google style guide](https://google.github.io/styleguide/pyguide.html)
  e.g.:

  ```
  # Good
  Returns:
      int: The new value.
  ```

- Follow all the other docstring style rules stated or implied in the
  [Google style guide](https://google.github.io/styleguide/pyguide.html) e.g.:

### Cross Referencing

- https://stackoverflow.com/questions/21289806/link-to-class-method-in-python-docstring

<!--
- Cross reference external libraries: batch (:class:`~torch.Tensor` | (:class:`~torch.Tensor`, ...) | [:class:`~torch.Tensor`, ...]):
-->
