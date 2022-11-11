# Docker Compose Workflow for Joplin Server

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Notes](#notes)

## About <a name = "about"></a>

[Joplin](https://joplinapp.org) is an open-source note-taking/notebook app which allows synchronization of notebook data to a number of various sources, including its own self-hosted web service. This then, is a [Docker Compose](https://docs.docker.com/compose/) workflow which can be used to deploy Joplin Server as a stack of microservices (Joplin Server, PostgreSQL, Caddy).

## Getting Started <a name = "getting_started"></a>

This workflow is meant to be deployed remotely, through the use of Docker Contexts, the set up for which is shown below.

### Prerequisites

* Docker
* Docker Compose

### Production Deployment

1. Clone this repo onto the machine you'll be deploying Joplin onto.
2. Set up your deployment target as a Docker Context:

```bash
docker context create joplin-prod \
    --default-stack-orchestrator=swarm \
    --docker host=ssh://<user>@<host>
```

3. Fill out the details in `./environment/joplin.env`
3. Update the `server_name` directives along with the paths to the Certbot-issued SSL information in the included Nginx config file (`./nginx/joplin.conf`) with the correct hostname.
4. Once all these options are set, bring up the service stack using the following command:

```bash
DOCKER_CONTEXT=joplin-prod POSTGRES_PASSWD=<password> docker-compose up -d
```

### Development

> NOTE: All the steps for Development are the same except for the following:

1. Use the default local docker context instead of the remote one
2. Change the `ENVIRONMENT` variable in `./config/joplin.env` to `development`
3. Deploy the stack using the following command:

```bash
POSTGRES_PASSWD=<password>
```

## Notes

* For more information on Docker Contexts, check [the official documentation](https://docs.docker.com/engine/context/working-with-contexts/)

* This deployment stack is also published as a Docker App on Docker Hub (TODO)

* the development