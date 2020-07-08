mimic_joint_gazebo_tutorial
===========================

I forked this over from [Martin Günther](https://github.com/mintar). I am going to modify to simulate a couple of arms with ray sensors. The arms will be attached to a box and stick straight out. The ray sensors, attached to the end of the arms, will point down into the ground. As the arms move, I want the ray sensors to mimic the arm angle, but in the opposite direction. The end result will be ray senosros that always point straght down into the ground, even as the arms move.  

---

Installation
------------

This repo has the following source dependency. Simply clone it into your catkin workspace:

    git clone https://github.com/roboticsgroup/roboticsgroup_gazebo_plugins.git


I created a catkin workspace specifically for this project, called `mimic_joints_ws`. These are the steps I followed to install: 

- `cd ~`
- `mkdir -p mimic_joints_ws/src`
- `cd mimic_joints_ws/src/`
- `git clone https://github.com/roboticsgroup/roboticsgroup_gazebo_plugins.git`
- `git clone https://github.com/DennisFGardner/mimic_joint_gazebo_tutorial.git`
- `cd ..`
- `catkin build`
- `source devel/setup.bash`
- `sudo apt install ros-melodic-rqt-joint-trajectory-controller`

As you can see in the last bullet point, I needed an additional package. 

Visualize
-------

```bash
roslaunch mimic_joint_gazebo_tutorial show_model_rviz.launch
```

Running
-------

To see the plugin in action, run:

```bash
roslaunch mimic_joint_gazebo_tutorial gazebo.launch
```

You can send command to the arms with the following (as examples): 

```bash
rostopic pub -1 /right_bar_ctrl/command std_msgs/Float64 0.4
```
or 
```bash
rostopic pub -1 /left_bar_ctrl/command std_msgs/Float64 0.4
```

In the examples above, the `0.4` has units of radians. 