# Introduction to ROS2 with Raspberry Pi 5

<p align="center">
    <br>
    <img src="etc/img/SUSeal-1color.png" alt="GIF Image" width="275"/>
</p>

## About

<p align="center">
    <br>
    <img src="etc/gif/ROS2.gif" alt="GIF Image" width="150"/>
</p>

[About](#about) • [Requirements](#requirements) • [Setup](#setup) • [Directory](#directory) • [Maintenance](#maintenance)

This repository acts as a guide for installing and configuring ROS2 on a Raspberry Pi [RPi] 5 device running the Ubuntu 22.04+ LTS operating system.

## Requirements

In order for the setup.sh script to run without any configurations required, the following are required:

- Raspberry Pi 5 (either 4 or 8 GB) with power source 
- 16 GB (minimum) microSD card with Ubuntu latest LTS flash
- Display device along with mouse + keyboard for the RPi
-- If you've setup a local user and password for the RPi during OS configuration, you can simply ssh into the RPi without the need for an external display via your laptop using the following command:
```bash
ssh username@ip
```

### Congifuring the Ubuntu flash

When configuring the settings for the microSD imager via the [Raspberry Pi imager](https://www.raspberrypi.com/software/), ensure that the __Ubuntu Desktop 24.xx LTS (64-bit)__ OS is selected and not the default Raspberry Pi OS. Also, set the _username_ of the RPi to "__test__". Without this change, you will need to edit the file location for sourcing the virtual enviornment among a few other commands.

## Setup

After the initial setup of your RPi device and it is connected to a reliable internet source, clone this repository into the main RPi home folder. 

```bash
git clone git@github.com:SU-Innovation-Lab/ROS2.git
```

The setup.sh script installs ROS2 and all of its required dependencies onto the local Raspberry Pi 5 device. 

<b style="color:red;">Note!</b> Upon successful completion of the setup.sh script, the RPi is expected to reboot. Once it starts back up, the 'ros2_venv' virtual enviornment should be activated and noted within the RPi terminal. You may need to hit the [Enter] key a few times during installation.

``` bash
# From the ROS2 directory, migrate to the setup script
cd ROS2/config

# Ensure that the setup.sh script is executable then execute it
chmod +rwx setup.sh
./setup.sh
```

After the RPi starts back up and the ros2_venv enviornment is active, test that ROS2 has been correctly installed on the device by running the following commands in __two seperate terminal windows__:

```bash
# Talker terminal
source /opt/ros/jazzy/setup.bash
ros2 run demo_nodes_cpp talker
```

```bash
# Listener terminal
source /opt/ros/jazzy/setup.bash
ros2 run demo_nodes_py listener
```

You should see the talker saying it's publishing messages and the listener saying it heard those messages showing both the C++ and Python APIs working properly.

## Directory

### 📁 /config

- __setup.sh__: This script installs ROS2 and all of its required dependencies onto the local Raspberry Pi 5 device. It sets up a Python virtual environment, installs necessary Python packages, and configures the system for ROS2.

### 📁 /docs

- __README.md__: This file. Provides an overview of the repository, setup instructions, and a directory of scripts and configuration files.

### 📁 /etc

This folder contains items (images, gifs, videos) used for visual purposes.

## Maintenance

### Git Branch

[3.1 Git Branching - Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

When making edits to the repository, it is good practice to newver commit directly to the main branch. Instead, create an additional branch that will be easy to identiy for your personal edits.

```bash
# a common branch name can be firstname.lastname
git checkout -b *branch-name
```

Basic idea to commiting:

1. Create a new personal branch
2. Make commits and push to such branch
3. Submit review to respority maintaners for compare and pull request to main branch