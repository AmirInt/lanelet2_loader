# lanelet2

Tools for loading lanelet2 maps onto RViz.

## Dependencies

- [autoware_auto_msgs](https://github.com/AmirInt/autoware_auto_msgs)
- [autoware_adapi_msgs](https://github.com/AmirInt/autoware_adapi_msgs)
- [autoware_common](https://github.com/AmirInt/autoware_common)
- [minimal_autoware_msgs](https://github.com/AmirInt/minimal_autoware_msgs)
- [minimal_tier4_autoware_msgs](https://github.com/AmirInt/minimal_tier4_autoware_msgs)


## Build

Clone the dependency packages into the `src` directory of your ROS2 workspace.

Then, from the root of your ROS2 workspace, to install ROS2 and system dependencies, run (ensure you have previously installed and initialised [rosdep](https://docs.ros.org/en/humble/Tutorials/Intermediate/Rosdep.html#how-do-i-use-the-rosdep-tool)):
```
rosdep install --from-paths src -y --ignore-src
```

Finally, build via:
```
colcon build
```

## Run

Source your ROS2 workspace.

Use the following command.

`ros2 run map_loader lanelet2_map_loader --ros-args -p lanelet2_map_path:=path/to/map.osm`
