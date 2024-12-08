[![Release](https://github.com/hajle-silesia/.github/actions/workflows/release.yaml/badge.svg)](https://github.com/hajle-silesia/.github/actions/workflows/release.yaml)

## About

Repository for organization shared workflows and configurations.

## Repository

### Structure

General overview of the repository structure. Not all files/directories are listed, only these that are specific to the tools in the repository.

```shell
.
├── .github                     # GitHub config files
│   ├── workflows               # GitHub Actions config files
│   ├── renovate.json           # Renovate shared config
│   └── renovate-blueprint.json # Renovate blueprint config
├── .pre-commit-config.yaml     # Pre-commit config file
├── README.md
```

## Architecture

Shared workflows and configurations are used to provide consistency across all repositories in the organization. In terms of extendability, there are two main types of shared resources:
- strict - used to enforce consistency, e.g. version management and package publishing
- flexible - used to provide baseline with the extension ability, e.g. dependency updates

### Dependency updates

[Renovate](https://docs.renovatebot.com/) is used as a tool for automated dependency updates. Although it handles many dependencies out of the box, there are many that are not supported yet. These have to be taken care of separately via [shared config file](.github/renovate.json). Verify periodically all dependencies against Renovate latest documentation/config file, to see if dependency support is added/separate handling is still needed. See [Renovate console](https://developer.mend.io/github/hajle-silesia) for scanning details.
Repositories in the organization should copy [config blueprint](.github/renovate-blueprint.json) into their own `.github/renovate.json` file to use shared configuration.

### Version management and package publishing

[semantic-release](https://semantic-release.gitbook.io/semantic-release/) is used as a tool for automated version management and package publishing. See configuration [here](.github/workflows/shared-release.yaml).
Repositories in the organization should copy [release workflow](.github/workflows/release.yaml) into their own `.github/workflows/release.yaml` file to use shared configuration.
