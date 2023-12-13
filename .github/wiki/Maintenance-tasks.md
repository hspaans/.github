Maintaining repositories is important to keep the relevant otherwise they must be archived. This way it allows to plan and rollout new features.

# Sprint 2024 Cleanup

## General

- [ ]  Bump to Terraform 1.7
- [ ]  Revert to `pip` instead of `pipenv` for Python projects
- [ ]  Implement GitHub Action `pip-audit` for Python projects:
```yaml
  pip-audit:
    name: Pip Audit
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Run pip-audit
        uses: pypa/gh-action-pip-audit@v1.0.8
        with:
          inputs: requirements.txt
```
- [ ]  Implement GitHub Action `dependency-review` for public projects:
```yaml
# Dependency Review Action
#
# This Action will scan dependency manifest files that change as part of a Pull Request, surfacing known-vulnerable versions of the packages declared or updated in the PR. Once installed, if the workflow run is marked as required, PRs introducing known-vulnerable packages will be blocked from merging.
#
# Source repository: https://github.com/actions/dependency-review-action
# Public documentation: https://docs.github.com/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-dependency-review#dependency-review-enforcement
# SPDX overview: https://spdx.org/licenses/
---
name: Dependency Review
on:
  pull_request:

permissions:
  contents: read
  pull-requests: write

jobs:
  dependency-review:
    name: Dependency Review
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Dependency Review
        uses: actions/dependency-review-action@v3
        with:
          allow-licenses: GPL-2.0-only, GPL-3.0-only, LGPL-2.1-only, LGPL-3.0-only, MIT, MPL-1.1, MPL-2.0, Apache-1.1, Apache-2.0
          comment-summary-in-pr: always
          fail-on-severity: critical
```

## Repository .github

- [ ]  Bump versions for Ansible Playbook CI
- [ ]  Drop `.github/workflows/typescript-node-lint.yml` [#101](https://github.com/hspaans/.github/issues/101)

## Ansible Role

- [ ]  Add Ubuntu 24.04 to roles
- [ ]  Add ``.gitattributes`` to repositories
- [ ]  Add ``.devcontainer/devcontainer.json`` to repositories
- [ ]  Remove the `schedule` trigger in ``.github/workflows/ci.yml``

## Molecule Container Images

- [ ]  Add Ubuntu 24.04

# Autumn 2023 Cleanup

## General

- [ ]  Bump to Terraform 1.6
- [ ]  Bump to Python 3.10
- [ ]  Bump to Debian 12 (bookworm)

## Repository .github

- [ ]  Bump versions for Ansible Playbook CI

## Ansible Role

- [ ]  Drop Debian 10 (buster)
- [ ]  Drop tmpfs from ``molecule/{debian,ubuntu}/molecule.yml``
- [ ]  All plays should be named. ansible-lint(name[play])
  - [ ]   ``tests/test.yml``
- [ ]  use FQCN for builtin module actions: ``apt``, ``yum``, ``package``
  - [ ]   ``molecule/resources/playbooks/prepare.yml``

## Molecule Container Images

None

# Open Items

- [ ]  ``ansible-lint`` should be installed for the Ansible Language Server to work correctly
- [ ]  integrate action [Dependency Review](https://github.com/marketplace/actions/dependency-review) into workflows
  - [ ]  Create file ``OWNER/REPOSITORY/dependency-review-config.yml@master``

# Roadmaps

* https://docs.ansible.com/ansible/devel/roadmap/ansible_roadmap_index.html
