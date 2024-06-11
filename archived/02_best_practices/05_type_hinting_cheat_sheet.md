# Type Hinting Cheat Sheet

# Basics
* For a basic function declaration, type-hint as follows:
    ```
    def <function_name>(<arg_name>: <arg_type>) -> <return_type>:
        ...
    ```

    e.g.:
    ```
    def greet(name: str) -> str:
        return f"Hello, {name}"
    ```

    With default arguments, do something like:
    ```
    def greet(name: str = "Thomas"):
        return f"Hello, {name}"
    ```

* Import types individually from typing to keep the function declaration more readable and clean:
    ```
    # Good
    from typing import Dict, Tuple

    def foo(x: Dict[str, int]) -> Tuple[int, int]
        ...
    ```

    ```
    # Bad
    import typing

    def foo(x: typing.Dict[str, int]) -> typing.Tuple[int, int]
        ...
    ```

    This is what is also used in [PEP 8](https://peps.python.org/pep-0008/), although contradictory to conventional wisdom which says that you should opt to import the package.

* Opt for use of, the more recent, pipe (|) instead of `typing.Union`.
* Try and limit defining aliases to types because one would have to import packages and remember what type represents what etc.

## Types
<table style="margin-left: auto; margin-right:auto; width: 90%;">
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
    <td><code>str|Path</code></span></td>
    <td>Paths</td>
    <td></td>
  </tr>
  <tr>
    <td><code>Optional[...]</code></td>
    <td>Shorthand for <code>Union[..., None]</code></td>
    <td></td>
  </tr>
</tbody>


* For a tuple, use `typing.Tuple`:
    ```
    from typing import Tuple

    def foo(x: Tuple[float, int, str]) -> Tuple[float, int, str]:
        ...
    ```

* For a dictionary, use `typing.Dict`:
    ```
    from typing import Dict

    def foo(x: Dict[str, int]) -> Dict[str, int]:
        ...
    ```

* For Numpy arrays, use `numpy.typing.NDArray`:
    ```
    import numpy.typing as npt

    def foo(x: npt.NDArray[np.float_]) -> npt.NDArray:
        ...
    ```

    According to the [documentation](https://numpy.org/devdocs/reference/typing.html),
    ```
    numpy.typing.NDArray = numpy.ndarray[typing.Any, numpy.dtype[+_ScalarType_co]][source]
    ```

    You don't need to specify the `typing.Any` in any of the cases as you cannot actually add the shape of the array to the type hint. Just specify the data type if needed. 