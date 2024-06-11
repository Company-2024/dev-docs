# Workflow Best Practices

## Creating a Model Architecture

- Always have a dummy input to run your model's `forward` method on otherwise
  you will struggle to figure out what's going on.
  ```
  # x shape: (batch_size, sequence_length, num_attributes, input_size)
  input_ = torch.rand((1, 5, 6, 1))
  model(input_)
  ```

## Project Workflow

- For notebooks, follow the naming convention: `##-<notebook_name>` where `##`
  is a number assigned to the notebook.
- Always aim to keep your notebooks in a state where you can simply 'Run All'
  and generate the plots required for presentations and reports.

### Re-implementing a Model

- When re-implementing a model, always try to change as little as possible.
  **Keep the datasets identical.**

## Git
