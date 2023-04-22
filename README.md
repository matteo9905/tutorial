# tutorial
PX4 TUTORIAL
Before starting installing PX4-Autopilot firmware,we need to install ROS2 foxy and gazebo 11(It's suggested to use these versions by the PX4 dev team).
In order to install ROS2 foxy we need to follow the following instructions:
# locale  # check for UTF-8
  sudo apt update && sudo apt install locales
  sudo locale-gen en_US en_US.UTF-8
  sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
  export LANG=en_US.UTF-8
  locale  # verify settings

