# .github


## Reusable workflows

### Containers

Release a Container Image

```yaml
---
name: Container Release

on:
  push:
    # Publish `master` as Docker `latest` image.
    branches:
      - master
      - v*

    # Publish `v1.2.3` tags as releases.
    tags:
      - v*

jobs:
  container-release:
    uses: hspaans/.github/.github/workflows/container-release.yml@v0.1.2
    with:
      actor: ${{ github.actor }}
      platforms: linux/amd64,linux/arm64
    secrets:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
