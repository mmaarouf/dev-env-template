# dev-env-template
Template development environment to be used when creating new projects.

## Setup steps
* Set the project name in `$PROJECT_NAME` variable in `./bin/dev-env`
* Replace all `{{PROJECT_NAME}}` instances in ./docker/docker-compose.yml with the project name
* Customise `./docker/Dockerfile.dev` with all the development tools needed
* Use `./bin/build-dev-env` to build and publish the dev environment under `mmaarouf/$PROJECT_NAME-dev-env` **public** repo on Dockerhub

## Scripts

### `./bin/dev-env`
Script containing the `run` command which can be sourced into other scripts and used to execute commands in either
an already running dev-env container or in a new ephemeral instance.

### `./bin/start-dev-env`
Starts the development environment and leaves it running in the background.

### `./bin/stop-dev-env`
Stops and deletes the running development environment.

### `./bin/build-dev-env`
Builds & pushes the development environment.
