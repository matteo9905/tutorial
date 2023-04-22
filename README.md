# TUTORIAL
## PX4 TUTORIAL
Before starting installing PX4-Autopilot firmware,we need to install ROS2 foxy and gazebo 11(It's suggested to use these versions by the PX4 dev team).
We need to install the following tools:
- Install ROS2 foxy and Gazebo11
* Install PX4-Autopilot firmware
+ Setup XRCE-DDS Agent & Client

### INSTALL ROS2 FOXY and GAZEBO
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
  Development tools: Compilers and other tools to build ROS packages
   ```
   sudo apt install ros-dev-tools
   ```
  Some Python dependencies must also be installed (using pip or apt):
  ```
  pip3 install --user -U empy pyros-genmsg setuptools
  ```
  If you want to check if ROS has been properly installed you can try launching two default nodes:a talker and a listener.
  First of all set up your environment by sourcing the following file.
  ```
  # Replace ".bash" with your shell if you're not using bash
  # Possible values are: setup.bash, setup.sh, setup.zsh
  source /opt/ros/foxy/setup.bash
  ```
  Run the C++ talker:
  ```
  ros2 run demo_nodes_cpp talker
  ```
  Open another terminal,source it and run the listener:
  ```
  source /opt/ros/foxy/setup.bash
  ros2 run demo_nodes_py listener
  ```
  If these two simple nodes work, it means ROS has been properly installed.
  
  Then install the GAZEBO:
  ```
  curl -sSL http://get.gazebosim.org | sh
  ```
  
  
  ### INSTALL PX4-AUTOPILOT FIRMWARE
  
