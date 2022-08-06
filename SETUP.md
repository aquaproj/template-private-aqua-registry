# Set up

## Create a repository using the template repository

https://github.com/aquaproj/template-private-aqua-registry

Replace the following place holders.

- `<REGISTRY_NAME>`
- `<REPO_OWNER>`
- `<REPO_NAME>`

## CI

To test the registry in CI, GitHub Access Token is required to access private repositories.

We recommend to create GitHub App and install it to private repositories.
You can also use GitHub Personal Access Token instead of GitHub App.

## Renovate

You can test the tool update in CI using Renovate.
Please install Renovate in repositories.

### Automerge Renovate Pull Requests

If you would like to automerge Renovate Pull Requests, please enable automerge.

ref. [2022-03-29 Automate handling a number of Pull Requests by Renovate in Terraform Monorepo](https://devs.quipper.com/2022/03/29/automate-handling-a-number-of-pull-requests-by-renovate-in-terraform-monorepo.html)

- Enable Automerge
  - Add the job `status-check` to the default branch's branch protection rule's `Status checks that are required.`
- Enable platformAutomerge
