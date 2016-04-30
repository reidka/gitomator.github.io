---
layout: doc-page
doc_source: 08-classroom-access-permissions
permalink: /docs/classroom/access-permissions

title: "Set access permissions"
modified: 2016-04-20T15:54:02-04:00
---

Set who (user or team) has what permissions (e.g. read or write) to which repo.

Usage:

```sh
 $ bin/task/update-access-permissions CONFIG
```

### Minimal configuration

Specify who (e.g. GitHub usernames) gets access (read-only, by default) to
which repo.

```yaml
repos:
  - repo-001: Alice
  - repo-002: Bob
  - repo-003: Charlie
  - repo-004: Dave
  # ...
```

### Multiple users per repo

You can also specify multiple users per repo (e.g. group assignments):

```yaml
repos:
  - repo-001: [Alice, Bob]
  - repo-002: [Charlie, Dave, Eva]
  - repo-003: [Frank, George]
```

And mix the two formats:

```yaml
repos:
  - repo-001: [Alice, Bob]
  - repo-002: Charlie
  - repo-003: [Dave, Eva]
```

### Permission type

Specify permissions other than default one (read-only):

```yaml
repos:
  - repo-001: Alice
  - repo-002: { Bob: write }
  - repo-003: { Charlie: admin }
  - repo-004: Dave
```

As you might expect, you can specify multiple users per repo:

```yaml
repos:
  - repo-001: { Alice: read , Bob: write }
  - repo-002: { Charlie: admin, Dave: write }
```

Which can also be specified as:

```yaml
repos:
  - repo-001:
     - Alice: read
     - Bob: write
  - repo-002:
     - Charlie: admin
     - Dave: write
```


### Default access permission

You can specify the `default_access_permission` in the config file:

```yaml
default_access_permission: write
repos:
  - repo-001: Alice
  - repo-002: Bob
  - repo-003: Charlie
  - repo-004: Dave
  # ...
```

### Team Permissions

The names in the configuration file can refer to user and/or teams.

When using the `update-access-permissions`, you can specify the `--permission-type`
option, which can be one of the following three options:

 * `user` - The default, treat names as user names.
 * `team` - Treat names as team names.
 * `mixed` - The script will first check if a team with the given name exists. If no such team exists, treat the name as a username.
