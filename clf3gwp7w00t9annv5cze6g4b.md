---
title: "GitHub Series | Actions - Workflow Dispatch"
datePublished: Sat Mar 11 2023 04:29:39 GMT+0000 (Coordinated Universal Time)
cuid: clf3gwp7w00t9annv5cze6g4b
slug: github-series-actions-workflow-dispatch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678012035114/ca049efd-2395-4d76-8303-b4476019062a.png
tags: github, devops, github-actions, ci-cd, workflow-dispatch

---

In our previous post, we looked at GitHub Actions please give that article a read before you go ahead with this one.

Workflow dispatch is a feature of GitHub Actions that allows you to trigger a specific workflow run on-demand, without the need for a code push or pull request. With workflow dispatch, you can create a custom event that can be triggered from the GitHub UI or through the GitHub API, allowing you to run a specific workflow in response to a particular event or action.

To use workflow dispatch, you must define a `workflow_dispatch` event in your workflow file, along with any required inputs or parameters. You can then trigger the workflow run from the Actions tab in your GitHub repository, or by sending a POST request to the GitHub API with the appropriate parameters.

Workflow dispatch can be useful in a variety of scenarios, such as running a deployment workflow on-demand, triggering a test suite for a specific branch or pull request, or kicking off a manual code review process. By allowing you to trigger workflows without the need for a code push or pull request, workflow dispatch can help streamline your development process and make it easier to manage your GitHub Actions.

Here's an example of how you could use workflow dispatch to trigger a deployment workflow on-demand:

* Define a `workflow_dispatch` event in your workflow file:
    

```yaml
name: Deploy to production
on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'The environment to deploy to (e.g. production, staging)'
        required: true
```

In this example, the workflow will only be triggered when a `workflow_dispatch` event is received, and it requires an `environment` input to be specified.

* Define the steps to be performed in your deployment workflow:
    

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Deploy to environment
        run: |
          # Perform deployment steps here, based on the specified environment input
```

In this example, the workflow consists of a single job called `deploy`, which runs on the `ubuntu-latest` operating system. The first step checks out the code, and the second step performs the actual deployment based on the specified `environment` input.

* Trigger the workflow run through the GitHub UI or API:
    

To trigger the deployment workflow, you would navigate to the Actions tab in your GitHub repository, select the `Deploy to production` workflow, and enter the required `environment` input. Alternatively, you could use the GitHub API to trigger the workflow to run programmatically.

Once triggered, the workflow would run through the defined steps and perform the deployment based on the specified `environment` input.

#### Example source code -

%[https://github.com/nikhilakki/nikhilakki.in-blog-code-examples/blob/main/.github/workflows/workflow-dispatch.yml] 

#### Screenshots -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678010987281/6a9c2ed9-399e-4aa4-a99d-95e75e637699.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1678010950315/1884fa99-1332-4661-8ac7-0e3afc4c4a00.png align="center")

### References -

%[https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow]