ARG ROS_DISTRO=humble

# Start with a base ROS2 image
FROM ros:${ROS_DISTRO}

# Install RViz2
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    software-properties-common \
 && add-apt-repository ppa:kisak/kisak-mesa \
 && apt-get update \
 && apt-get install -y --no-install-recommends \
    libqt5svg5 \
    mesa-utils \
    ros-${ROS_DISTRO}-rviz2 \
 && rm -rf /var/lib/apt/lists/*

# Add WSL2 default user to enable WSL2 users to forward their XDG_RUNTIME_DIR (optional)
# BUG: <QStandardPaths: runtime directory '/mnt/wslg/runtime-dir' is not owned by UID 0, but a directory permissions 0700 owned by UID 1000 GID 1000>
# ARG USERNAME=wsl-root
# ARG USER_UID=1000
# ARG USER_GID=1000
# RUN groupadd --gid ${USER_GID} ${USERNAME} \
#  && useradd --uid ${USER_UID} --gid ${USER_GID} -m ${USERNAME}

# Launch Rviz2
CMD ["ros2", "run", "rviz2", "rviz2"]
