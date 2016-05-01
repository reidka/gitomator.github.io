---
layout: doc-page
doc_source: 09-classroom-ci
permalink: /docs/classroom/ci

title: "`enable-ci` & `disable-ci`"
---

Enable/disable continuous integration on your hosted repos (e.g. Travis CI with
GitHub repos).

Usage:

```sh
 $ bin/task/enable-ci ASSIGNMENT-CONFIG
 $ bin/task/disable-ci ASSIGNMENT-CONFIG
```

 > _Tip:_ You can specify the `--sync` command-line flag, to get Gitomator to sync your
 > CI service with your hosting service, before enabling/disabling CI on the repos.          
 > When using Travis CI and GitHub, you should use the `--sync` flag when
 > enabling CI on newly created repos.

### Minimal configuration


```yaml
repos:
  - repo-001
  - repo-002
  - repo-003
  - repo-004
```
