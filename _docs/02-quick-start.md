---
layout: doc-page
doc_source: 02-quick-start
permalink: /docs/quick-start/

title: "Quick-Start"
excerpt: "Getting started with Gitomator"
---

## Install Dependencies

Make sure your have:

* [Ruby](https://www.ruby-lang.org/en/downloads/) (Gitomator is developed and tested on version 2.2)
* [Ruby Gems](https://rubygems.org/pages/download)
* [Bundler](http://bundler.io/)


## Create `~/.gitomator`

Create the file `.gitomator` in your home directory.      
This file contains your credentials and the name of your GitHub organization:

```yaml
hosting:
  provider: github
  username: YOUR-GITHUB-USERNAME
  password: YOUR-GITHUB-PASSWORD
  organization: YOUR-GITHUB-ORGANIZATION
```

 > On Windows, your home directory is probably `ROOT\Users\<YOUR-USERNAME>`.

 > _Tip:_ You can configure Gitomator to use your [access token](https://github.com/blog/1509-personal-api-tokens)
   instead of username and password. In either case, you should keep the token/password
   private.

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

 > *Note:* If you're on OSX El-Captiran and having trouble installing Nokogiri (one of the dependecies), please [read this issue](https://github.com/gitomator/gitomator-classroom/issues/6).

## Create some repositories

Create the file `repos.yml`:

```yaml
repos:
  - gitomator-test-repo-1
  - gitomator-test-repo-2
  - gitomator-test-repo-3
```

And run the following command:

```sh
$ bin/task/make-repos repos.yml
```

The script will print informative log messages to the console.
When it's done, go to your GitHub organization page.
You should see 3 new repositories.

## Specify `source_repo`

Notice that the repositories that we created are empty.
In many cases, you want to create new repositories with some initial code (e.g.
code provided to students as the starting point of an assignment).

You can do that by specifying a `source_repo`, in the config file.        
For example, change `repos.yml` to

```yaml
source_repo: gitomator/gitomator-classroom
repos:
  - gitomator-test-repo-1
  - gitomator-test-repo-2
  - gitomator-test-repo-3
```

And run the command

```sh
$ bin/task/make-repos -u repos.yml
```

The `-u` option tells Gitomator to update (i.e. push commits from the source
repo) repos that already exist. That is, the `make-repos` command can be used to
create as well as update repositories.

 > Run `bin/task/make-repos --help` for more info command-line options.


## Specify `repo_properties`

By default, repositories are created public.
If you want the repositories to be private, you can specify it in the config file:

```yaml
source_repo: gitomator/gitomator-classroom

repo_properties:
  private: true

repos:
  - gitomator-test-repo-4
  - gitomator-test-repo-5
  - gitomator-test-repo-6
```

To see all supported `repo_properties`, see the [example config files](/docs/classroom/config-files).

 > _Note:_ In order to create private repos, your GitHub organization must have
 private repositories enabled (i.e. you're on one of the paid plans, or you were
 approved for an educational discount).

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
