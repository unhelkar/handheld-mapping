# handheld-mapping
A wrapper which allows for handheld mapping using RGBD sensors and the ROS package [rtabmap_ros](http://wiki.ros.org/rtabmap_ros).

## Dependencies
This package requires installation of ROS (version hydro or higher) on an Ubuntu (12.04 or higher) system.

- Install drivers for your RGB-D sensor (Kinect, Xtion, etc.)

- Install [rtabmap_ros](http://wiki.ros.org/rtabmap_ros): 
```
sudo apt-get install ros-InsertVersionNAME-rtabmap ros-InsertVersionNAME-rtabmap-ros
```

- Install [depthimage_to_laserscan](https://github.com/ros-perception/depthimage_to_laserscan): 
```
ros-InsertVersionNAME-depthimage-to-laserscan
```

## Installation

Add this package to `src` folder your catkin workspace, and then execute catkin_make.
```
cd ~/catkin_ws/src
git clone https://github.com/unhelkar/handheld-mapping.git handheld_mapping
cd ..
catkin_make
```

## Usage

- Launch handheld mapping
```
roslaunch handheld_mapping kinect_mapper.launch (To use Kinect)
roslaunch handheld_mapping xtion_mapper.launch (To use Xtion)
```

- (Optional) Launch rviz visualization
```
roslaunch handheld_mapping rviz.launch
```

- Move around the RGB-D sensor gradually in the environment, while ensuring that there are sufficient features in the depth field of the sensor. In case you loose odometry (indicated by red overlay in rtabmap visualization), either try to move to a previous location where you had odometry or if that's not possible reinitialize the mapper.

- Save the map. Note the map will be saved in the directory from which you are executing this command in the terminal.
```
rosrun map_server map_saver map:=/rtabmap/proj_map -f InsertMapName
```