# Tech Stack

Our tech stack comprises the following components. Refer to [Setup Guides](#)
for details on how to correctly configure some of them.

## Programming Languages

Our standard for most machine learning and data science tasks is Python. When
there high performance is essential, we use C++ and if on embedded systems with
no need forC++ features, we use C.

## Deep Learning Frameworks

### PyTorch

The core deep learning framework we use is [PyTorch](https://pytorch.org/). This
is because of its widespread adoption in the research community which allows us
to leverage research very quickly. Read
[OpenAI's blog on why they standardised PyTorch](https://openai.com/index/openai-pytorch/).
There may, however, be rare are exceptions will need to use
[TensorFlow](https://www.tensorflow.org/).

Refer to the
[PyTorch installation documentation](https://docs.anaconda.com/miniconda/miniconda-install/)
for installation details.

<!-- Link to specific setup guides for each. -->

## Python Environment

### Conda

For most of our machine learning projects, we will use Conda as our package
manager because this allows for installation of other things such as CUDA and
cuDNN within the environment which creates flexibility to use different versions
for different projects with ease.

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

### Virtual Environment

## MLOps

### Data Versioning Control (DVC)

### MLflow

## DevOps

<!-- Link to DevOps stack -->
