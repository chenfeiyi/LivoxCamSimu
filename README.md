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
```bash
    roslauch livox_laser_simulation livox_simulation.launch
```
to see.

Change sensor by change the following lines in the robot.xacro into another xacro file.
```xml
  <xacro:include filename="$(find livox_laser_simulation)/urdf/livox_horizon.xacro"/>
  <Livox_Horizon name="livox" visualize="true" publish_pointcloud_type="2"/>
```
You can change the extrinsic parameters between camera and Livox in file "robot.xacro"
```xml
  <xacro:usb_cam parent="livox_base" xyz="0.1 0.3 0.2" rpy="0 ${M_PI/40} ${M_PI/20}"/>

```
And we supply a Matlab script (src/GtCalc.m) to calculate the convert this xyz and rpy into extrinsic matrix. You need to change
this two line:
```matlab
xyz=[0.1 0.3 0.2]; % parameters in Gazebo
rpy=[0 pi/40 pi/20]; % parameters in Gazebo
```


- avia.csv
- horizon.csv
- mid40.csv
- mid70.csv
- tele.csv

## File Structure

├── include:     "Header files"   
│   └── livox_laser_simulation  
├── launch       "launch files"  
├── meshes       "The 3D model of livox"  
├── resources    "Images for demostration"  
├── rviz         "Rviz configuration files"  
├── scan_mode    "csv files that contains the scanning pattern of Livox"  
├── src          "Plugin source files"  
├── urdf         "Robot and sensors' definition in Gazebo"  
└── worlds       "The world definition in Gazebo"  

## TODO
- Revise this readme
