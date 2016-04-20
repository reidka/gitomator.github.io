---
layout: doc-page
doc_source: 01-welcome  # The name of this Markdown file (without the .md folder)
permalink: /docs/welcome/

title: "Welcome"
excerpt: "Welcome"
modified: 2016-04-20T10:43:02-04:00
---


Gitomator is a set of libraries and command-line tools, built to help software educators.

 * Automate your workflow around services like GitHub & Travis CI.
 * Use the existing automation tasks, or create your own.
 * Plug-in architecture allows you to use the same API to access different service providers.
 * Easy to extend with new services, providers and tasks.
 * Free, Open-Source (MIT license), contributor-friendly project. Please open issues and/or submit pull-requests on [GitHub](https://github.com/gitomator).


# What can I do with it?

In two words - Workflow automation.
For example, you can create the following [YAML](http://yaml.org/) file:

```yaml
source_repo: starter_code

repos:
  - repo1: Alice
  - repo2: Bob
  - repo3: { Charlie: read, TAs: write }
```

And, with a single command, run the following operations in your GitHub organization:

 * Create repos `repo1`, `repo2` and `repo3`.
 * Push changes to these repos (from an existing repo, `starter_code`).
 * User access - Grant `Alice`, `Bob` and `Charlie` read permission to `repo1`, `repo2` and `repo3`, respectively.
 * Team access - Grant `TAs` write permission to `repo3`,
 * Optionally, by specifying a command-line flag, enable Travis CI on all repos.

# What is it good for?

Running a software engineering course at a University, for example.          

In fact, the prototype of Gitomator was used to automate the workflow of coding
assignments in an advanced software engineering course at the University of Toronto.
