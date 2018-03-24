# drl_project
Automous driving behavior at intersections with simulaor Gazebo for course Deep Reinforcement Learning
# Installation of Gazebo7 with ROS Indigo

1. Install gazebo from source

sudo apt-get remove '.*gazebo.*' '.*sdformat.*' '.*ignition-math.*' '.*ignition-msgs.*' '.*ignition-transport.*'

sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable lsb_release -cs main" > /etc/apt/sources.list.d/gazebo-stable.list'

wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -

sudo apt-get update

sudo apt-get install ros-$ROS_DISTRO-gazebo7-ros-pkgs

2. Make sure that you succeed with installing gazebo

In terminal:

$ gazebo
You should see a GUI with a empty world.

$ which gzserver
$ which gzclient
You should see:
/usr/local/bin/gzserver
/usr/local/bin/gzclient

3. Install gazebo_ros_pkgs

mkdir -p ~/autonomous_car/src
cd ~/autonomous_car/src
catkin_init_workspace
cd ~/autonomous_car
catkin_make

echo "source ~/autonomous_car/devel/setup.bash" >> ~/.bashrc

sudo apt-get install -y gazebo2

cd ~/autonomous_car/src
git clone https://github.com/ros-simulation/gazebo_ros_pkgs.git -b indigo-devel

(you might need to delete some previous installed gazebo7, choose yes)

rosdep update
rosdep check --from-paths . --ignore-src --rosdistro indigo

rosdep install --from-paths . --ignore-src --rosdistro indigo -y

cd ~/autonomous_cat/
catkin_make

4. Test

source, roscore
source, rosrun gazebo_ros gazebo
(You should see a GUI)

source, rostopic list
(You should see 
/gazebo/link_states
/gazebo/model_states
/gazebo/parameter_descriptions
/gazebo/parameter_updates
/gazebo/set_link_state
/gazebo/set_model_state
)

source, rosservice list
(You should see
/gazebo/apply_body_wrench
/gazebo/apply_joint_effort
/gazebo/clear_body_wrenches
/gazebo/clear_joint_forces
/gazebo/delete_model
/gazebo/get_joint_properties
/gazebo/get_link_properties
/gazebo/get_link_state
/gazebo/get_loggers
/gazebo/get_model_properties
/gazebo/get_model_state
/gazebo/get_physics_properties
/gazebo/get_world_properties
/gazebo/pause_physics
/gazebo/reset_simulation
/gazebo/reset_world
/gazebo/set_joint_properties
/gazebo/set_link_properties
/gazebo/set_link_state
/gazebo/set_logger_level
/gazebo/set_model_configuration
/gazebo/set_model_state
/gazebo/set_parameters
/gazebo/set_physics_properties
/gazebo/spawn_gazebo_model
/gazebo/spawn_sdf_model
/gazebo/spawn_urdf_model
/gazebo/unpause_physics
/rosout/get_loggers
/rosout/set_logger_level
)

Reference:
http://gazebosim.org/tutorials



