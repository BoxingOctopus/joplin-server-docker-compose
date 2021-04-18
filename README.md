# Docker Compose Workflow for Joplin Server

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Notes](#notes)

## About <a name = "about"></a>

[Joplin](https://joplinapp.org) is an open-source note-taking/notebook app which allows synchronization of notebook data to a number of various sources, including its own self-hosted web service. This then, is a [Docker Compose](https://docs.docker.com/compose/) workflow which can be used to deploy Joplin Server as a stack of microservices (Joplin Server, PostgreSQL, Nginx + Certbot).

## Getting Started <a name = "getting_started"></a>

### Prerequisites

* Docker
* Docker Compose

### Pre-Flight Configuration Steps

1. Clone this repo onto the machine you'll be deploying Joplin onto.
2. Fill out the details in `./environment/joplin.env`
3. Update the `server_name` directives along with the paths to the Certbot-issued SSL information in the included Nginx config file (`./ngnix/joplin.conf`) with the correct hostname.
4. Update the `domains` and `email` variables in `./scripts/init-letsencrypt.sh` 

Once all these options are set, bring up the service stack using the following command:

```bash
POSTGRES_PASSWD=<password> docker-compose up -d
```

## Notes <a name = "notes"></a>

* The `postgres` service stores its database on a named volume (`joplin_db`).
* The `postgres` service will automatically backup the database and dump the backups in the `./pg_backup` directory on the host. It is recommended that the `./pg_backup` directory be used as a mount point for a remote filesystem. In future, Amazon S3/DigitalOcean Spaces may be used as the default for this.
* The `certbot` and `nginx` services will automatically renew the SSL cert every twelve hours. 
