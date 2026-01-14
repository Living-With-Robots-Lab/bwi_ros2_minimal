# bwi_ros2_minimal

#### Note: make sure your account is in a 'dialout' group. Contact admin if not sure.

Create a ros2 workspace using:
```
echo 'source /opt/ros/humble/setup.bash' >> ~/.bashrc
mkdir bwi_ros2
cd bwi_ros2
echo 'export COLCON_WS=~/bwi_ros2' >> ~/.bashrc 
source ~/.bashrc
mkdir src
```

## Dependencies Installation:

### Serial:
```
cd ~/bwi_ros2
git clone https://github.com/utexas-bwi/serial.git
```

```
cd serial
mkdir build
cd build
cmake ..
make
```

### Azure_Kinect_ROS_Driver
```
cd ~/bwi_ros2/src
git clone --branch humble https://github.com/microsoft/Azure_Kinect_ROS_Driver.git
```

### ROS2 packages
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/segway_msgs.git
git clone https://github.com/utexas-bwi/bwi_ros2_description.git
git clone https://github.com/utexas-bwi/bwi_ros2_common.git
```
```
cd ~/bwi_ros2/src
mkdir lidar
cd lidar

git clone https://github.com/utexas-bwi/scan_filter.git
git clone --recursive https://github.com/utexas-bwi/urg_node2.git
```
for v4s and v5s:
```
cd ~/bwi_ros2/src/lidar
git clone https://github.com/utexas-bwi/ros2_laser_scan_merger.git
git clone https://github.com/ros-drivers/velodyne.git
```

### (BWIBOTs V2s only) segway drivers:
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/libsegwayrmp_ros2.git
mv libsegwayrmp_ros2/ libsegwayrmp
git clone https://github.com/utexas-bwi/segway_rmp_ros2.git
```

### (BWIBOTs V4s and V5s only) segway drivers:

```
pip install pyserial
cd ~/bwi_ros2/src
git clone https://github.com/Living-With-Robots-Lab/ros2segway.git
```

### other packages:
```
cd ~/bwi_ros2/src
git clone https://github.com/utexas-bwi/convex_decomposition.git
git clone https://github.com/utexas-bwi/ivcon.git
```

### Visit Door list ### 
```
cd ~/bwi_ros2/src
git clone https://github.com/Living-With-Robots-Lab/bwi_tasks.git
```

## Build

```
cd ~/bwi_ros2
rosdep update
rosdep install --from-paths src -y --ignore-src
colcon build
source install/setup.bash
```

if <code>colcon build</code> fails on V2s then try this: <code>pip install --upgrade packaging --user </code>. Build once again.

## Run

### Run the robot
V2s:
```
ros2 launch bwi_launch segbot_v2.launch.py
```
V4s and v5s: use segbot_v4 or segbot_v5 above
### Run the Azure camera drivers 
```
ros2 launch azure_kinect_ros_driver driver.launch.py
```

### Run visit door list
```
ros2 run bwi_tasks visit_door_list
```


