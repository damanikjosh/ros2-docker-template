# ROS 2 Docker development environment template

This repository contains a template for setting up a ROS 2 development environment using Docker. The template is designed to be a starting point for developing ROS 2 packages in a Docker container. The template includes a Dockerfile for building a ROS 2 development environment, a docker-compose file for managing the container, and a sample ROS 2 package.

## Folder structure

- `robot`: Contains the Dockerfile and docker-compose file for building and running the hardware interface.
- `simulator`: Contains the Dockerfile and docker-compose file for building and running the simulator.
- `src`: Contains the source code for the ROS 2 package.
  - `src/common`: Contains common code shared between the robot and simulator.
  - `src/robot`: Contains the code for the robot hardware interface.
  - `src/simulator`: Contains the code for the simulator.# ROS 2 Docker development environment template

## Prerequisites

- **Docker**. Follow the instructions [here](https://docs.docker.com/get-docker/) to install Docker.
- **Docker Compose**. Follow the instructions [here](https://docs.docker.com/compose/install/) to install Docker Compose.
- **NVIDIA Container Toolkit** (optional). Follow the instructions [here](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) to install the NVIDIA Container Toolkit if you have an NVIDIA GPU.

## Getting started

In the `simulator/Dockerfile`, I added `turtlesim` as an example package. You can replace it with your own package. 

1. Clone this repository:

```bash
git clone https://github.com/damanikjosh/ros2-docker-template.git
```
2. Build the Docker image:

```bash
cd ros2-docker-template/simulator
docker compose build
```

3. Initialize the xhost to allow the Docker container to display GUI applications:

```bash
xhost +local:root
```

4. Start the Docker container:

```bash
docker compose up
```