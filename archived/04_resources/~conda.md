# Conda

## Installation Order

Conda can be nefarious when it comes to installing stuff and conflicts. When
setting up an environment from scratch, try the following order:

1. `conda-build`
2. `pip`
3. `cudatoolkit`, `cudnn`
4. `torch`, `torchvision`, `torchaudio`
5. `matplotlib`
