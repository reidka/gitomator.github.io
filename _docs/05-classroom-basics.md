---
layout: doc-page
doc_source: 05-classroom-basics
permalink: /docs/classroom/basics

title: "Gitomator Classroom - The Basics"
excerpt: "The main concepts behind Gitomator"
modified: 2016-04-20T15:54:02-04:00
---

`gitomator-classroom` is a set of simple command-line tools.        

## YAML configuration files

Configuration and data are provided as [YAML](http://yaml.org/) text files.

YAML is "a human friendly data serialization standard". In other words,
it's nicer-looking JSON. The point is, your don't really need to learn YAML,
it's designed to be easy-to-read by human.

## Pluggable services

Gitomator defines high-level API's for accessing various services. For example:

 * `hosting` service, for hosting Git repositories (e.g GitHub, BitBucket, GitLab, your plain old file server)
 * `ci` service, for managing Continuous Integration builds (e.g. Travis CI, Shippable, Drone.io)


Service providers are defined in a configuration file.

The following file configures Gitomator to use GitHub and Travis CI, with credentials loaded from environment variables.

```yaml
hosting:
  provider: github
  access_token: <%= ENV['GITHUB_ACCESS_TOKEN'] %>
  organization: <%= ENV['GITHUB_ORG'] %>

ci:
  provider: travis
  github_access_token: <%= ENV['GITHUB_ACCESS_TOKEN'] %>
  github_organization: <%= ENV['GITHUB_ORG'] %>
```

 > _Note:_ The `<%= %>` syntax are [ERB](http://www.stuartellis.eu/articles/erb/) (embedded Ruby) tags.

## Data as declarative configuration

Consider the following YAML file, that can be used with the `create-repos` command-line tool:

```yaml
repos:
 - repo1
 - repo2
 - repo3
```

As a human, you can interpret this file in two different ways:

 1. Procedural (e.g _Create the repositories `repo1`, `repo2` and `repo3`_), where you interpret the file as a sequence of instructions.
 2. Declarative (e.g. _Make sure that the repos `repo1`, `repo2` and `repo3` exist_), where you interpret the file as "a state of the world".

The difference may seem subtle,
but thinking declaratively simplifies our reasoning about automation tasks, as they become more complex.
For example:


```yaml
source_repo: starter-code
repos:
 - repo1: Alice
 - repo2: Bob
 - repo3: Charlie
```

By thinking of the YAML above as a "state of the world":

 1. Repos (`repo1`, `repo2` and `repo3`)
 2. Their content (commits from the `starter-code` repo)
 3. Which user has access to which repo

We abstract away procedural details, such as:

 * Check if a repo exists, before trying to create it.
 * If a repo exists, check if there are new commits from `starter-code` that should be pushed to that repo.
 * Check existing access permissions, they might need to be removed or updated.
