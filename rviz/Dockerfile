ARG ROS_DISTRO=noetic

# Start with a base ROS image
FROM ros:${ROS_DISTRO}

# Install RViz
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    software-properties-common \
 && add-apt-repository ppa:kisak/turtle \
 && apt-get update \
 && apt-get install -y --no-install-recommends \
    dbus \
    mesa-utils \
    ros-${ROS_DISTRO}-rviz \
 && rm -rf /var/lib/apt/lists/*

# Add WSL2 default user to enable WSL2 users to forward their XDG_RUNTIME_DIR (optional)
# BUG: <QStandardPaths: runtime directory '/mnt/wslg/runtime-dir' is not owned by UID 0, but a directory permissions 0700 owned by UID 1000 GID 1000>
# ARG USERNAME=wsl-root
# ARG USER_UID=1000
# ARG USER_GID=1000
# RUN groupadd --gid ${USER_GID} ${USERNAME} \
#  && useradd --uid ${USER_UID} --gid ${USER_GID} -m ${USERNAME}

# Launch RViz
CMD ["rosrun", "rviz", "rviz"]
