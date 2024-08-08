ARG ROS_DISTRO=jazzy

FROM ros:${ROS_DISTRO}-ros-base
LABEL authors="Joshua J. Damanik <joshuajdmk@gmail.com>"

ENV DEBIAN_FRONTEND=noninteractive

# Install some basic dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Install ros dependencies
RUN apt-get update && apt-get install -y \
    # add ros packages here \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /ros2_ws

COPY src/common src/common
COPY src/robot src/robot

ENV GZ_VERSION=harmonic

RUN . /opt/ros/${ROS_DISTRO}/setup.sh \
    && colcon build --symlink-install \
    && echo "source /ros2_ws/install/setup.bash" >> /root/.bashrc

COPY simulator/entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]