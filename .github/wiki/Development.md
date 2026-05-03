## Using git

> [!NOTE]
> Use commands on own risk.

Rename tag

```shell
git tag v3 v2
git tag -d v2
git push origin --delete v2
```

Delete tag locally and remotely

```shell
git tag -d v2
git push origin --delete v2
```

## Using GitHub CLI

Creating a new repository based on a template repository.

```shell
gh repo create <repository name> -t hspaans/template
```

Creating a tag and release with GitHub CLI

```shell
gh release create "v2" \
   --title "Release v2" \
   --generate-notes
```
