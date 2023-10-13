# map_loader package

This package provides the features of loading lanelet2 maps onto RViz.

## Dependencies

First clone the following packages into the `src` directory of your ROS2 workspace:
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

## lanelet2_map_loader

### Feature

lanelet2_map_loader loads Lanelet2 file and publishes the map data as autoware_auto_mapping_msgs/HADMapBin message.
The node projects lan/lon coordinates into arbitrary coordinates defined in `/map/map_projector_info` from `map_projection_loader`.
Please see [tier4_autoware_msgs/msg/MapProjectorInfo.msg](https://github.com/tier4/tier4_autoware_msgs/blob/tier4/universe/tier4_map_msgs/msg/MapProjectorInfo.msg) for supported projector types.

### How to run

`ros2 run map_loader lanelet2_map_loader --ros-args -p lanelet2_map_path:=path/to/map.osm`

### Subscribed Topics

- ~input/map_projector_info (tier4_map_msgs/MapProjectorInfo) : Projection type for Autoware

### Published Topics

- ~output/lanelet2_map (autoware_auto_mapping_msgs/HADMapBin) : Binary data of loaded Lanelet2 Map

### Parameters

| Name                   | Type        | Description                                      | Default value |
| :--------------------- | :---------- | :----------------------------------------------- | :------------ |
| center_line_resolution | double      | Define the resolution of the lanelet center line | 5.0           |
| lanelet2_map_path      | std::string | The lanelet2 map path                            | None          |

---

## lanelet2_map_visualization

### Feature

lanelet2_map_visualization visualizes autoware_auto_mapping_msgs/HADMapBin messages into visualization_msgs/MarkerArray.

### How to Run

`ros2 run map_loader lanelet2_map_visualization`

### Subscribed Topics

- ~input/lanelet2_map (autoware_auto_mapping_msgs/HADMapBin) : binary data of Lanelet2 Map

### Published Topics

- ~output/lanelet2_map_marker (visualization_msgs/MarkerArray) : visualization messages for RViz

## Run

To run the whole package, use the provided launch file.

`ros2 launch map_loader lanelet2_map_loader lanelet2_map_path:=path/to/map.osm`