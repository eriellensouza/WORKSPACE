# Exercise 3: Workflow jobs

## Problem

Building on the knowledge from lesson 1 and the previous exercise, you will now create a more complex workflow with multiple jobs.

We discussed the simple workflow definition in the lesson. Using that definition as the basis for this exercise, create a new workflow file named `lesson1_exercise3.yaml` in the `.github/workflows` directory of your repository. Ammend the workflow definition to include the following:

- Change the workflow name to: `Lesson 1 - Exercise 3`
- Change the run name to: `Run of the complex workflow`
- Add a new job named `test` that runs on the `ubuntu-latest` runner
  - Add **3 steps** for this job:
    - Step 1: Checkout the repository using `actions/checkout@v4`
    - Step 2: Using the [GitHub Actions marketplace](https://github.com/marketplace?type=actions), find an action that will install and configure NodeJS version 18.* and add it as a step in the `test` job
    - Step 3: Run the following node command as the final step in the `test` job: `node -e "console.log('running from node!')"`

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

- The workflow run should succeed with both jobs (`build` and `test`) completing successfully
- Step 3 of the `test` job should output `running from node!` to the logs
