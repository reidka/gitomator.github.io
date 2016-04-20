---
layout: doc-page
doc_source: 01-overview  # The name of this Markdown file (without the .md folder)
permalink: /docs/overview/

title: "What is Gitoamtor?"
excerpt: "Overall architecture & goals of Gitomator"
modified: 2016-04-20T10:43:02-04:00
---


Gitomator is a set of libraries and command-line tools,
built to help software educators automate their workflow.

It is made up of a number of libraries:

 * [`gitomator`](https://github.com/gitomator/gitomator) - Lightweight "foundations" library.
    * High-level service interfaces, with support for pluggable service-providers.
    * General-purpose automation tasks
 * [`gitomator-github`](https://github.com/gitomator/gitomator-github) - GitHub service-provider(s).
 * [`gitomator-travis`](https://github.com/gitomator/gitomator-travis) - Travis CI service-provider(s).

 * [`gitomator-classroom`](https://github.com/gitomator/gitomator-classroom) -
   Workflow automation for software educators.
    * Built on top of Gitoamtor
    * Uses `gitomator-github` and `gitomator-travis`, by default.
