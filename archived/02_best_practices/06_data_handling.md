# Data Handling

Observe the following rules for data handling:

* Use [scikit-learn](https://scikit-learn.org/stable/) for all your data handling. This not only allows for utitlity functions which are reusable across PyTorch and TensorFlow code bases but also, scikit-learn has better functionality e.g. the ability to split data while keeping the same proportions across all classes.
* When splitting datasets into train, validation and test sets, use [scikit-learn](https://scikit-learn.org/stable/)'s `train_test_split` with the `stratify` parameter so as to ensure that the proportion of values in the sample produced will be the same as the proportion of values provided to parameter `stratify`. This keeps the datasets balanced. With very small or very imbalanced data sets, it's quite possible that the random split could completely eliminate a class from one of the splits.