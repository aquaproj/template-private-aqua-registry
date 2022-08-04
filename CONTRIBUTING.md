# Contributing

About how to write [registry.yaml](registry.yaml), please see [Registry Configuration](https://aquaproj.github.io/docs/reference/registry-config).

## Requirements

- [aqua](https://aquaproj.github.io/docs/reference/install)
- [GitHub Personal Access Token](README.md)
- (Optional) [GitHub CLI](https://cli.github.com/)

GitHub CLI is required to create pull requests by `aqua-registry create-pr-new-pkg` command.
`aqua-registry create-pr-new-pkg` is useful but you can also create pull requests without this.
So GitHub CLI is optional.

## Set up

Checkout the repository and install [aqua-registry CLI](https://github.com/aquaproj/registry-tool).

```console
$ git checkout https://github.com/<REPO_OWENR>/<REPO_NAME>
$ cd <REPO_NAME>
$ aqua i -l # Install aqua-registry CLI
```

## How to add packages

1. Scaffold configuration: `aqua-registry scaffold <package name>`
1. Test and fix generated files
1. Update registry.yaml: `aqua-registry gr`
1. Create a pull request: `aqua-registry create-pr-new-pkg <package name>...`

:warning: When you update `pkgs/**/registry.yaml`, you have to run `aqua-registry gr` to reflect the update to `registry.yaml` on the repository root directory.

## Style Guide

https://aquaproj.github.io/docs/reference/registry-style-guide

### Example: Add BurntSushi/ripgrep

In this example, we describe how to add [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep) to the registry.

```console
$ aqua-registry scaffold BurntSushi/ripgrep
```

Check the log and fix the following configuration files as needed.

* pkgs/BurntSushi/ripgrep/pkg.yaml
* pkgs/BurntSushi/ripgrep/registry.yaml
* aqua-test.yaml

Run `rg --help` for testing.

```console
$ rg --help
```

If it doesn't work, check the log and fix the above configuration files.

When it works well, please create a pull request.

```console
$ aqua-registry create-pr-new-pkg BurntSushi/ripgrep
```
