# ROS 2 Humble Installation Guide

This guide provides step-by-step instructions for installing ROS 2 Humble Hawksbill on Ubuntu 22.04 (Jammy).

**Official Documentation Reference:** [ROS 2 Documentation - Ubuntu Installation](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)

## Prerequisites

ROS 2 Humble packages are currently available for Ubuntu Jammy (22.04). Make sure you're running a supported Ubuntu version.

## Set Locale

Make sure you have a locale which supports UTF-8:

```bash
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```

## Setup Sources

Add the ROS 2 apt repository to your system.

First ensure that the Ubuntu Universe repository is enabled:

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

Install the ROS 2 apt source configuration:

```bash
sudo apt update && sudo apt install curl -y
export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')
curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo ${UBUNTU_CODENAME:-${VERSION_CODENAME}})_all.deb"
sudo dpkg -i /tmp/ros2-apt-source.deb
```

## Install ROS 2 Packages

Update your apt repository caches and upgrade your system:

```bash
sudo apt update
sudo apt upgrade
```

**Warning:** Due to early updates in Ubuntu 22.04, it is important that systemd and udev-related packages are updated before installing ROS 2.

Choose one of the following installation options:

### Desktop Install (Recommended)
Includes ROS, RViz, demos, tutorials:

```bash
sudo apt install ros-humble-desktop
```

### ROS-Base Install (Bare Bones)
Communication libraries, message packages, command line tools. No GUI tools:

```bash
sudo apt install ros-humble-ros-base
```

### Development Tools
Compilers and other tools to build ROS packages:

```bash
sudo apt install ros-dev-tools
```

## Environment Setup

### Sourcing the Setup Script

Set up your environment by sourcing the following file:

```bash
source /opt/ros/humble/setup.bash
```

**Note:** Replace `.bash` with your shell if you're not using bash. Possible values are: `setup.bash`, `setup.sh`, `setup.zsh`.

To automatically source this script every time you open a new terminal, add it to your shell startup script:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

## Try Some Examples

### Talker-Listener Test

If you installed `ros-humble-desktop`, you can try some examples to verify your installation.

In one terminal, run a C++ talker:

```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp talker
```

In another terminal, run a Python listener:

```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_py listener
```

You should see the talker saying that it's Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly.

## Install TurtleBot3 Packages

For the exercises in this course, you'll also need TurtleBot3 packages:

```bash
sudo apt install ros-humble-turtlebot3*
```

## Install Additional Tools

Install useful ROS 2 tools for development:

```bash
sudo apt install ros-humble-teleop-twist-keyboard
sudo apt install ros-humble-rviz2
sudo apt install ros-humble-gazebo-ros-pkgs
```

## Uninstall (Optional)

If you need to uninstall ROS 2:

```bash
sudo apt remove ~nros-humble-* && sudo apt autoremove
```

You may also want to remove the repository:

```bash
sudo apt remove ros2-apt-source
sudo apt update
sudo apt autoremove
sudo apt upgrade
```

