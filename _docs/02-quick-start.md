---
layout: doc-page
doc_source: 02-quick-start
permalink: /docs/quick-start/

title: "Quick-Start"
excerpt: "Getting started with Gitomator"
modified: 2016-04-20T15:54:02-04:00
---

## Install Dependencies

Make sure your have:

* [Ruby](https://www.ruby-lang.org/en/downloads/) (Gitomator is developed and tested on version 2.2)
* [Ruby Gems](https://rubygems.org/pages/download)
* [Bundler](http://bundler.io/)


## Create `~/.gitomator`

Create the file, `~/.gitomator`, containing your credentials and
the name of your GitHub organization:

```yaml
hosting:
  provider: github
  username: YOUR-GITHUB-USERNAME
  password: YOUR-GITHUB-PASSWORD
  organization: YOUR-GITHUB-ORGANIZATION
```

 > If you're on Windows, you should create the `.gitomator` file in your home
   directory (which is probably `ROOT\Users\<YOUR-USERNAME>`).

## Setup

Open a terminal window, and clone the code:

```bash
$ git clone https://github.com/gitomator/gitomator-classroom.git
```

Install all Ruby dependencies

```bash
$ cd gitomator-classroom
$ bin/setup
```

OK, you're ready to go.

## Create some repositories

Create the file `repos.yml`:

```yaml
name: fake-assignment
source_repo: gitomator/gitomator-classroom
repos:
  - gitomator-test-repo-1
  - gitomator-test-repo-2
  - gitomator-test-repo-3
```

And run the following command:

```sh
$ bin/task/create_repos repos.yml
```

You will see informative log messages printed to the console.

When the script is done, go to the repositories page of your GitHub organization (at `https://github.com/YOUR-GITHUB-ORGANIZATION`).
You should see 3 new repositories.

Notice that the repos are not empty. Each repo contains all the commits from (the `master` branch of)
[`gitomator/gitomator-classroom`](https://github.com/gitomator/gitomator-classroom).

## Delete the repositories

Gitomator does not have a `delete-repos` task (we don't want anybody to
accidentally delete all of their students' repos). Instead, let's delete the test repositories using the interactive console. You can start the console with the command:

```sh
$ bin/console
```

The console is just a Ruby [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)
that uses your `~/.gitomator` to create a few convenience functions.

If you don't know Ruby, that's fine. Just type the following in the console:

```ruby
hosting.delete_repo "gitomator-test-repo-3"
```

Refresh the repositories page of your GitHub organization, and you will see that
`gitomator-test-repo-3` is no longer there.

 > Since the console is just a Ruby REPL, you can use Ruby to delete all 3 repos
in one command:
```ruby
(1..3).each {|i| hosting.delete_repo "gitomator-test-repo-#{i}" }
```

You can exit the console by typing `exit`.
