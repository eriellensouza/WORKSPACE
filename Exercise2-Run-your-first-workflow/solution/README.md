# Exercise 2: Run your first workflow

## Problem

In lesson 1 you learned about the different components of GitHub Actions and the workflow files and their definitions. In this exercise, you will use the workflow we discussed in the lesson to run your first workflow.

Using the following workflow definition, create a new workflow file named `lesson1_exercise2.yaml` in the `.github/workflows` directory of your repository.

```yaml
name: Simple Workflow

run-name: Run of the simple workflow

on:
  # Workflow run trigger events
  push:
    branches: ["main"]
  pull_request:
    branches: ["main"]
  # Manually trigger workflow run
  workflow_dispatch:

jobs:
  # First job
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      # By default, the runner will use Bash on Linux/MacOS runners
      # Bash is supported on all runner types
      - name: Run a one-line script
        run: echo Hello, world!

      - name: Run a multi-line script
        run: |
          echo Add other actions to build,
          echo test, and deploy your project.
```

## Exepcted Output

- The workflow run should succeed with the job `build` completing successfully
- Step 2 of the `build` job should output `Hello, world!` to the logs
- Step 3 of the `build` job should output the following to the logs:
  
  ```bash
  Add other actions to build,
  test, and deploy your project.
  ```
