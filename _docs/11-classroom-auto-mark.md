---
layout: doc-page
doc_source: 11-classroom-auto-mark
permalink: /docs/classroom/auto-mark

title: "`auto-mark`"
---

Usage:

```sh
 $ bin/task/auto-mark AUTO-MARK-CONFIG
```

Run a Docker-based auto-marker on each of repo in the config file.

  * Secure - run auto markers inside an isolated environment.
  * Flexible - Use an environment (i.e. Docker image) of your choice.
  * Simple
     * The auto-marker is a shell script
     * Config file specifies all the resources (i.e files/folders) that the
       script needs, and a place for it to store the results.
 * Re-usable & Easy to share - Docker images can be stored publicly using services such as Docker Hub.


 > **Important:** You will need to run this command in an environment
 > (i.e. terminal window) where you can run `docker` commands.


 > ### What is Docker ?!?
 >
 > If you don't know what Docker containers are, here's the short version -
 > Containers are light-weight virtual machines, and Docker is becoming the
 > industry-standard container technology.
 > For the long version, check out [Docker's website](https://www.docker.com/).

## Example

Consider the following auto-marker configuration file:

```yaml
name: warm-up-assignment

#----------------------- auto-marker properties --------------------------------

# A docker image to use for auto-marking
docker_image: alpine

# The auto-marker's script
automarker_script: /tmp/workspace/run.sh

# Other resources needed by the auto-marker
# (mounted as read-only volumes on the Docker container)
resources:
  solution:   /tmp/gitomator/local_clones/$REPO$
  automarker: /tmp/gitomator/local_clones/automarker-repo

# A local directory to store the auto-marker results
# (mounted as read/write volume on the Docker container)
results_dir: /tmp/workspace/auto-marker-results

#-------------------------------------------------------------------------------

repos:
 - repo-001
 - repo-002
 - repo-003
 - repo-004
```

As you can see, an auto-marker configuration file contains the following information:

 * The script that needs to run,
 * The environment (i.e. Docker image) it needs to run in,
 * The resources that it depends on,
 * And the place where it should store results.

The `/root` folder on the container will look like this:

```sh
  /root
     run.sh
     results/
     resources/
       automarker/
       solution/
```

The following table describes the files/folder that will be mounted, according
to the configuration file above:

| Path on the container | Path on the host machine |
| --------------------- | ------------------------ |
| `/root/run.sh`        | `/tmp/workspace/run.sh`  |
| `/root/results`       | `/tmp/workspace/auto-marker-results` |
| `/root/resources/automarker` | `/tmp/gitomator/local_clones/automarker-repo` |
| `/root/resources/solution` | `/tmp/gitomator/local_clones/repo-00X` (where `X` is either 1, 2, 3 or 4)|
