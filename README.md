# dev-env-template

Template development environment to be used when creating new projects.

## Required Tools

* bash
* Docker

## Usage

### Creating a New Project From Template

Running `./create-dev-env [project]` creates a new project from template under `./out/[project]-dev-env`.
The project can then be copied out of `./out/` to another location and used for the new project.

### Clean-up

Running `./delete-out` deletes the `./out/` directory.

## Scripts

### `./bin/dev-env/runner`

Script containing the `run` command which can be sourced into other scripts and used to execute
the script in either an already running development environment container or in a new ephemeral
instance. Executing the scripts within the container will simply run the command locally.

`run` works by determining the calling script name, and calls it within a docker environment
(either via `exec` or `run` - unless it's already in the docker environment in which case it won't
do anything extra). It will then return the exit code of the docker execution to exit the script
entirly to avoid recalling it on the host.

Note that you can pass script arguments to the `run` command via `run $@`.

Example usage in a script:

```bash
!#/usr/bin/env bash
source `dirname $BASH_SOURCE`/dev-env/runner && run $@

# ...the rest of the script
```

### `./bin/dev-env/start`

Starts the development environment and leaves it running in the background.

### `./bin/dev-env/stop`

Stops and deletes the running development environment.

### `./bin/dev-env/build`

Builds & pushes the development environment.

### `./bin/shell`

Runs a new `bash` in the dev env. It also serves as an example of how to source `./bin/dev-env/runner` and use `run` command.

## CI

Project comes with a basic Circle CI pipeline configuration under `./circleci/config.yml`.

## .editorconfig

Project contains an [`.editconfig`](https://editorconfig.org/) for consistent coding style across different editors.