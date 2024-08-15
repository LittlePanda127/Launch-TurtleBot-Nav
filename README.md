**Launch TurtleBot Navigation**
This guide provides detailed steps to install the TurtleBot packages, set up a simulation environment, create a map, and launch navigation for TurtleBot.

**Prerequisites**
Ensure you have the following installed:
1-Ubuntu 20.04
2-ROS Neotic

****Installation Steps****
1.Install turtlebot Packages:
Open a terminal and execute the following commands to install TurtleBot packages:
sudo apt-get update
sudo apt-get install ros-noetic-turtlebot3

2.Install Turtlebot simulation packages:
sudo apt-get install ros-noetic-turtlebot3-simulations
![image](https://github.com/user-attachments/assets/c57cbf67-c668-4775-8c78-63972da3d638)

3.Set up environment variables
Add the TurtleBot model to your environment variables. Append the following lines to your ~/.bashrc file:\
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
source ~/.bashrc
![image](https://github.com/user-attachments/assets/c450fec3-4a3f-43f6-a0a5-a837bfda545d)

4.Create a Map and Launch Navigation
4.1 Launch the TurtleBot World Start by launching the TurtleBot world in Gazebo:
roslaunch turtlebot3_gazebo turtlebot3_world.launch
![image](https://github.com/user-attachments/assets/dc932487-a8ca-4f55-be22-9ab9817264cc)

4.2 Launch SLAM for Mapping To create a map using SLAM (Simultaneous Localization and Mapping), run:
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
![image](https://github.com/user-attachments/assets/c52169c4-d564-4d2f-b5e9-cfe3cf8580c2)

You can save the map by running:
rosrun map_server map_saver -f ~/map

4.3 Launch Navigation Finally, launch the navigation stack:
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml

![image](https://github.com/user-attachments/assets/3ffc2c30-8ce0-424b-8813-fecddf98ecb5)



**Additional Dependencies**
Ensure all dependencies are installed. If not, you can install them using the following commands:

sudo apt-get install ros-noetic-navigation
sudo apt-get install ros-noetic-slam-gmapping

**Troubleshooting**
If you encounter issues with missing dependencies, use rosdep to install them:
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -r -y
![image](https://github.com/user-attachments/assets/f7815c33-e67e-4a7d-b528-d8b6b9d2be4b)
![image](https://github.com/user-attachments/assets/53968d70-5c4f-4efc-a25b-450339c86753)


Ensure all necessary environment variables are correctly set by sourcing your .'bashrc':
source ~/.bashrc

