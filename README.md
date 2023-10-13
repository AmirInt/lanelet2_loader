# lanelet2

This package provides the features of loading lanelet2 maps onto RViz.

## Dependencies

First clone the following packages into the `src` directory of your ROS2 workspace:
- [autoware_auto_msgs](https://github.com/tier4/autoware_auto_msgs)
- [autoware_common](https://github.com/autowarefoundation/autoware_common)
- [minimal_autoware_msgs](https://github.com/AmirInt/minimal_autoware_msgs)
- [minimal_tier4_autoware_msgs](https://github.com/AmirInt/minimal_tier4_autoware_msgs)

Then, from the root of your ROS2 workspace, to install ROS2 and system dependencies, run:
```
rosdep install --from-paths src -y --ignore-src
```

## Build

From the root of your ROS2 workspace, run:
```
colcon build
```

## Run

To run the whole package, use the provided launch file.

`ros2 launch map_loader lanelet2_map_loader lanelet2_map_path:=path/to/map.osm`
