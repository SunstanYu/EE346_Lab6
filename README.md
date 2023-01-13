# EE346_Lab6
LiDAR-Based Navigation with TurtleBot3

Clone source code

```bash
cd ~/catkin_ws/src
git clone git@github.com:SunstanYu/EE346_Lab6.git
```

#### Part 1: **LiDAR-Based Navigation**

In this part, we will create a ROS “action client” node that uses move_base to navigate our robot to any desired position of a given map. Then, modify the script so that our robot can start from P1 and visit P2, P3, and P4 in turn.

1. Connect and start the robot 

   ```bash
   ssh pi@{IP_ADDRESS_OF_RASPBERRY_PI}
   roslaunch turtlebot3_bringup turtlebot3_robot.launch
   ```

2. Open the map generated in lab5

   ```bash
   $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
   ```

3. Use the navigation script to perform navigation

   ```bash
   cd EE346_Lab6/script
   python navigation.py
   ```



#### Part 2: **Parking with the ArUco Marker**

In this part, we will expand the application in Part 1 to allow the robot to park in front of an ArUco marker after visiting the four designated positions. Specifically, upon returning to P1, your robot should look for the ArUco marker (“Original” Dictionary at size 50mm) with the ID of #14 and park in front of it within 10cm in the lane marked with black tapes.

1. Enable the camera of the robot

   ```bash
   roslaunch raspicam_node camerav2_410x308_30fps.launch
   ```

2. Run the arcuco finder to detect aruco

   ```bash
   cd ~/catkin_ws/src/aruco-ros
   roslaunch aruco_marker_finder.launch
   ```

3. Run the park script to adjust the car's position according to the aruco pose dynamically

   ```bash
   cd EE346_Lab6/script
   python park.py
   ```

   
