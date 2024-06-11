# Trouble Shooting

Here are some errors encountered by Peralex AI developers and how they went about fixing them.

#### Error Importing MLFlow

**Issue**

```
PydanticUserError: If you use `@root_validator` with pre=False (the default) you MUST specify `skip_on_failure=True`. Note that `@root_validator` is deprecated and should be replaced with `@model_validator`.
```

**Solution**
This is an issue that was specific to MLFlow version 2.6.0. Resolved by installing version 2.5. See [this Github issue](https://github.com/mlflow/mlflow/issues/9331).

Also uninstall pydantic?
