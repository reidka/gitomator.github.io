---
layout: doc-page
doc_source: 05-classroom-basics
permalink: /docs/classroom/basics

title: "Gitomator Classroom - The Basics"
excerpt: "The main concepts behind Gitomator"
---

`gitomator-classroom` is a set of simple command-line tools.        

## Tools

 * `bin/task`       
   General-purpose automation tasks. For example: Creating repos, updating team
   memberships and setting access permissions.         
   Use the `--help` to get more info about each command.
 * `bin/console`           
   Starts the IRB (Ruby interactive shell) with a few convenient variables and methods loaded.
 * `bin/workflow`         
   Full workflow automation. For example: Publishing an assignment.         
   These tools are meant to be purpose-specific, and will most likely involve
   a few automation tasks composed together somehow.


## YAML configuration files

Configuration and data are provided as [YAML](http://yaml.org/) text files.
YAML is "a human friendly data serialization standard". For our purposes, you
can think of it as a "nicer-looking JSON".

Why YAML?

 * Text files are a good "lowest common denominator".  
   * Easy to generate and/or edit.
   * Don't require any special software.
 * YAML is easy to read.

To see the various configuration files that Gitomator uses see
[this section of the docs](/docs/classroom/config-files).

## Getting Started With GitHub

 1. Create a [GitHub organization](https://help.github.com/articles/creating-a-new-organization-account/)
 2. [Request a discounted/free plan for educational use](https://education.github.com/discount_requests/new).       
   _Note:_ You can start using Gitomator before getting your discount, you just won't be able to create private repos.
 3. **Important:** In your organization's settings page, go to the **member privileges**
    section and set the **default repository permission** to None.     
    (Otherwise, every students will be able to see every repo in the organization).
 4. _Suggestion:_ Make one of your colleagues an organization owner.         
    (Extremely useful for cases where one of you cannot access their account or
     accidentally loses their owner privileges)
