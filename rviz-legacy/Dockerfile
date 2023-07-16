ARG ROS_DISTRO=kinetic

# Start with a base ROS image
FROM ros:${ROS_DISTRO}

# Install RViz
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    dbus \
    mesa-utils \
    ros-${ROS_DISTRO}-rviz \
 && rm -rf /var/lib/apt/lists/*

# Change to different locale to fix bug in Fontconfig in Ubuntu 14.04 (optional)
# BUG: <Fontconfig warning: ignoring C.UTF-8: not a valid language tag>
# RUN locale-gen en_US en_US.UTF-8
# ENV LC_ALL=en_US.UTF-8
# ENV LANG=en_US.UTF-8

# Launch RViz
CMD ["rosrun", "rviz", "rviz"]
