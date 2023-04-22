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
  sudo apt install gazebo11
  ```
  
  ### INSTALL PX4-AUTOPILOT FIRMWARE
  
  The PX4 source code is stored on Github in the PX4/PX4-Autopilot repository.To get the very latest ("main") version onto your computer, enter the           following command into a terminal:
  ```
  git clone https://github.com/PX4/PX4-Autopilot.git --recursive
  ```
  Run the ubuntu.sh with no arguments (in a bash shell) to install everything:
  ```
  bash ./PX4-Autopilot/Tools/setup/ubuntu.sh
  ```
  Then you need to reboot your PC.
  After having rebooted you PC you can launch the following line on the terminal:
  ```
  make px4_sitl gazebo-classic
  ```
  The build system makes it very easy to build and start PX4 on SITL, launch a simulator, and connect them. The syntax (simplified) looks like this:
  ```
  make px4_sitl simulator[_vehicle-model]
  ```
  Where simulator is gz (for Gazebo), gazebo-classic, jmavsim or some other simulator, and vehicle-model is a particular vehicle type supported by that       simulator (Gazebo and jMAVSim only support multicopters at time of writing, while Gazebo Classic supports many different types.A number of examples are     shown below, and there are many more in the individual pages for each of the simulators:
  1. Start Gazebo Classic with iris drone
  ```
  make px4_sitl gazebo-classic_iris
  ```
  2. Start Gazebo Classic with classic plane
  ```
  make px4_sitl gazebo-classic-classic_plane
  ```
  ### SETUP XRCE-DDS AGENT & CLIENT
  PX4 uses XRCE-DDS middleware to allow uORB messages to be published and subscribed on a companion computer as though they were ROS 2 topics. This           provides a fast and reliable integration between PX4 and ROS 2, and makes it much easier for ROS 2 applications to get vehicle information and send         commands. You can find all the details at the following URL https://docs.px4.io/main/en/middleware/xrce_dds.html
  To setup and start the agent:
  1. Open a terminal
  2. Enter the following commands to fetch and build the agent from source:
  ```
  git clone https://github.com/eProsima/Micro-XRCE-DDS-Agent.git
  cd Micro-XRCE-DDS-Agent
  mkdir build
  cd build
  cmake ..
  make
  sudo make install
  sudo ldconfig /usr/local/lib/
  ```
  3. Start the agent with settings for connecting to the XRCE-DDS client running on the simulator:
   ```
   MicroXRCEAgent udp4 -p 8888
   ```
