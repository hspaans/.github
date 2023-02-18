# .github

Github settings for this organization and its repositories following the [this guide].

## Reusable workflows

### Close stale issues and PRs

Scan the repository every night for stale issues and pull-requests to mark and close them.

```yaml
---
name: Close stale issues and pull-requests

on:
  schedule:
    - cron: '30 1 * * *'

permissions:
  issues: write
  pull-requests: write

jobs:
  stale:
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
    uses: hspaans/.github/.github/workflows/python-ci.yml@master
```

[this guide]: https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file
