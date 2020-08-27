# ati_sensor_description

### Overview

Description and simulation of ATI sensors, merged description of descriptions available at 

* *https://github.com/CentroEPiaggio/force-torque-sensor/tree/master/model*
* *https://github.com/iirob/ati_force_torque*
 
with included modularity through a yaml file for easy parameter tuning (adapter plate thickness for instance) or adding new sensors

### Output

A Wrench is produced, relatively to the *top plate* of the sensor (*ft_tool_link*) on the topic */ft_sensor* at a rate of 100 Hz by default

### Settings

The urdf macros are designed to load models defined in the sensor_types.yaml, and passing some other parameters, even overriding some of them.

* **prefix**: the prefix used in front of ft_sensor in names and as namespace
* **child**: frame of the tool to be attached to the ATI if provided (tool frame of ati will be statically linked to this child)
* **model**: (default to 'gamma'): name of the yaml parameters to load
* **interface_height**: thickness of the interface between the robot and the ati sensor. If given (and not '-'), value is added to the bare height of the sensor, without the standard flat plate
* **sim** (default to false): adds a gazebo FT plugin if true
* **rate** (default to 100): rate of update of the gazebo plugin

### Usage

There is a standalone example (can be directly spawned in gazebo), attached to the world, which shows how to instantiate the macro

```
xacro `rospack find ati_sensor_description`/robots/sensor.urdf.xacro sim:=true > /tmp/sensor.urdf
roslaunch gazebo_ros empty_world.launch
rosrun gazebo_ros spawn_model -urdf -file /tmp/sensor.urdf -model sensor
```

