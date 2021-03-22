# Contributing

## Contents of this file

### For contributors
- [Running locally](#running-locally)
- [Conventions to follow](#conventions-to-follow)
- [Testing and linting](#testing-and-linting)
- [Updating Changelog](#updating-changelog)

### For maintainers
- [Releasing a new version](#releasing-a-new-version)

## Running locally

Locally source module into another Terraform code base and plan/apply as normal.

## Conventions to follow

Follow [Terraform Style Conventions](https://www.terraform.io/docs/language/syntax/style.html) and [Terraform Standard Module Structure](https://www.terraform.io/docs/language/modules/develop/structure.html).

## Testing and linting

Code is linted using `terraform fmt`.

## Updating Changelog


If you open a GitHub pull request on this repo, please update `CHANGELOG` to reflect your contribution.

Add your entry under `Unreleased` as `Breaking changes`, `New features`, `Fixes`.

Internal changes to the project that are not part of the public API do not need changelog entries, for example fixing the CI build server.

These sections follow [semantic versioning](https://semver.org/), where:

- `Breaking changes` corresponds to a `major` (1.X.X) change.
- `New features` corresponds to a `minor` (X.1.X) change.
- `Fixes` corresponds to a `patch` (X.X.1) change.

See the [`CHANGELOG_TEMPLATE.md`](/docs/contributing/CHANGELOG_TEMPLATE.md) for an example for how this looks.


## Releasing a new version

Each merge to `main` branch will create a GitHub release using semver 1.2.3 syntax. Each GitHub release will also be presented as a version on Terraform Registry.
