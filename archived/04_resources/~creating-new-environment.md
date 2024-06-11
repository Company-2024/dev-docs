# Creating New Environment from Scratch

Conda can be quite nefarious when it comes to installing packages. To create a
new environment from scratch follow the installation order given below:

1. `conda-build` (for Miniconda whereby it's not installed by default).
2. `pip`
3. `cudatoolkit`, `cudnn`:

```
conda install -c conda-forge cudatoolkit=11.7 cudnn=8.4
```

4. `torch`, `torchvision`, `torchaudio` (pip)
5. `PySoundFile` (pip)
6. `scikit-learn` (pip)
7. `matplotlib` (pip)
8. `pandas` (pip)
9. `scipy` (pip)
10. `lightning`
11. `jupyterlab` (pip)
12. `ipykernel` (Remove any old kernels and add new one)
13. `black` (conda)
