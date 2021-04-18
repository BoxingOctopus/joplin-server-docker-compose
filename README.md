# Docker Compose Workflow for Joplin Server

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
- [Contributing](../CONTRIBUTING.md)

## About <a name = "about"></a>

[Joplin](https://joplinapp.org) is an open-source note-taking/notebook app which allows synchronization of notebook data to a number of various sources, including its own self-hosted web service. This then, is a [Docker Compose](https://docs.docker.com/compose/) workflow which can be used to deploy Joplin Server as a stack of microservices (Joplin Server, PostgreSQL, Nginx + Certbot).

## Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See [deployment](#deployment) for notes on how to deploy the project on a live system.

### Prerequisites

* Docker
* Docker Compose


### Installing

1. Clone this repo onto the machine you'll be deploying Joplin onto.
2. Fill out the details in `./environment/joplin.env`
3. Update the `server_name` directives along with the paths to the Certbot-issued SSL information in the included Nginx config file (`./ngnix/joplin.conf`) with the correct hostname.
4. Update the 

## Usage <a name = "usage"></a>

Add notes about how to use the system.
