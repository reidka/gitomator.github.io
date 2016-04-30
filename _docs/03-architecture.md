---
layout: doc-page
doc_source: 03-architecture
permalink: /docs/architecture/

title: "Architecture"
excerpt: "Under the hood of Gitomator"
---

Gitomator is made up of a number of libraries:

 * [`gitomator`](https://github.com/gitomator/gitomator) - Lightweight "foundations" library.
    * High-level service interfaces, with support for pluggable service-providers.
    * General-purpose automation tasks
 * [`gitomator-github`](https://github.com/gitomator/gitomator-github) - GitHub service-provider implementation(s).
 * [`gitomator-travis`](https://github.com/gitomator/gitomator-travis) - Travis CI service-provider implementation(s).

 * [`gitomator-classroom`](https://github.com/gitomator/gitomator-classroom) -
   Workflow automation for software educators.
    * Built on top of Gitoamtor
    * Uses `gitomator-github` and `gitomator-travis`, by default.
