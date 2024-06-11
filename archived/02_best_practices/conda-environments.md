# Conda Environments

## Creating New Conda Environment
### Anaconda Prompt
Create a new environment via the following command:
```
conda create -n <environment name> [python=x.x] [space separated packages]
```

If for specific project, a recommended name would be ```<repository_name>_py<python_version>``` e.g. ```nb_classification_py310```.

Verify that the environment was created using
```
conda env list
```

and activate the environment using

```
conda activate <environment name>
```

<!-- TODO: Add more details -->

### PyCharm
<!-- TODO: Add more details -->

## Installing Packages
Packages are installed using the standard command
```
conda install [-c <channel>] package_name[=<package_version>]
```
<!-- TODO: <=x.x = -->

However, there are some cases of interest which we'd like to point out.

### CUDA and cuDNN
CUDA and cuDNN can be installed using ```conda``` and this is recommended because it allows for various versions which Tensorflow is particularly picky about.

First determine what CUDA and cuDNN versions the desired version of Tensorflow will accept. See tables on the Tensorflow documentation for [Windows](https://www.tensorflow.org/install/source_windows#gpu) and [Linux/macOS](https://www.tensorflow.org/install/source#gpu).


### TensorFlow
It is generally recommended (even by the TensorFlow organisation itself) to install TensorFlow using Pip rather than Conda in order to obtain the latest versions of the package and because TensorFlow has many dependencies which lead to conflicts with other packages in the environment.

Also ensure that you have installed CUDA and cuDNN.

Follow the steps on the [official Tensorflow documentation for installation](https://www.tensorflow.org/install/pip) and ensure you install the correct versions for your system.

Make sure that when you are creating an ```environment.yml``` file, this is specified under ```pip```.

:::tip ```tensorflow``` vs ```tensorflow-gpu``` 
For TensorFlow<2.0 there are two packages namely ```tensorflow``` and ```tensorflow-gpu```. (See [this SO post](https://stackoverflow.com/questions/52624703/difference-between-installation-libraries-of-tensorflow-gpu-vs-cpu) for more details). For TensorFlow>=2.0, there is, no longer, a separation between the installations and you simply install ```tensorflow``` which comes with GPU support if you have the appropriate hardware and CUDA and cuDNN installed.
<!-- TODO: Add more details -->