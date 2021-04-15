# ros-params

This repo contains a set of ROS default yaml parameter files to be used with a ROS robot.

Download these yaml files and adjust as needed.

To use the parameter files, make sure your launch file is pointing to the correct location.

## Examples:

### Loading in the base namespace

```xml
<launch>
    <node pkg="amcl" type="amcl" name="amcl" output="screen">
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/amcl.yaml" command="load"/>
    </node>
</launch>
```

### Loading in the node's namespace

note: the common is loaded in to the node's namespace under the namespace of local_costmap and global_costmap.

```xml
<launch>
    <node pkg="move_base" type="move_base" respawn="false" name="move_base" output="screen">
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/costmap_common.yaml" command="load" ns="global_costmap" />
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/costmap_common.yaml" command="load" ns="local_costmap" />
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/local_costmap.yaml" command="load" />
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/global_costmap.yaml" command="load" />
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/local_planner.yaml" command="load" />
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/global_planner.yaml" command="load" />
    </node>
</launch>
```

References:

Those mentioned in the files and [Kaiyu Zheng's ROS Navigation Tuninig Guide](https://kaiyuzheng.me/documents/navguide.pdf)
