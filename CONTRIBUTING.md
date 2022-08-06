# Contributing

About how to write [registry.yaml](registry.yaml), please see [Registry Configuration](https://aquaproj.github.io/docs/reference/registry-config).

## Requirements

- [aqua](https://aquaproj.github.io/docs/reference/install) >= [v1.14.0](https://github.com/aquaproj/aqua/releases/tag/v1.14.0)
- [GitHub Personal Access Token](README.md#github-access-token-is-required)

## Set up

Checkout the repository and install [aqua-registry CLI](https://github.com/aquaproj/registry-tool).

```console
$ git checkout https://github.com/<REPO_OWENR>/<REPO_NAME>
$ cd <REPO_NAME>
$ aqua i -l # Install aqua-registry CLI
```

## How to add packages

1. Scaffold configuration: `aqua-registry scaffold <package name>`
1. Fix generated files if the scaffold fails
1. Update registry.yaml: `aqua-registry gr`
1. Test: `aqua i` and run installed tools
1. Repeat the step 2 ~ 4 until packages are installed properly
1. Create a pull request: `aqua-registry create-pr-new-pkg <package name>...`

:warning: Don't run `scaffold` command against the same package at multiple times.

:warning: When you update `pkgs/**/registry.yaml`, you have to run `aqua-registry gr` to reflect the update to `registry.yaml` on the repository root directory.

## Style Guide

https://aquaproj.github.io/docs/reference/registry-style-guide

### Getting Started

Let's try to add [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep) to the registry.

```console
$ aqua-registry scaffold BurntSushi/ripgrep
+ aqua gr BurntSushi/ripgrep
 >> registry.yamlUpdate registry.yaml
Creating aqua-local.yaml
+ aqua g local,BurntSushi/ripgrep >> aqua-local.yaml
+ aqua g pkgs/BurntSushi/ripgrep/pkg.yaml >> BurntSushi/ripgrep
+ aqua i --test
INFO[0000] create a symbolic link                        aqua_version=1.18.0 env=darwin/arm64 link_file=/Users/shunsukesuzuki/.local/share/aquaproj-aqua/bin/ripgrep new=aqua-proxy program=aqua
ERRO[0000] install the package                           aqua_version=1.18.0 env=darwin/arm64 error="check file_src is correct: exe_path isn't found: stat /Users/shunsukesuzuki/.local/share/aquaproj-aqua/pkgs/github_release/github.com/BurntSushi/ripgrep/13.0.0/ripgrep-13.0.0-x86_64-apple-darwin.tar.gz/ripgrep: no such file or directory" file_name=ripgrep package_name=BurntSushi/ripgrep package_version=13.0.0 program=aqua registry=local
FATA[0000] aqua failed                                   aqua_version=1.18.0 env=darwin/arm64 error="it failed to install some packages" program=aqua
FATA[0001] aqua failed                                   aqua_version=0.1.0-1 env=darwin/arm64 error="execute a command: aqua i: exit status 1" program=aqua-registry
```

When the scaffold fails, please see the log.

```
check file_src is correct: exe_path isn't found: stat /Users/shunsukesuzuki/.local/share/aquaproj-aqua/pkgs/github_release/github.com/BurntSushi/ripgrep/13.0.0/ripgrep-13.0.0-x86_64-apple-darwin.tar.gz/ripgrep: no such file or directory
```

:bulb: [Troubleshooting: check file_src is correct](https://aquaproj.github.io/docs/trouble-shooting#check-file_src-is-correct)

Fix the configuration pkgs/BurntSushi/ripgrep/registry.yaml like [this](https://github.com/aquaproj/aqua-registry/blob/main/pkgs/BurntSushi/ripgrep/registry.yaml).

Then run `aqua-registry gr` and `aqua i`.

```console
$ aqua-registry gr
$ aqua i
```

Check the log and fix the following configuration files as needed.

- pkgs/BurntSushi/ripgrep/pkg.yaml
- pkgs/BurntSushi/ripgrep/registry.yaml
- aqua-test.yaml

Run `rg --help` for testing.

```console
$ rg --help
```

If it doesn't work, check the log and fix the above configuration files.

When it works well, please create a pull request.

```console
$ aqua-registry create-pr-new-pkg BurntSushi/ripgrep
```
