# github-actions playground

A workflow is a configurable automated process that will run one or more jobs. Workflows are defined by a YAML file checked in to your repository and will run when triggered by an event in your repository, or they can be triggered manually, or at a defined schedule. 

 

 

Github workflows are made up of at least one job. A job is a set of steps in a workflow that is executed on the same runner. Each step is either a shell script that will be executed, or an another action that will be run. Steps are executed in order and are dependent on each other. Since each step is executed on the same runner, you can share data from one step to another. For example, you can have a step that builds your application followed by a step that tests the application that was built. 

We can specify how a job is triggered. 

It could be run manually with or without inputs using workflow_dispatch 

It could run on specific events like a pr raised or branch merged and which branch it was merged to 

We could schedule it using cron 

 

Each job can be made up of multiple steps. We need to specify a runner for a job. Each job will run inside its own virtual machine runner, or inside a container, and has one or more steps that either run a script that you define or run an action, which is a reusable extension that can simplify your workflow. 

 
```
# Controls when the workflow will run 

on: 

  push: 

  workflow_dispatch: 

# A workflow run is made up of one or more jobs that can run sequentially or in parallel 

jobs: 

  # This workflow contains a single job called "build" 

  build: 

    # The type of runner that the job will run on 

    runs-on: ubuntu-latest 

 

 

Each step can run a command or invoke an action using the uses keyword 

 

 # Steps represent a sequence of tasks that will be executed as part of the job 

    steps: 

      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it 

      - uses: actions/checkout@v3 

      - name: Install 

        run: npm ci 

      # Runs a set of commands using the runners shell 

      - name: test 

        run: npm run test 

 ```

### Actions 

 

An action is a custom application for the GitHub Actions platform that performs a complex but frequently repeated task. Use an action to help reduce the amount of repetitive code that you write in your workflow files. An action can pull your git repository from GitHub, set up the correct toolchain for your build environment, or set up the authentication to your cloud provider. 

You can write your own actions, or you can find actions to use in your workflows in the GitHub Marketplace. 

 

 

### Runners 

 

runner is a server that runs your workflows when they're triggered. Each runner can run a single job at a time. GitHub provides Ubuntu Linux, Microsoft Windows, and macOS runners to run your workflows; each workflow run executes in a fresh, newly-provisioned virtual machine. GitHub also offers larger runners, which are available in larger configurations. 

 

 

### Conditional execution of steps 

 

What if I want to run a step on  
