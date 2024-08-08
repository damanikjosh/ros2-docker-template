ARG ROS_DISTRO=jazzy

FROM osrf/ros:${ROS_DISTRO}-desktop-full
LABEL authors="Joshua J. Damanik <joshuajdmk@gmail.com>"

ENV DEBIAN_FRONTEND=noninteractive

# Install some basic dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    xterm \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Install ros dependencies
RUN apt-get update && apt-get install -y \
    ros-${ROS_DISTRO}-turtlesim \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /ros2_ws

COPY src/common src/common
COPY src/simulator src/simulator

ENV GZ_VERSION=harmonic

RUN . /opt/ros/${ROS_DISTRO}/setup.sh \
    && colcon build --symlink-install \
    && echo "source /ros2_ws/install/setup.bash" >> /root/.bashrc

COPY simulator/entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]