# dev-env-template
Template development environment to be used when creating new projects.

## Setup steps
* Set the project name in `$PROJECT_NAME` variable in `./bin/dev-env/runner`
* Replace all `{{PROJECT_NAME}}` instances in ./docker/docker-compose.yml with the project name
* Customise `./docker/Dockerfile.dev` with all the development tools needed
* Use `./bin/dev-env/build` to build and publish the dev environment under `mmaarouf/$PROJECT_NAME-dev-env` **public** repo on Dockerhub

## Scripts

### `./bin/dev-env/runner`
Script containing the `run` command which can be sourced into other scripts and used to execute commands in either
an already running development environment container or in a new ephemeral instance.

### `./bin/dev-env/start`
Starts the development environment and leaves it running in the background.

### `./bin/dev-env/stop`
Stops and deletes the running development environment.

### `./bin/dev-env/build`
Builds & pushes the development environment.

### `./bin/shell`
Runs a new `sh` in the dev env. It also serves as an example of how to source `./bin/dev-env/runner` and use `run` command.

## CI
Project comes with a basic Circle CI pipeline configuration under `./circleci/config.yml`.

## .editorconfig
Project contains an [`.editconfig`](https://editorconfig.org/) for consistent coding style across different editors.
