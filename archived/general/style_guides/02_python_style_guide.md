# Python Style Guide

## Comments

### Code Organisation Comments

You may want to group code within a module under headings. You are to use the
following style:

```python
###################################
#         Level 1 Heading         #
###################################
```

Note that for the Level 1 heading, the mininimum number of characters on a line
is 35. This is merely an aesthetic choice.

```python
# ===============
# Level 2 Heading
# ===============
```

```python
# ---------------
# Level 3 Heading
# ---------------
```

- Level 1 headings are for major code groupings e.g. separating groups of
  classes or stand-alone functions (not class methods) doing different things.
- Level 2 headings are for less significant code groupings e.g. separating
  groups of class methods doing different things.
- Level 3 headings are for minor code groupings e.g. grouping a bunch of lines
  of code that are doing something which you really need to put under a heading
  of this sort.

Note that you don't necessarily have to have Level 2 code groupings under a
Level 1 grouping. Sometimes it just doesn't make sense to do so.
