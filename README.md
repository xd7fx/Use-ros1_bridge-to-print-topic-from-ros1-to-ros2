# Use ros1_bridge to print topic from ros1 to ros2

## Introduction
This project demonstrates how to bridge topics between ROS1 (Noetic) and ROS2 (Foxy) using `ros1_bridge`. By following the provided instructions, you will learn to set up both ROS versions, run turtlesim nodes, and establish a dynamic bridge for seamless topic communication. The steps include environment setup, running nodes, and verifying the bridge functionality. Troubleshooting tips are also included to help resolve common issues.

## Prerequisites
Ensure you have ROS1 (Noetic) and ROS2 (Foxy) installed on your system.

## Installation Instructions

## ROS1 (Noetic)
Press here 👉🏼
[ROS-Installation-Guide](https://github.com/xd7fx/ROS-Installation-Guide).

## ROS2 (Foxy)
# 1. **Set locale**
  ```sh
    locale  # check for UTF-8
    
    sudo apt update && sudo apt install locales
    sudo locale-gen en_US en_US.UTF-8
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    export LANG=en_US.UTF-8

    locale  # verify settings
  ```
![لقطة الشاشة 2024-07-17 062157](https://github.com/user-attachments/assets/8f926aa6-33fc-4b60-ad24-cab53925370b)


# 2. **Setup your sources.list**
  ```sh
    sudo apt install software-properties-common
    sudo add-apt-repository universe
  ```
![لقطة الشاشة 2024-07a-17 062431](https://github.com/user-attachments/assets/029ab671-900a-4be8-b898-f9f6702e2cf9)


## Now add the ROS 2 GPG key with apt.

  ```sh
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
  ```
![wqs](https://github.com/user-attachments/assets/ed0cab30-c31d-4a15-b85d-fc698040e207)

## Then add the repository to your sources list.
  ```sh
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```
![ssss](https://github.com/user-attachments/assets/e71330f5-802b-445a-8b47-2e8d3a89a77e)

# 3. **Installation**
  ```sh
    sudo apt update
    sudo apt install ros-foxy-desktop
    sudo apt install ros-dev-tools
  ```

![لقطة الشاشة 2024-07-17 0626s48](https://github.com/user-attachments/assets/71fd12e4-eaac-4284-9980-b5f170d68926)
![لقطة الشاشة 2024e-07-17 064302](https://github.com/user-attachments/assets/19f2292e-31e0-4a3d-bc2e-57f67f643116)
![لقطة الشاشة 2024-07-17 063035](https://github.com/user-attachments/assets/469026f4-0851-4742-b7bd-b17b487e0e6a)



# 4. **Environment Setup**
   ```sh
    echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
    source ~/.bashrc
   ```
![لقطة الشاشة 2024-07-17 064237](https://github.com/user-attachments/assets/a0ddda08-6493-49c9-8487-2fa8c3ad5b97)


## Usage

### Start ROS1 (Noetic)
1. **Source the ROS1 setup file and Run the turtlesim node**
    ```sh
    source /opt/ros/noetic/setup.bash
    roscore
    ```
![thfthft](https://github.com/user-attachments/assets/2d994de4-5933-4e65-91e6-8884856d49b7)


### Start turtlesim in ROS2 (Foxy)
1. **Source the ROS2 setup file and Run the turtlesim node**
    ```sh
    source /opt/ros/foxy/setup.bash
    ros2 run turtlesim turtlesim_node
    ```
![sadasdas](https://github.com/user-attachments/assets/8e9c23ce-2521-4e7d-b641-897d36d39146)



### Start turtlesim in ROS1 (Noetic)
1. **Source the ROS2 setup file and Run the turtlesim node**
    ```sh
    source /opt/ros/noetic/setup.bash
    rosrun turtlesim turtle_teleop_key
    ```
![لقطة الشاشة 2024-07-17 100726](https://github.com/user-attachments/assets/bbc018f1-bc50-4357-b1f5-208865b87664)

### Verify the Bridge
1. **List ROS1 and ROS2 nodes and topics**
    ```sh
    source /opt/ros/noetic/setup.bash
    rosnode list
    rostopic echo /turtle1/cmd_vel

    
    ros2 node list
    ros2 topic list
    ros2 topic echo /turtle1/cmd_vel
    ```

![dwawdaw](https://github.com/user-attachments/assets/ec027094-da51-4a18-846e-b8fc26e65533)


### Using ros1_bridge
  ```sh
    sudo apt install ros-foxy-ros1-bridge
  ```
1. **Download package**

![لقطة الشاشة 2024-07-17 085843](https://github.com/user-attachments/assets/cce02448-8f89-4725-9249-d96cb05ef4c1)


2. **Source both ROS1 and ROS2 setup files**
    ```sh
    source /opt/ros/noetic/setup.bash
    source /opt/ros/foxy/setup.bash
    ```
3. **Run the dynamic bridge**
    ```sh
    ros2 run ros1_bridge dynamic_bridge
    ```
Thus, we were able to operate the turtle on Ros2 and control from Ros1
![لقطة الشاشة 2024-07-17 100652](https://github.com/user-attachments/assets/d679df91-bb13-467c-92da-037d51556bbd)

    
