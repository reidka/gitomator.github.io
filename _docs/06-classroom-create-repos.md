---
layout: doc-page
doc_source: 06-classroom-create-repos
permalink: /docs/classroom/create-repos

title: "Create & update repositories"
---

Usage:

```sh
 $ bin/task/create-repos CONFIG
```

### Minimal configuration

Create a bunch of empty repos.

```yaml
repos:
  - repo-001
  - repo-002
  - repo-003
  - repo-004
```

### Specify `source_repo`

The `master` branch of the specified `source_repo` will be pushed to each repo that is created.

 > tip: You can run the `create-repos` task with the `--update-existing` flag
 > in order to push recent changes from the `source_repo` to existing repos
 > (assuming there are no Git conflicts).

```yaml
source_repo: repo-with-starter-code
repos:
  - repo-001
  - repo-002
  - repo-003
  - repo-004
```
