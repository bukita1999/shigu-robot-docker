From choate1990/ros_china:melodic-ros-desktop-full

SHELL ["/bin/bash", "-c"]
#复制Shigu源码
RUN mkdir -p ~/Shigu/src && cd ~/Shigu/src && git clone https://gitee.com/bukita2019/shigu_robot.git && ls

RUN cd ~/Shigu/src && git clone https://gitee.com/bukita2019/shigu_robot_dependence.git

RUN apt update && apt-get install -y \
    libceres-dev libgps-dev ros-melodic-geographic-msgs \
    libgeographic-dev ros-melodic-geographic-* ros-melodic-qt-build \
    geographiclib-* ros-melodic-serial ros-melodic-tf2-sensor-msgs\
    && ln -s /usr/share/cmake/geographiclib/FindGeographicLib.cmake /usr/share/cmake-3.10/Modules/


RUN cd ~/Shigu && source /opt/ros/melodic/setup.bash && catkin_make

