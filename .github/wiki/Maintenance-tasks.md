# Maintenance Tasks

Maintaining repositories is important to keep the relevant otherwise they must
be archived. This way it allows to plan and rollout new features.

## EoY 2024

### General actions

- [ ]  Start pinning shared worflows
- [ ]  Group Dependabot and ecosystems

```yaml
---
version: 2
updates:
  - package-ecosystem: devcontainer
    directory: /
    schedule:
      interval: weekly
    groups:
      devcontainer:
        patterns:
          - "*"

  - package-ecosystem: github-actions
    directory: /
    schedule:
      interval: weekly
    groups:
      github-actions:
        patterns:
          - "*"
```

- [ ]  Bump to Terraform 1.9
- [ ]  Revert to `pip` instead of `pipenv` for Python projects
- [ ]  Drop GitHub Action `pip-audit` for Python projects as Dependabot can scan the SBOM
- [ ]  Implement GitHub Action `dependency-review` for public projects:

```yaml
# Dependency Review Action
#
# This Action will scan dependency manifest files that change as part of a Pull
# Request, surfacing known-vulnerable versions of the packages declared or
# updated in the PR. Once installed, if the workflow run is marked as required,
# PRs introducing known-vulnerable packages will be blocked from merging.
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

### Repository .github

- [ ]  Bump Ansible versions for Ansible Playbook CI
- [ ]  Create a date based

### Ansible Roles

- [ ]  Add Ubuntu 24.04 to roles
- [ ]  Add ``.gitattributes`` to repositories
- [ ]  Add ``.devcontainer/devcontainer.json`` to repositories
- [ ]  Remove the `schedule` trigger in ``.github/workflows/ci.yml``

## SoC 2025

TBD

## Open Items

- [ ]  ``ansible-lint`` should be installed for the Ansible Language Server
       to work correctly
- [ ]  integrate action [Dependency Review](https://github.com/marketplace/actions/dependency-review)
       into workflows
  - [ ]  Create file ``OWNER/REPOSITORY/dependency-review-config.yml@master``

## Roadmaps

### Merge Ansible Roles into an Ansible Collection

Most Ansible Roles can be better merged in a generic Ansible Collection.

- [Ansible documentation](https://docs.ansible.com/ansible/devel/roadmap/ansible_roadmap_index.html)
