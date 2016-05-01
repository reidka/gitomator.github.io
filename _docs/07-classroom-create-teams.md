---
layout: doc-page
doc_source: 07-classroom-create-teams
permalink: /docs/classroom/teams

title: "`update-teams`"
---

Usage:

```sh
 $ bin/task/update-teams TEAMS-CONFIG
```

### Minimal configuration

Specify teams (by name) and their members (e.g. GitHub usernames).

```yaml
Students:
  - Alice
  - Bob
  - Charlie
  - Dave

Teaching-Assistants:
  - Zoe
  - Ron
```

### Specify Role

By default, team members have the `member` role, but you can specify a different
role. For example:

```yaml
Team1:
  - Alice
  - Bob
  - {Zoe: admin}

Team2:
  - Charlie
  - Dave
  - {Ron: admin}
```
