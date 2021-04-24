# ros-params

This repo contains a set of ROS default yaml parameter files to be used with a ROS robot. The intent is to include all options, their defaults, and the description of the options to make it easier to see the options that are available. In some cases the standard default is replaced by recommendations made from reputable sources.

Download these yaml files and adjust as needed. You can use clone this repo, download or use wget to pull the files you need. Example: `wget https://raw.githubusercontent.com/brannonvann/ros-params/master/move_base.yaml`

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
        <rosparam file="$(find PACKAGE_NAME_HERE)/params/move_base.yaml" command="load" />
    </node>
</launch>
```

## References

Much of the text comes directly from the documentation available at ros.org for each package. Other sources are mentioned in the files. I also referenced [Kaiyu Zheng's ROS Navigation Tuninig Guide](https://kaiyuzheng.me/documents/navguide.pdf).
