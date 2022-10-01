# .github

Github settings for this organization and its repositories following the [this guide].

## Reusable workflows

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
