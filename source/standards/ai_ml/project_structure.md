## Machine Learning Project Structure

Machine learning projects should generally be structured as follows:

```
project-root/
  |- doc/
  |- data/
  |- src/
       |- <pipeline_modules>
  |- .gitignore
  |- environment.yaml
  |- params.yaml
  |- pyproject.toml
  |- README.md
  |- requirements.txt
```

A description of the files and directories is given below:

<table>
  <tr>
    <th>File / Directory</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>doc</td>
    <td>Typically Sphinx documentation but can be any</td>
  </tr>
</table>

<!--
TODO:
featurise.py
infer.py
evaluate.py [Can include speed evaluation]
export.py
models.py
prepare.py
train.py
-->

They may be cases where multiple projects will need to be grouped within a
parent directory.
