# Running Airflow in Docker

This quick-start guide will allow you to quickly get Airflow up and running with the CeleryExecutor in Docker

### Caution

This procedure can be useful learning and exploration. However, adapting it for use in real-world situations can be complicated. Making changes to this procedure will require specialized in Docker & Docker Compose, and the Airflow community may not be able to help you.

For that reason, we recommend using Kebernetes with the Official Airflow Community Helm Chart when you ready to run Airflow in production.

### Before you Begin

This procedure assumes familiarity with Docker and Docker Compose. If you haven't worked with these tools before, you should take a moment to run throught the Docker Quick Start (especially the section on Docker Compose) so you are familiar with how they word.

Follow these steps to install the necessary tools, if you have not already done so.

<p>1. Install Docker Community Edition (CE) on your workstation. Depending on your OS, you may need to configure Docker to use at least 4.00 GB of memory the Airflow conteineres to run properly. Please refer to the Resouces section in the Docker for Windows or Docker for Mac documentation for more information</p>
<p>2. Install Docker Compose v2.14.0 or newer on your workstation.</p>

Older version of docker-compose do not support all the features required by the Airflow docker-compose.yml file, so double check that your version meets the minimum version requirements.

### Tip

The default amount of memory available for Docker on macOS is ofthen not enough to get Airflow up and running. If enought memory is not allocated, it might lead to the webserver continuosly restarting. You should allocate at least 4GB memory for the Docker Engine (ideally 8GB).

You can check if you have enough by running this command:

docker run --rm "debian:bullseye-slim" bash -c 'numfmt --to iec $(echo $(($(getconf _PHYS_PAGES) * $(getconf PAGE_SIZE))))'

### Warning

Some operating systems (Fedora, ArchLinux, RHEL, Rocky) have recently introduced Kernel changes that result in Airflow in Docker Compose consuming 100% memory when run inside the community Docker implementation maintained by OS teams.

This is an issue with backwards-incompatible containerd configuration that some of Airflow dependencies have problems with and is tracked in a few issues:

- Moby issue
- Containeres issue

There is no solution yet from the containerd team, but seems that installing Docker Desktop on Linus solves the problem as stated in This comment and allows to run Breeze with no problems. 



https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html#running-airflow-in-docker
