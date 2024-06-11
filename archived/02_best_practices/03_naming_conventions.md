# Naming Conventions

## Dataset Naming

- The most widely used convention for naming a file corresponding to a data item
  is to have the label followed by an underscore and the followed by any other
  text you wish included in the name. All algorithms in Peralex machine learning
  libraries assume this notation.

## Function and Class Naming

- Be as descriptive as possible. Try to keep the name short but if you can't do
  that, it is better to have a very long, descriptive function name than a short
  ambiguous one.
- For helper functions, you might want to start the function name with `perform`
  e.g. `perform_split` which indicates that this is the function where the
  actual thing is happening.

## Variable Naming

### Data

`inpt`**:** A single data item input into a machine learning model or algorithm.
This may be a feature vector or a raw data vector. It is also referred to, in
other literature, as record, observation, instance, or sample<sup>1</sup>. There
is no, agreed upon, standard about the terminology. 'Input' is used in popular
textbooks \[1, 2\] and both PyTorch and TensorFlow use it. It is not only the
most intuitive and descriptive of the terms but also applies in various
scenarios e.g. training, inference and data analysis. 'Example' is a commonly
used option but this may imply an input-label pair. 'Input' doesn't create such
ambiguity. \
`inputs`**:** A collection of above mentioned `inpt` items. \
`target`**:** The output that is expected for a given output. In classification,
this should, unless with good reason, be an integer corresponding to the index
of the class to which the input belongs. 'Target' is the preferred term in
PyTorch and is used for such things as `target_transform`. Also see `label`. \
`targets`**:** A collection of above mentioned `target` items. \
`pred`**:** A prediction, by the model, of what the `target` is. \
`preds`**:** A collection of above mentioned `pred` items. \
`label`**:** A string corresponding to the label of a given input. This should
be the actual name of the input e.g. 'dog' or 'cat'. \
`labels`**:** A collection of above mentioned label items. \
`pred_label`**:** A prediction, by the model, of what the `label` is. \
`pred_labels`**:** A collection of the above mentioned `pred_label` items. \
`feature`**:** A data item, which is a representation of a raw data item,
containing the most important characteristics of the raw data for machine
learning. Unless with good reason not to, use `inpt` and `inputs` as these terms
are more generally applicable. \
`features`**:** A collection of above mentioned feature items.

<sup>1</sup>'sample' may also refer to a collection of inputs.

- Do not use `x` and `y` for `inputs` and `targets` unless if the scope is very
  small and mathematical otherwise the variable name are not descriptive at all.

### Paths

`*_dir`**:** Path to a named directory. May be a string or a `pathlib.Path`
object. However, if you need both in the same scope, for the `Path` object use
`*_dir_path_obj`. This allows you to use `*_dir` as a string function argument.
\
`filepath`**:** Path to any file. May be a string or a `pathlib.Path` object. However,
if you need both in the same scope, for the `Path` object, use `filepath_obj`. This
allows you to use `filepath` as a string function argument. \
`*_filepath` **:** Path a named file. May be a string or a `pathlib.Path`
object. However, if you need both in the same scope, for the `Path` object, use
`*_filepath_obj` This allows you to use `*_filepath` as a string function
argument.

## Bibtex

- A typical convention for the citing key in Bibtex citations, used by Google,
  Arxiv etc., is `author_last_nameYYYYfirst_significant_word_from_title` e.g.:

```
@misc{miller2021class,
      title             =     {Class Anchor Clustering: a Loss for Distance-based Open Set Recognition},
      author            =     {Dimity Miller and Niko Sünderhauf and Michael Milford and Feras Dayoub},
      year              =     {2021},
      eprint            =     {2004.02434},
      archivePrefix     =     {arXiv},
      primaryClass      =     {cs.CV}
}
```

## Bibliography

\[1\] Bishop, C. M. (2007). Pattern Recognition and Machine
Learning. Switzerland: Springer. URL:
https://www.microsoft.com/en-us/research/uploads/prod/2006/01/Bishop-Pattern-Recognition-and-Machine-Learning-2006.pdf
. \
\[2\] Ian Goodfellow, Yoshua Bengio, & Aaron Courville (2016). Deep Learning. MIT
Press. URL: https://www.deeplearningbook.org/ .
