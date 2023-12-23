# .github

Github settings for this organization and its repositories following the [this guide].

## Reusable workflows

### Close stale issues and PRs

Scan the repository every night for stale issues and pull-requests to mark and
close them.

```yaml
---
name: Close stale issues and pull-requests

on:
  schedule:
    - cron: '30 1 * * *'

jobs:
  stale:
    permissions:
      issues: write
      pull-requests: write
    name: GitHub Action Stale
    uses: hspaans/.github/.github/workflows/reusable-stale.yml@master
```

### Ansible Roles

```yaml
---
name: CI

on:
  pull_request:
  schedule:
    - cron: '22 22 10 * *'

jobs:
  ansible-role-ci:
    name: Ansible Role CI
    uses: hspaans/.github/.github/workflows/ansible-role-ci.yml@master
```

### Containers

```yaml
---
name: CI

on:
  pull_request:
  schedule:
    - cron: '22 22 10 * *'

jobs:
  container-ci:
    name: Container CI
    uses: hspaans/.github/.github/workflows/container-ci.yml@master
```

### Python

The Python workflow is used for all Python repositories. It has the following requirements:

* ``requirements.txt`` in the root of the repository is used for all Python dependencies
* Sphinx documentation in ``docs/`` (depending on ``requirements.txt`` and Python 3.10)
* Pytest tests in ``tests/`` (depending on ``requirements.txt`` and runs on Python >=3.8)
* Linting with flake8, yamllint (depending on ``requirements.txt`` and runs on default Python)

```yaml
---
name: CI

on:
  pull_request:
  schedule:
    - cron: '22 22 10 * *'

jobs:
  python-ci:
    name: Python CI
    uses: hspaans/.github/.github/workflows/python-ci.yml@master
```

[this guide]: https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file
