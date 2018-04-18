# Docker Bastion

This repository builds a very slim bastion host suitable for use in any container environment (e.g. Docker Compose, Amazon ECR). It supports only SSH access by default. Once in there are a handful of Swiss Army style tools including DB clients for PostgreSQL and MySQL.

## Usage

You could launch it as a stand alone instance on the server:

    docker run -e SSH_PASSWORD=shU3a2KnRv1n0LPNz \
        -d -P \
        --link database \
        meanbee/bastion

Or you could add it to your `docker-compose` configuration:

    bastion:
        image: meanbee/bastion
        environment:
            - SSH_PASSWORD=shU3a2KnRv1n0LPNz
        links:
            - database
        expose:
            - 22

You can SSH into the container using the published port and the `bastion` user with the provided password.

## Environment variables

### SSH_PASSWORD

Required. Sets the password for the `bastion` user.

### SSH_HOME_DIR

Optional. Sets the home directory for the `bastion` user.

## Credits

Originally forked from https://github.com/meanbee/docker-bastion
