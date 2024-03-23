# jasonbot_ROS2
My robot package built with ROS2 and colcon package management.

## Setup
1. Follow the guide to install ROS2 
    * [Install GUide](https://video.udacity-data.com/topher/2023/October/6538afad_udacity_ros2_gazebo_tutorial.docx/udacity_ros2_gazebo_tutorial.docx.pdf)
```
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update
sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# Change jammy to what Ubuntu distro you actually use 
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt upgrade

# For the following, change humble for the latest or your preferred distro
sudo apt install ros-humble-desktop
source /opt/ros/humble/setup.bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
sudo apt install lsb-release wget gnupg
sudo wget https://packages.osrfoundation.org/gazebo.gpg -O /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt update
sudo apt install ignition-fortress

curl -sSL http://get.gazebosim.org | sh

```
2. Install colcon package manager
```
sudo apt install python3-colcon-common-extensions

# Setup colcon_cd
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
# change the humble to the exact version of ros2 on your system
echo "export _colcon_cd_root=/opt/ros/humble/" >> ~/.bashrc

# Setup colcon_tab
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```
##

PS. To create a package in ROS2, you execute the following command
```
# NOTE: Similar to the function of catkin_create_pkg <package name> in ROS 1 

ros2 pkg create --build-type ament_cmake <package name> --dependencies [dep 1] [dep 2] ...
# e.g. ros2 pkg create --build-type ament_cmake jsonbot_ros2 --dependencies rclcpp std_msgs
```
