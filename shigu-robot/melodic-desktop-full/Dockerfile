From choate1990/ros_china:melodic-ros-desktop-full

SHELL ["/bin/bash", "-c"]

RUN apt update && apt install -y git
#复制Shigu源码
RUN mkdir -p ~/Shigu/src && cd ~/Shigu/src && git clone https://gitee.com/bukita2019/shigu_robot.git && ls

#下载依赖
RUN cd ~/Shigu/src && git clone https://gitee.com/bukita2019/shigu_robot_dependence.git \
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-teleop/twist_mux.git \
    && git clone -b kinetic-devel https://github.91chi.fun/https://github.com/ros-visualization/interactive_marker_twist_server.git\
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-perception/slam_gmapping.git \
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros/robot_state_publisher.git \
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/bukita1999/robot_localization.git
    

RUN cd ~/Shigu/src && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-perception/openslam_gmapping.git\
    && git clone -b ros1 https://github.91chi.fun/https://github.com/ros-planning/navigation_msgs.git\
    && git clone -b melodic-devel https://github.91chi.fun/https://github.com/ros-planning/navigation.git

RUN apt update && apt-get install -y \
    libceres-dev libgps-dev ros-melodic-geographic-msgs \
    libgeographic-dev ros-melodic-geographic-* ros-melodic-qt-build \
    geographiclib-* ros-melodic-serial ros-melodic-tf2-sensor-msgs\
    ros-melodic-fiducial-msgs ros-melodic-rtabmap-ros libsdl-image1.2-dev libsdl-dev \
    mesa-utils software-properties-common\
    && ln -s /usr/share/cmake/geographiclib/FindGeographicLib.cmake /usr/share/cmake-3.10/Modules/ 
    
RUN cd ~/ && git clone https://github.91chi.fun/https://github.com/chaolmu/gazebo_models_worlds_collection.git \
    && cd ~/gazebo_models_worlds_collection && cp -r models ~/.gazebo/ \
    && rm -rf ~/gazebo_models_worlds_collection/models


# RUN add-apt-repository ppa:kisak/kisak-mesa && apt-get update && apt -y dist-upgrade


RUN cd ~/Shigu && source /opt/ros/melodic/setup.bash && catkin_make

RUN source /opt/ros/melodic/setup.bash && source ~/Shigu/devel/setup.bash 

RUN rostest shigu_gazebo available_data_test.test

RUN rostest shigu_gazebo unavailable_data_test.test



