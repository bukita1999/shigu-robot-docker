From choate1990/ros_china:noetic-ros-desktop-full

SHELL ["/bin/bash", "-c"]

RUN apt update && apt install -y git
#复制Shigu源码
RUN mkdir -p ~/Shigu/src && cd ~/Shigu/src && git clone https://gitee.com/bukita2019/shigu_robot.git && ls

#下载依赖
RUN cd ~/Shigu/src && git clone -b noetic-devel https://gitee.com/bukita2019/shigu_robot_dependence.git \
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-teleop/twist_mux.git \
    && git clone -b kinetic-devel https://github.91chi.fun/https://github.com/ros-visualization/interactive_marker_twist_server.git\
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-perception/slam_gmapping.git \
    && git clone -b noetic-devel https://github.91chi.fun/https://github.com/ros/robot_state_publisher.git \
    && git clone -b noetic-devel https://github.91chi.fun/https://github.com/cra-ros-pkg/robot_localization.git \
    && git clone -b noetic-devel https://github.91chi.fun/https://github.com/ros-planning/navigation.git

RUN cd ~/Shigu/src && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-perception/openslam_gmapping.git\
    && git clone -b ros1 https://github.91chi.fun/https://github.com/ros-planning/navigation_msgs.git

RUN apt update && apt-get install -y \
    libceres-dev libgps-dev ros-noetic-geographic-msgs \
    libgeographic-dev ros-noetic-geographic-* \
    geographiclib-* ros-noetic-serial ros-noetic-tf2-sensor-msgs\
    ros-noetic-fiducial-msgs ros-noetic-rtabmap-ros libsdl-image1.2-dev libsdl-dev \
    && ln -s /usr/share/cmake/geographiclib/FindGeographicLib.cmake /usr/share/cmake-3.16/Modules/



RUN cd ~/Shigu && source /opt/ros/noetic/setup.bash && catkin_make



