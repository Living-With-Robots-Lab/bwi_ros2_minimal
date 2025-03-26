# bwi_ros2_minimal

Please create a ros2 workspace using:
```
echo 'source /opt/ros/humble/setup.bash' >> ~/.bashrc
mkdir bwi_ros2 
cd bwi_ros2 
mkdir src
echo 'export COLCON_WS=~/bwi_ros2' >> ~/.bashrc
source ~/.bashrc
```

## Dependencies Installation:

### Serial:
```
cd ~/bwi_ros2
git clone https://github.com/utexas-bwi/serial_for_ros2.git
move 'serial' folder out of the 'serial_for_ros2' package and delete the 'serial_for_ros2' package
cd serial
rm -rf build
mkdir build
cmake ..
make
```

### Azure_Kinect_ROS_Driver
```
cd ~/bwi_ros2/src
git clone --branch humble https://github.com/microsoft/Azure_Kinect_ROS_Driver.git
```

### bwi_ros2_common
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/bwi_ros2_common.git
```

### segway drivers:
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/libsegwayrmp_ros2.git
mv libsegwayrmp_ros2/ libsegwayrmp
git clone https://github.com/utexas-bwi/segway_rmp_ros2.git
```

### other packages:
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/convex_decomposition_ros2.git
mv convex_decomposition_ros2/ convex_decomposition
git clone https://github.com/utexas-bwi/ivcon-ros2.git
mv ivcon-ros2/ ivcon
```
## Build

```
cd ~/bwi_ros2
source install/setup.bash
```

## Run

### Run the robot
```
ros2 launch bwi_lauch segbot_v2.launch.py
```
### Run the Azure camera drivers 
```
ros2 launch azure_kinect_ros_driver driver.launch.py
```

