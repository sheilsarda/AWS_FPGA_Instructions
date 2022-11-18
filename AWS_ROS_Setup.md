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



