# Experiment Tracking with MLflow

MLFlow is an open-source platform for managing the end-to-end machine learning
lifecycle.

<!-- Unfortunately, there is no way, at the moment, to have a parent directory for experiments. See the following:
1. https://github.com/mlflow/mlflow/issues/1464
2. https://github.com/mlflow/mlflow/issues/4595 -->

Export URI. set_tracking_uri is finicky for MLProjects:
https://github.com/mlflow/mlflow/issues/608#:~:text=How%20are%20ya%27ll,the%20abovementioned%20errors.

```bash
set MLFLOW_TRACKING_URI=file:///D:/Shared/Repositories/MachineLearning/dra_emitter_classification/logs/mlruns/experiments/
```

Python API doesn't play too nicely with mlflow run Export URI. set_tracking_uri
is finicky for MLProjects:
https://github.com/mlflow/mlflow/issues/608#:~:text=How%20are%20ya%27ll,the%20abovementioned%20errors.

You need to provide the same experiment name to the mlflow CLI:

mlflow run . -P experiment_name=testproject --experiment-name testproject For
more details: https://www.mlflow.org/docs/latest/cli.html#mlflow-run
https://stackoverflow.com/questions/59006453/mlflow-active-run-id-does-not-match-environment-run-id

## Overview

The basic usage of MLflow in Peralex AI projects is as follows:

