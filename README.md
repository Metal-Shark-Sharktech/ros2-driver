# Advanced Navigation ROS2 Driver - IR Version

## Introduction

This is an example using the Advanced Navigation Spatial SDK to create a ROS2 driver that reads and decodes the Advanced Navigation Packet Protocol (ANPP) (in this case packet #20 and packet #28) and publishes the information as ROS topics / messages. 

This example also includes the encoding of ANPP packet #55 and pushes the information to the Spatial INS.

It is designed to work with all Advanced Navigation INS devices using ANPP.

The code has been written to be easy to understand and for ease of extensibility with other ANPP packets.

This example has been developed and tested using **Ubuntu Linux v20.04 LTS** and **ROS2 Humble**. Installation instructions for ROS2 can be found here: https://index.ros.org/doc/ros2/Installation/Foxy/Linux-Install-Debians/

If you require any assistance using this code, please email support@advancednavigation.com


## Build Instruction

- Packages should be created in the src directory, not the root of the workspace. Navigate to `workspace-folder-name/src`, and get the Advanced Navigation ROS2 Driver   
  ```
  git clone https://github.com/independentrobotics/advanced-navigation-orientus-driver.git
  ```
- You likely already have the `rclpp` and `std_msgs` packages installed as part of your ROS2 system. Either way, it’s good practice to run rosdep in the root of your workspace (`workspace-folder-name`) to check for missing dependencies before building:
  ```
  rosdep install -i --from-path src --rosdistro humble -y
  ```
- In the root of your workspace, `workspace-folder-name`, source and build the package:
  - Source the ROS2 Environment to the current folder:
    ```
    source /opt/ros/humble/setup.bash
    ```
  - Build your new package:
    ```
    colcon build --packages-select advanced-navigation-orientus-driver
    ```

## Device Configuration

To use this example code, your Advanced Navigation device should be configured to output ANPP packets #20 and #28.

If you are not sure how to configure your Advanced Navigation Device please refer to the Reference Manual on the relevant product page (https://www.advancednavigation.com/products/all). 



## Run Instructions

Open a new terminal or new tab, navigate to `workspace-folder-name`, and source the setup files:
```
source ./install/setup.bash
sudo chmod a+rw /dev/tty/USB0
ros2 launch aqua2_launch orientus_imu_launch.py
```
Make sure you ahve aqua2_launch in your src folder

## Published Topics
Use RQT Monitor to view published topics. Here you will find details on how to use RQT: https://index.ros.org/doc/ros2/Tutorials/RQt-Overview-Usage/
- Open a new terminal or new tab and source ROS2 Environment to the current folder:
  ```
  source /opt/ros/humble/setup.bash
  ```
- Run RQT Monitor by entering the following:
  ```
  rqt
  ```
- To view the published messages in RQT Monitor, click **Plugins** and click **Topic Monitor**
