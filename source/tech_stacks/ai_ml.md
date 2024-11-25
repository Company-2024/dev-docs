# Machine Learning Stack

Our tech stack comprises the following components. Refer to [Setup Guides](#)
for details on how to correctly configure some of them.

Refer also to the [Python Stack page](#).

## Programming Languages

Our standard for most machine learning and data science tasks is Python. When
high performance is essential, we use C++ and for embedded systems with no
requirement for C++ features, we use C.

## Deep Learning Frameworks

### PyTorch

The core deep learning framework we use is [PyTorch](https://pytorch.org/). This
is because of its widespread adoption in the research community which allows us
to leverage research very quickly. Read
[OpenAI's blog on why they standardised PyTorch](https://openai.com/index/openai-pytorch/).
There may, however, be rare exceptions where you will need to use
[TensorFlow](https://www.tensorflow.org/) or other deep learning frameworks.

Refer to the
[PyTorch website](https://docs.anaconda.com/miniconda/miniconda-install/) for
installation details.

```{note}

Use pip even if you are installing into a Conda environment unless you have a
specific reason for doing otherwise. This is discussed further in
[Conda Setup Guide](#).
```

<!-- Link to specific setup guides for each. -->

## Python Environment

Python development should, at all times, be done within a Conda environment or a
virtual environment.

### Conda

For most of our machine learning projects, use Conda because this allows for
installation of other things such as CUDA and cuDNN within the environment which
creates flexibility to use different versions for different projects with ease.

[Anaconda](https://www.anaconda.com/) is the most popular system by which one
can use Conda. However, we prefer
[Miniconda](https://docs.anaconda.com/miniconda/) which is a miniature
installation of Anaconda distribution which only includes Conda, Python and the
packages they depend on. As a result, Miniconda is smaller and takes up less
storage requirements. Only use Anaconda instead of Miniconda when there is a
specific reason to do so.

Refer to the
[Miniconda installation documentation](https://docs.anaconda.com/miniconda/miniconda-install/)
for installation details.

Also refer to the
[Conda Environment section of the Python Environments setup guide](#) for
details on how to set up your Conda environment.

### Virtual Environment

For simple cases or non-machine learning projects, use Python virtual
environments.

Refer to the
[Virtual Environment section of the Python Environments setup guide](#) for
details on how to set up your virtual environment environment.

## MLOps

Machine learning operations (MLOps) are a set of practices that help to manage
the machine learning (ML) life cycle more efficiently. Below are the tools we
use data management, model management, pipeline management etc.

### Data Versioning Control (DVC)

[Data Version Control (DVC)](https://dvc.org/) is an open-source version control
system specifically designed for dataset version tracking and managing machine
learning models and workflows.

We will only use DVC for dataset version tracking as MLflow is a much better
solution for workflow management.

Refer to the [DVC installation documentation](https://dvc.org/doc/install) for
installation details. It is recommended that you install it as a system
application rather than a Python package so that you can reuse the installation
with ease. However, installing as a Python package is also fine.

### MLflow

[MLflow](https://mlflow.org/) is an open-source end-to-end MLOps platform which
we use for experiment tracking, visualisation, evaluation, model registries
among other things.

Refer to the
[MLflow Tracking Quickstart documentation](https://mlflow.org/docs/latest/getting-started/intro-quickstart/index.html)
for installation details.

## DevOps

Refer to [DevOps Stack](#) page.

<!-- Link to DevOps stack -->