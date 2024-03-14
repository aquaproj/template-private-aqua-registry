# template-private-aqua-registry

Template Repository for Private aqua Registry

[Reference](https://aquaproj.github.io/docs/develop-registry/create-private-registry) | [Contributing](CONTRIBUTING.md)

## :warning: Archive this repository

[#465](https://github.com/aquaproj/template-private-aqua-registry/issues/465)

We archived this repository because we can't maintain this repository continuously.

## What's aqua?

aqua is a Declarative CLI Version Manager written in Go.

https://aquaproj.github.io/

## GitHub Access Token is required

Please set your GitHub Access Token as the environment variable `GITHUB_TOKEN` or `AQUA_GITHUB_TOKEN`.
GitHub Access Token is required to access private repositories.
The scope `repo` is required.

## How to use this repository

1. Use as Registry
1. Use as Global Configuration

### 1. Use as Registry

aqua.yaml

```yaml
---
# aqua - Declarative CLI Version Manager
# https://aquaproj.github.io/
registries:
  - name: custom # Rename freely
    type: github_content
    repo_owner: <REPO_OWNER>
    repo_name: <REPO_NAME>
    ref: v0.1.0 # renovate: depName=<REPO_OWNER>/<REPO_NAME>
    path: registry.yaml
packages:
```

### 2. Use as Global Configuration

About Global Configuration, please see the document.

- https://aquaproj.github.io/docs/tutorial/global-config
- https://aquaproj.github.io/docs/guides/team-config

Checkout this repository and set the environment variable `AQUA_GLOBAL_CONFIG`.

```console
$ git checkout https://github.com/<REPO_OWNER>/<REPO_NAME>
$ export AQUA_GLOBAL_CONFIG=$PWD/<REPO_NAME>/aqua-all.yaml:$AQUA_GLOBAL_CONFIG
```

## LICENSE

[MIT](LICENSE)
