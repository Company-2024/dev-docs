# General Rules

## Configuration

Everything should be configured via a configuration file e.g. a `params.yaml`.
The user should never have to go into the code to set anything except for the
configuration filepath.

During prototyping, each run should have a separate parameters file even if it's
just a duplicate of another. This minimises confusion as one would have to guess
or scour through the code which parameter files belong to what experiments. This
file must be named according to the usual experiment run name convention.

## Naming Conventions

- When dealing with quantities with units, the variable name should be followed
  by the unit e.g.

```python
# Good
center_frequency_Hz = 1000
```

```python
# Bad
center_frequency = 1000
```

## Comments

- Functions/methods should not be longer than 30 lines. Refactor your code to
  make calls to other smaller functions/methods BUT ensure you use good,
  descriptive function/method names that abstract a single idea. If you can't
  think of a good name, please don't create a secret language that only the
  painfully initiated can speak.

- Input shapes can be lifesavers. Include them in comments.

- Comment your code but remember, LESS IS MORE. Comments can add clutter and
  noise to your code, making it difficult to read. Additionally, they can lead
  to errors or inconsistencies if they don't align with your code changes.
  Moreover, comments are often ignored or skipped if they are too long, too
  frequent, or too vague. Lastly, comments can be a sign of bad code smell,
  indicating that your code is too complex or poorly written and needs to be
  refactored or rewritten.

  Code comments, are best reserved for explaining the code's intent rather than
  what it does. The code should be written to a standard where someone can read
  the lines directly and understand what will happen in execution.

## Function Arguments

- Do not use 0, [], {} etc. as default arguments. Use `None` instead.
- Where necessary, do keyword argument assignment to minimise mistakes e.g.:

  ```
  foo(name=x, value=1, ...)
  ```

  instead of

  ```
  foo(x, 1, ...)
  ```

  Follow the general rules:

  1. If it is hard to infer the purpose (name) of the argument from the function
     name – pass it by keyword (e.g. I wouldn't want to have
     text.splitlines(True) in my code).
  2. If it is hard to infer the order of the arguments, for example if you have
     too many arguments, or when you have independent optional arguments – pass
     it by keyword (e.g. funkyplot(x, y, None, None, None, None, None, None,
     'red') doesn't look particularly nice).
  3. Never pass the first few arguments by keyword if the purpose of the
     argument is obvious. You see, sin(2\*pi) is better than sin(value=2\*pi),
     the same is true for plot(x, y, z).

  See
  [this](https://stackoverflow.com/questions/7041752/any-reason-not-to-always-use-keyword-arguments)
  for the full discussion.

## Paths

- Always use `pathlib.Path` for dealing with paths. This much better than the
  `os` module which represents paths as strings that can't do much.
- For paths as arguments, the argument type should always be a string and then
  if any conversions need to be done to the path type, then the function/method
  must handle this.
- If you find yourself with more than two lines of code that look similar then
  you are, redudantly, repeating something that should be in a function.

## Datasets

When writing classes for datasets i.e. inheriting `torch.utils.data.Dataset`,
implement an `__init__` method that allows you to create the dataset without
arguments and performs an initialisation of an empty dataset with all the
required amenities.

Data must always be normalised as a part of preprocessing.

A data file must be named in such a way that the first set of characters before
an underscore in the filename is the label. Never use a `labels.csv` file. This
is difficult to keep up to date and for every modification made, you will need
to update this.

## Data Augmentation

- This should only be done after the train and test split.
