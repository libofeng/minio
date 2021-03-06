# Deploy Minio on Docker Compose [![Slack](https://slack.minio.io/slack?type=svg)](https://slack.minio.io) [![Go Report Card](https://goreportcard.com/badge/minio/minio)](https://goreportcard.com/report/minio/minio) [![Docker Pulls](https://img.shields.io/docker/pulls/minio/minio.svg?maxAge=604800)](https://hub.docker.com/r/minio/minio/) [![codecov](https://codecov.io/gh/minio/minio/branch/master/graph/badge.svg)](https://codecov.io/gh/minio/minio)

Docker Compose allows defining and running single host, multi-container Docker applications.

With Compose, you use a Compose file to configure Minio services. Then, using a single command, you can create and launch all the Distributed Minio instances from your configuration. Distributed Minio instances will be deployed in multiple containers on the same host. This is a great way to set up development, testing, and staging environments, based on Distributed Minio. 

## 1. Prerequisites

* Familiarity with [Docker Compose](https://docs.docker.com/compose/overview/).
* Docker installed on your machine. Download the relevant installer from [here](https://www.docker.com/community-edition#/download).

## 2. Run Distributed Minio on Docker Compose

To deploy Distributed Minio on Docker Compose, please download [docker-compose.yaml](https://github.com/minio/minio/blob/master/docs/orchestration/docker-compose/docker-compose.yaml?raw=true) to your current working directory. Note that Docker Compose pulls the Minio Docker image, so there is no need to explicitly download Minio binary. Then run one of the below commands

### GNU/Linux and macOS

```sh
docker-compose pull
docker-compose up
```

### Windows

```sh
docker-compose.exe pull
docker-compose.exe up
```

Each instance is now accessible on the host at ports 9001 through 9004, proceed to access the Web browser at http://127.0.0.1:9001/

### Notes

* By default the Docker Compose file uses the Docker image for latest Minio server release. You can change the image tag to pull a specific [Minio Docker image](https://hub.docker.com/r/minio/minio/).

* There are 4 minio distributed instances created by default. You can add more Minio services (up to total 16) to your Minio Compose deployment. To add a service
  * Replicate a service definition and change the name of the new service appropriately.
  * Update the command section in each service.
  * Update the port number to exposed for the new service. Also, make sure the port assigned for the new service is not already being used on the host.

  Read more about distributed Minio [here](https://docs.minio.io/docs/distributed-minio-quickstart-guide).

* Minio services in the Docker compose file expose ports 9001 to 9004. This allows multiple services to run on a host.

### Explore Further
- [Minio Erasure Code QuickStart Guide](https://docs.minio.io/docs/minio-erasure-code-quickstart-guide)
- [Use `mc` with Minio Server](https://docs.minio.io/docs/minio-client-quickstart-guide)
- [Use `aws-cli` with Minio Server](https://docs.minio.io/docs/aws-cli-with-minio)
- [Use `s3cmd` with Minio Server](https://docs.minio.io/docs/s3cmd-with-minio)
- [Use `minio-go` SDK with Minio Server](https://docs.minio.io/docs/golang-client-quickstart-guide)
- [The Minio documentation website](https://docs.minio.io)
