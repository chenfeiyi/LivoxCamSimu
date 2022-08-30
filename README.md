# Livox Camera Simulation
This is a ros package for sensor simulation for cameras and lidar. This repo is built based on the [livox simulator](https://github.com/lvfengchi/livox_laser_simulation). 

## Requirements
### gazebo9
- enviroment: ROS melodic + gazebo7
- pointcloud type: sensor_msg::pointcloud2(pcl::Pointcloud\<pcl::PointXYZ\>)

## Dependence

- [livox_ros_driver](https://github.com/Livox-SDK/livox_ros_driver)

## Usage

Run 
```
    roslauch livox_laser_simulation livox_simulation.launch
```
to see.

Change sensor by change the following lines in the robot.xacro into another xacro file.
```xml
  <xacro:include filename="$(find livox_laser_simulation)/urdf/livox_horizon.xacro"/>
  <Livox_Horizon name="livox" visualize="true" publish_pointcloud_type="2"/>
```

- avia.csv
- horizon.csv
- mid40.csv
- mid70.csv
- tele.csv
