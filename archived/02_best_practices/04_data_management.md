# Data Engineering Best Practices

Meticulous data management is absolutely pivotal to not hating oneself in the
long run during a project. Observe the following rules for data management:

- Keep a zip of the data somewhere.
- Keep your all your raw data in a single directory named `raw` organised into
  subdirectories for each class where the class name is the name of the
  subdirectory. This is the standard followed for such datasets as
  [ImageNet](https://www.image-net.org/download.php) etc.
  <!-- - prepared: If one were to distribute the data, this is what will be distributed. However,
  have a baseline directory in there in case you need to make major changes to the dataset, you can
  just create a new directory in the prepared. Even for preprocessed and raw. This allows you to create
  new datasets for the same category without too much hassle and upheaval in DVC.
  You may need to modify the baseline esp. as you get more
  data or realise that some of the data is useless. That's fine. Just
  track it with DVC. preprocessed: all the data ready for a model but not split.
  Useful for generating new splits, counting all the data, analysing all the data etc. -->
- The most widely used convention for naming a file corresponding to a data item
  is to have the label followed by an underscore and the followed by any other
  text you wish included in the name. All algorithms in Peralex machine learning
  libraries assume this notation. You should never need a `labels.csv` file
  which can very easily get corrupted or fall behind the current version of the
  data. This also makes it very easy to add and remove classes.
- When making significant changes to a dataset e.g. completely removing some
  classes etc., opt for creating a completely different directory for the
  prepared data and track that with DVC. You are, essentially, creating a new
  dataset. However, do this sparingly as it consumes quite a lot of storage
  space.
- Sometimes you will need to get rid of some data. Create a `.trash` directory.
  In the root of the `data` directory. Do not create any other `.trash` folders
  for data elsewhere, otherwise you will not find them when things get chaotic.
  Ensure everything you delete is in a parent directory of some sort with, in
  the very least, a README explaining what the dataset was and why you don't
  need it anymore otherwise it will be a mission. Also track the trash directory
  with DVC. Follow the exact same relative path as the original location of the
  dataset.
- Accompany each dataset with a README.md that, in the very least, describes
  what the dataset is and what its purpose is. If necessary, also include some
  type of metadata file.
- Augment after splitting.
<!-- - Dataset normalisation. -->
