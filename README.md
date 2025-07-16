# PARC2025-Engineers-League-Phase2
This repository provides information how to setup the docker container to be used in the real world phase of the PARC 2025 Engineers League competition in Senegal.

## Download Docker

It is assumed that the PC your team has running Ubuntu 24.04 with Docker installed. If you do not have Docker installed on your PC run the following commands:

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

To run docker commands with `sudo` run these commands:

```
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
```

You can verify the Docker installation by pulling this test image:

```
docker run hello-world
```

## Pull Docker Image

The Docker image used is based on Ubuntu 22.04 which will uses the Humble version of ROS2. Pull the image from Docker hub with this command:

```
docker pull thenoobinventor/parc2025-humble:latest
```

## Clone repository

Clone this project repository:

```
git clone https://github.com/PARC-Robotics/PARC2025-Engineers-League-Phase2.git
```

## Commands to enable GUI use on your PC

To be able to use a graphical user interface (GUI), like `RViz`, on your host machine when you run `RViz` in the container, execute the following commands on your host machine NOT in the container:

```
xhost +local:root
ps aux | grep X
```

## Create a container

Before running a container, edit these parts of the `docker-compose.yml` file in the repository:

```
volumes:
- '/home/noobmsi/parc2025_humble/src:/home/ros/ros2_ws/src'
```

Replace `noobmsi/parc2025_humble` with your PC username and the chosen workspace name on your PC.

While still in the project repository, create and run a Docker container in detached mode with `docker compose`:

```
docker compose up -d
```

Attach to the created container with this command:

```
docker attach parc2025-humble
````
