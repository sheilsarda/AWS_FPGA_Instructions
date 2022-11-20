# Getting ROS setup on EC2 Ubuntu 22.0

## ROS 2 Hawksbill installation instructions
### [Source](https://docs.ros.org/en/humble/Installation.html)

#### Step 1: UTF-8 Locale
```sh
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

#### Step 2: Ubuntu Universe and ROS Package
```sh
sudo apt install software-properties-common
sudo apt-get install build-essential
sudo add-apt-repository universe
sudo apt update && sudo apt install curl gnupg lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

#### Step 3: Install non-GUI ROS (base)
```sh
sudo apt update
sudo apt upgrade
sudo apt install ros-humble-ros-base
source /opt/ros/humble/setup.bash
```

#### Step 4: Necessary Packages
```sh
sudo apt install python3-colcon-common-extensions
sudo apt install python3-rosdep2
```

## How to Write Packages

### Init Package
#### [Source](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Creating-Your-First-ROS2-Package.html)
```sh
cd ~/ros2_ws/src
ros2 pkg create --build-type ament_cmake <package_name>
```
OR if you want a hello world executable to start with:
```sh
ros2 pkg create --build-type ament_cmake --node-name my_node my_package
cd ~/ros2_ws
colcon build
```
### Creating Launch Files
#### [Source](https://docs.ros.org/en/humble/Tutorials/Intermediate/Launch/Creating-Launch-Files.html)

### Running Packages
```sh
colcon build
. install/setup.bash
ros2 run <package-name> <node-name>
```

### Other Helpful Dependencies
```sh
sudo apt install picocom
sudo apt install socat
```