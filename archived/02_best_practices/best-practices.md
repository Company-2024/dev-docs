# Best Practices

## Miscellaneous
* Do not use tensorflow or pytorch in utilities because one would have to install both to use the utility library.

## Path Handling
* Always use ```pathlib.Path```.
* When passing paths into a function, the argument should always be a string
and then the function should be responsible for the conversion of the string to
a ```pathlib.Path``` object. It is inconsequential if the user of the function
passes a ```pathlib.Path``` object instead of a string.