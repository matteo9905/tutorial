# tutorial
## PX4 TUTORIAL
Before starting installing PX4-Autopilot firmware,we need to install ROS2 foxy and gazebo 11(It's suggested to use these versions by the PX4 dev team).
In order to install ROS2 foxy we need to follow the following instructions:
### INSTALL ROS2 FOXY
  You can find all the above instruction at this URL https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html 
  ```
# locale  # check for UTF-8
  sudo apt update && sudo apt install locales
  sudo locale-gen en_US en_US.UTF-8
  sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
  export LANG=en_US.UTF-8
  locale  # verify settings
  ```
  ```
  sudo apt install software-properties-common
  sudo add-apt-repository universe
  ```
  ```
  sudo apt update && sudo apt install curl -y
  sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
  ```
  If curl command does not work, you need to install it.
  ```
  echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-       release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```
  Update the system:
  ```
  sudo apt update && sudo apt upgrade
  ```
  Desktop Install (Recommended): ROS, RViz, demos, tutorials.
  ```
  sudo apt install ros-foxy-desktop python3-argcomplete
  ```