1. Install MLflow to your Conda environment, if not already installed, using:

   ```bash
   pip install mlflow
   ```

   If you are going to want to run the MLflow server on your own PC and would
   like to create an executable to launch the server, also install MLflow
   globally using

   ```batch
   # Windows
   python3.x -m pip install mlflow
   ```

   You will need to add the Scripts directory for the Python to which you
   installed MLflow to PATH otherwise you will get an error that `mlflow` is not
   a recognised command.

   See [creating executable to launch MLflow server](#).

2. Add MLflow tracking to your code. It is important that you pay attention to
   naming conventions and various elements related to tracking as outlined in
   the section on [adding MLflow tracking to code](#).

3. View your experiments on the MLflow UI.

4. Create an [MLflow project](#) for the pipeline.

## Adding MLflow Tracking to Code

### Naming Conventions

Before we discuss the tracking code, it is important to look at some parameters
what will be used and what conventions are used for some of them.

1. `experiment_name`: Experiments are the primary unit of organisation in
   MLflow; all runs belong to an experiment. Each experiment lets you visualize,
   search, and compare runs, as well as download run artifacts or metadata for
   analysis in other tools. Unfortunately, MLflow does not, at the moment,
   support organisation of experiments into some type of project directory. As
   such the naming convention that must be followed for experiment names is:

   ```
   <project_name>_<pipeline_stage>_<experiment_number>_<descriptive_experiment_name>
   ```

    <!-- Automation of generation of experiment name. -->

2. `run_name`: An experiment can have several runs which you can then compare.
   There is no specific naming convention required for runs as these are
   organised very well in the UI.

<!-- 3. uri -->

### Tracking Code

### Automations

For many popular machine learning libraries, you make a single function call:
`mlflow.autolog()` which will automatically logs parameters, metrics, and
artifacts of your run.
[Read further](https://mlflow.org/docs/latest/tracking.html#automatic-logging).

For libraries which do not support `autolog`, you may use key-value pairs to
track

<!-- prettier-ignore -->
| Name       | Used for                                                 | Function call |
|------------|----------------------------------------------------------|---------------|
| Parameters | Constant values (for instance, configuration parameters) | `mlflow.log_param`, `mlflow.log_params` |
| Metrics    | Values updated during the run (for instance, accuracy)   | `mlflow.log_metric` |
| Artifact   | Files produced by the run (for instance, model weights)  | `mlflow.log_artifacts`, `mlflow.log_image`, `mlflow.log_text` |

The following code snippet illustrates the standard usage of MLflow for Peralex
AI projects. The rest of this page discusses components of this code snippet and
other further details. If you copy the code into your project, remember to
remove any unnecessary comments.

```
import dvc.api
import lightning.pytorch as pl
import mlflow
experiment_name = "my_experiment"
run_name = "my_experiment_run"
mlflow_uri = r"\\iserver.ct\UserDev\ai\mlflow\dra_emitter_classification\mlruns"

mlflow.set_tracking_uri(mlflow_uri)
mlflow.set_experiment(experiment_name)

# Enable autologging functionality
mlflow.pytorch.autolog(
    log_models=True   # Save generated models
)

# Use return value of start_run as context manager in with block
# otherwise you will have to call end_run at the end
with mlflow.start_run(run_name=run_name) as run:
    mlf_logger = MLFlowLogger(
        experiment_name=mlflow.get_experiment(run.info.experiment_id).name,
        tracking_uri=mlflow.get_tracking_uri(),
        run_id=run.info.run_id,
    )

    # Lightning trainer
    trainer = pl.Trainer(
        ...
        logger=mlf_logger,
    )

    # Train the model
    start_time = time.time()
    trainer.fit(...)
    runtime = (time.time() - start_time) / 60

    print(f"Training took {runtime:.2f} min in total.")
    print("Run ID: {}".format(run.info.run_id))
```

After this, launch the MLflow UI, from your prompt, using:

```
mlflow ui --backend-store-uri <the_uri>
```

See
[`mlflow.pytorch`](https://mlflow.org/docs/latest/python_api/mlflow.pytorch.html#module-mlflow.pytorch)
for other details.

You might want to override the autologging functionality for certain metrics in
the PyTorch/Lightning model e.g.:

```
def on_train_epoch_end():
    ...
    # Log training metrics over all batches using MLFlow
    self.logger.log_metrics(
        metrics,
        step=self.current_epoch,
    )
```

This allows you to use the epochs as the `step`.

Also, after directly calling `self.logger`, if you would like to push the
metrics to the progress bar as well, use `log` with `logger=False` i.e.:

```
def on_train_epoch_end():
    ...
    # Show metrics on progress bar
        self.log_dict(
            metrics,
            on_step=False,
            on_epoch=True,
            prog_bar=True,
            logger=False,
        )
```

You can also set the `MLFLOW_TRACKING_URI` environment variable. However, this
is less preferrable than doing this in code as it might cause mix-ups for
different projects.

### Logging (Saving) and Loading the Model

To log/save the model, you can either set `log_models=True` as an argument to
`autolog` or you can use use `mflow.pytorch.log_model` as follows:

```
mlflow.pytorch.log_model(model, "model")
```

### Linking MLflow with DVC

```
import dvc.api
```

class DVCDatasetSource(mlflow.data.dataset_source.DatasetSource): def
**init**(self, url, path, rev=None): super().**init**()

        self.url = url
        self.path = path
        self.rev = rev

    def _to_dict(self):
        dict = {"url": url, "path": path, "rev": rev}

        return dict

# Automate extraction of information about dataset to avoid errors

repo = git.Repo() dvc_dataset = { "url": [remote.url for remote in
repo.remotes][0], "path": "data/prepared", "rev": repo.head.object.hexsha, }

## Viewing Experiments on MLflow UI

### Creating Script or Executable to Launch MLflow UI

#### Windows

You may use a PowerShell or batch (or even bash, if you have the supporting
software required) script to launch the MLflow UI.

##### Powershell

1. Create a powershell script (.ps1 file) to launch the MLflow UI as follows:

   ```
   mlflow ui --backend-store-uri <backend_store_uri>
   ```

   Remember to replace the backend store URI with the correct one.

2. Open PowerShell as Administrator and run:

   ```
   Install-Module ps2exe
   ```

3. Then run:

   ```
   Invoke-PS2EXE <path_to_your_ps1_file> <path_to_your_exe_file>
   ```

4. You many also want to change the icon of the .exe file.

## Notes

<!-- - (`mlflow server` vs `mlflow ui`)[https://github.com/mlflow/mlflow/issues/1341] -->

MLProjects If you run with conda environment, it will download the environment.
Run using local.
