# Getting Started

There are various software and hardware tools you will require to work on
Peralex Machine Learning projects and we'll discuss how to set them up here.

## Hardware and Firmware

Apart from the obvious hardware required to develop code, you will require an
NVDIA Graphics Processing Unit (GPU). Ensure that your GPU is compatible with,
at least, CUDA 11.7. See
[this](https://en.wikipedia.org/wiki/CUDA#:~:text=GPUs%20supported%5B,%2Donly%20products)
for details on compatibility of NVDIA GPUs with CUDA.

### GPU Setup

Installing a GPU into a desktop PC is pretty simple. Follow
[this guide](https://www.youtube.com/watch?v=HoLv2s23mMQ&ab_channel=DigitalTrends).

For the next steps, you will need to know the exact name of your GPU:

- [Check GPU name on Windows](https://www.microsoft.com/en-us/windows/learning-center/how-to-check-gpu#:~:text=Check%20GPU%20from%20Settings,be%20shown%20under%20Display%20information.)

After this, you will need to
[download NVDIA GPU drivers](https://www.nvidia.com/download/index.aspx).

You need not worry about installing CUDA and cuDNN yet, unless if you would like
a system-wide installation, as this needs to be installed via Conda.

## Setting Up the Development Sofware

The software setup is divided into three components which are setting up
stand-alone software, setting up a Conda environment and installing softaware in
the Conda environment.

### Stand-alone Software

Download and set up the following stand-alone software:

1. **An Integrated Development Environment (IDE) or text editor (e.g. PyCharm or
   VSCode):**<br> PyCharm and Visual Studio Code (VSCode) are the most
   recommended software for writing and editing your code. PyCharm is the most
   recommended tool for writing Python code whereas VSCode is the most
   recommended for all other code.

   PyCharm, being an IDE, is more resource intensive but offers a wide range of
   features that ensure that your Python code is of the highest quality.

   VSCode is a text editor and is more lightweight but has a vast library of
   extensions to also help you write high quality code. If you do use VSCode for
   writing Python code, ensure that it has been properly configured with the
   appropriate extensions and linting otherwise, unless you know the entire
   [PEP 8](https://peps.python.org/pep-0008/) off by heart, you will come to
   find that your code is of unacceptable quality.

   - [Download the official Pycharm](https://www.jetbrains.com/pycharm/download/#section=windows)
     or
   - [Download the offical VSCode](https://code.visualstudio.com/download).<br><br>

2. **Anaconda or Miniconda \[recommended\]:**<br> Anaconda is a popular
   open-source distribution of the Python and R programming languages used for
   data science and machine learning. It comes with Conda &mdash; a package
   management system and environment management system used for managing
   packages and dependencies &mdash; and includes a variety of packages and
   tools that are commonly used in data science, such as NumPy, Pandas,
   Matplotlib, Scikit-learn, and Jupyter Notebook.

   Miniconda is a minimal installer for Conda and allows you to create a conda
   environment containing only Conda, its dependencies, Pip and Python. Use this
   if you would like to save on memory.

   Conda is used instead of regular virtual environments for ease of use of
   various Python versions, installation of various versions of CUDA and cuDNN
   and several other advantages which we don't need to carry on listing here.

   - [Download the official Anaconda](https://www.anaconda.com/download) or
   - [Download the official Miniconda](https://docs.conda.io/en/latest/miniconda.html).<br><br>

### Conda Environment Setup

Launch Anaconda Prompt and do the following:

#### Configuring Proxy Settings

For a fresh install of Conda, from any Conda environment, set Conda to use the
Peralex proxy by running:

```
conda config --set proxy_servers.http http://proxy.ct:3128
conda config --set proxy_servers.https http://proxy.ct:3128
```

and then do the same for Pip by running:

```
set https_proxy=http://proxy.ct:3128
set http_proxy=http://proxy.ct:3128
```

otherwise you may have trouble installing packages.

> NOTE: Most proxies use an unencrypted traffic to the proxy. So make sure the
> URLs to your proxy are both http://.

#### Creating the Environment

Already existing projects should come with an `environment.yml` file which you
should use to create your Conda environment by running the command:

```
conda env create -f environment.yml
```

However, if you are starting a new project or if you wish to create a personal,
general purpose environment (which is recommended to save on time and memory),
run the command:

```
conda create -n <environment_name> [python=x.x] [space_separated_packages]
```

See [Naming Conventions](#) for how environments should be named.

Activate your new environment:

```
conda activate <environment_name>
```

#### Adding Project Library Directories to Python Path

It is advisable to add any directories in which you want the Python interpreter
to search for local packages. This is done using `conda develop`. If you are
using Miniconda, this is not installed by default and you need to first install
`conda-build` which comes with `conda develop` by running:

```
conda install conda-build
```

> NOTE: Ensure that you install this before installing several other packages
> otherwise you may face challenges with conflicts.

After this, you may then add the local library paths by running:

```
conda develop /path/to/project/lib/
```

It is also a good idea to add the project root so that your Python scripts have
access to all files within the project root i.e. run:

```
conda develop /path/to/project/root/
```

### Environment Software and Packages

Having created and configured your Conda environment, you may now install any
packages or software that you wish to install in the environment. You can either
use `conda install` or `pip install` depending on the package/software's
availability. Here, some noteable packages/software are discussed.

1. **CUDA and cuDNN**<br> [CUDA](https://developer.nvidia.com/cuda-toolkit)
   (Compute Unified Device Architecture) and
   [cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network
   library) are technologies developed by NVIDIA that play a crucial role in
   accelerating deep learning and general-purpose computing on NVIDIA GPUs
   (Graphics Processing Units). For the Peralex Machine Learning projects, both
   software are installed via Conda into the Conda environment to allow for
   support of various versions without too much effort.

   **Windows**<br> The generic command for installation is:

   ```
   conda install -c conda-forge cudatoolkit=x.x cudnn=x.x
   ```

   For PyTorch, it is recommended that you install CUDA 11.7 and cuDNN 8.4 by
   running:

   ```
   conda install -c conda-forge cudatoolkit=11.7 cudnn=8.4
   ```

   For TensorFlow, it is recommended that you install CUDA 11.2 and cuDNN 8.1 by
   running:

   ```
   conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
   ```

2. **PyTorch**<br> PyTorch is an open-source machine learning library and
   framework primarily developed by Facebook's AI Research lab (FAIR). It is the
   standard framework used for Peralex Machine Learning projects.

   **Windows**<br> To install PyTorch for CUDA 11.7 on Windows, run the command:

   ```
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117
   ```

   There are other means to install it e.g. using Conda, LibTorch etc. Pip is
   recommended because it is, typically, the most up to date and would result in
   less conflicts with other packages installed via pip.

   For other installation methods or versions of PyTorch, see the
   [official documentation](https://pytorch.org/).

3. **TensorFlow**<br> TensorFlow is PyTorch's counterpart, developed by the
   Google Brain team. While we don't, ordinarily, use this, if you need to
   install it, execute the following instructions.

   **Windows**<br> Run the command:

   ```
   # Anything above 2.10 is not supported on the GPU on Windows Native
   python -m pip install "tensorflow<2.11"

   # Verify install:
   python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
   ```

4. **Black**<br>
   [Black](https://black.readthedocs.io/en/stable/the_black_code_style/index.html)
   is a [PEP 8](https://peps.python.org/pep-0008/) compliant, opinionated code
   formatter. It is installed via Conda:

   ```
   conda install -c conda-forge black
   ```

   or pip

   ```
   pip install black
   ```

   After installing Black into your environment, integrate it into your IDE or
   text editor by following the
   [instructions for editor integration](https://black.readthedocs.io/en/stable/integrations/editors.html).

   If you would like to also format Jupyter notebooks, use
   [jupyter-black](https://github.com/n8henrie/jupyter-black). This is a fork of
   [nb_black](https://github.com/dnanhkhoa/nb_black) with improvements. Install
   jupyter-black by running:

   ```
   pip install jupyter-black
   ```

   and load it into your notebook using

   ```
   %load_ext jupyter_black
   ```

   See
   [the Github repository for jupyter-black](https://github.com/n8henrie/jupyter-black)
   for more details and additional features.

5. **Jupyter**<br> [Jupyter](https://jupyter.org/) is an open-source interactive
   computing environment that allows you to create and share documents
   containing live code, equations, visualizations, and narrative text.

   Two Jupyter tools of interest are Jupyter Lab and Jupyter Notebook which
   allow you to work with live code, equations, visualizations, and narrative
   text. Jupyter Lab expands on the capabilities of Jupyter Notebook by
   providing a more comprehensive and flexible interface.

   You may install Jupyter Lab by running the command

   ```
   pip install jupyterlab
   ```

   or

   ```
   conda install -c conda-forge jupyterlab
   ```

   and you may install Jupyter Notebook by running the command

   ```
   pip install notebook
   ```

   or

   ```
   conda install -c anaconda jupyter # this will also install Jupyter Lab
   ```

   The latter method to install Jupyter Notebook will also install Jupyter Lab.
   [Read more about this](https://stackoverflow.com/questions/75991405/why-is-conda-install-jupyter-installing-jupyter-lab).

   Jupyter Lab also comes with a native desktop version.
   [Download and install Jupyter Lab desktop](https://github.com/jupyterlab/jupyterlab-desktop).

   > NOTE: See [Ipykernel](#) for installation of a kernel to be used with
   > Jupyter tools.

6. **Ipykernel**<br> Ipykernel is a Python package that provides the IPython
   kernel for Jupyter. The IPython kernel is the computational engine that runs
   code in Jupyter Notebooks and other Jupyter interactive environments.

   Install by running:

   ```
   conda install ipykernel
   ```

   or

   ```
   pip install ipykernel
   ```

   After this, from Anaconda Prompt and with your desired environment activated,
   set up a kernel for the environment by running:

   ```
   ipython kernel install --user --name=<any_name_for_the_kernel>
   ```

   Now, when you use the notebook, always ensure that it is using the kernel for
   the correct environment.

   To list all kernels, run

   ```
   jupyter kernelspec list
   ```

   and to remove a kernel, run

   ```
   jupyter kernelspec uninstall <name_of_unwanted_kernel>
   ```

   > IMPORTANT: You may notice that when you run your code in the notebooks, you
   > cannot detect some packages or CUDA etc. This may be because you are
   > actually using the default Python interpreter and not the one for the
   > desired environment.

### Final Setup

git config --global submodule.recurse true

<!--
MLproject: https://www.youtube.com/watch?v=l6oZJ8y9M1o&t=87s , https://mlflow.org/docs/latest/projects.html#overview
Create a template.py. Project structure: https://dev.to/luxacademy/generic-folder-structure-for-your-machine-learning-projects-4coe
https://medium.com/@haythemtellili/end-to-end-ml-pipelines-with-mlflow-projects-63a11baa2dd1
- main should be in src folder: https://www.reddit.com/r/cpp_questions/comments/xpkvto/should_maincpp_be_in_the_top_level_folder_in_src/
-->
