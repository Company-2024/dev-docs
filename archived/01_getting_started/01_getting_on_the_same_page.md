# Getting on the Same Page

## Architecture

<!-- Make the same block diagram as the one on Neptune's website. -->

## Tech Stack

The following is a list of software tools we use for Peralex AI projects.

1. **[PyTorch](https://pytorch.org/):** PyTorch is an open-source machine
   learning library and framework primarily developed by Facebook's AI Research
   lab (FAIR). It is the standard framework for several tech giants including
   OpenAI, Tesla, Facebook and several others.

   Among the many advantages of PyTorch over TensorFlow, the primary reason we
   have adopted it as our standard is due to its widespread use in academics
   which signficantly reduces the time to implement cutting edge algorithms from
   literature.

2. **[MLflow](https://mlflow.org/):** For MLOps, we use a combination of MLflow
   and DVC for experiment tracking and data versioning respectively.

   MLflow is an open-source platform for managing the end-to-end machine
   learning lifecycle. It tackles four primary functions:

   - Tracking experiments to record and compare parameters and results (MLflow
     Tracking).
   - Packaging machine learning code in a reusable, reproducible form in order
     to share with other data scientists or transfer to production (MLflow
     Projects).
   - Managing and deploying models from a variety of machine learning libraries
     to a variety of model serving and inference platforms (MLflow Models).
   - Providing a central model store to collaboratively manage the full
     lifecycle of an MLflow Model, including model versioning, stage
     transitions, and annotations (MLflow Model Registry).

   There are other tools which do similar things to MLflow and several
   comparisons of these tools.

   MLflow and Weight and Biases are, according to Github statistics, by far the
   most popular. Weights and Biases's main shortcoming, however, is that it is
   not open-source and is more of a costly cloud offering. Furthermore, MLflow
   allows for management of the full end-to-end machine learning lifecycle
   unlike other platforms.

   See the article: [Experiment Tracking with MLflow](#) for details on how to
   use it in Peralex AI projects.

3. **[Data Version Control (DVC)](https://dvc.org/):** DVC is an open-source,
   Git-based data version control tool which helps with sharing of datasets and
   reproducibility of experiment results. It also has a component of experiment
   tracking; however, this is nowhere near as developed as MLFlow and as a
   result, both are used in conjunction with each other.

<!-- Tsaug: Data augmentation -->
