# PyTorch Style Guide

To convert a `torch.Tensor` object to a `numpy.ndarray`, use
`<tensor_var_name>.cpu().detach().numpy()`

<!--
- Add details from https://stackoverflow.com/questions/63582590/why-do-we-call-detach-before-calling-numpy-on-a-pytorch-tensor on use of detach.
-->

## Models

<!--
- self.model_type = "Transformer"
- Each model should be accompanied by: def gather_outputs(
        self,
        dataloader: torch.utils.data.DataLoader,
        device: torch.device | int,
        correctly_classified: bool = False,
    )
-->

## Datasets

Always structure your datasets such that the batch is always first in the shape
of a tensor containing multiple examples i.e. `batch_first = True`. This makes
things much easier during deployment.

## Training

<!--
- EarlyStopping: https://github.com/Lightning-AI/lightning/discussions/11787
-->

The naming convention for the directory in which the model checkpoints should be
saved is `models/model_ckpts/<mlflow_experiment_name>/<mlflow_run_name>`
