## livox_repub
republish livox raw message to standard pointcloud2


## install

```
mkdir -p ~/catkin_ws_livox_repub/src
cd ~/catkin_ws_livox_repub/src
git clone https://github.com/zzwu29/livox_repub.git
cd ..
catkin_make
```

## config your message in launch file

The default livox_raw_message_name is "/livox/lidar". livox_points_message_name is "/livox/points".

```
<launch>
   <node pkg="livox_repub" type="livox_repub_online_node" name="livox_repub_online_node" output="screen" >
      <param name="livox_raw_message_name"    type="string"   value="/livox/lidar" />
      <param name="livox_points_message_name"    type="string"   value="/livox/points" />
   </node>
</launch>
```

## run

terminal - 1
```
roslaunch livox_repub livox_repub_online.launch
```

## record

terminal - 2
```
rosbag record /livox/points -O YOUR_BAG_NAME.bag
```

## extract to files

.bag to .pcd
```
rosrun pcl_ros bag_to_pcd <input_file.bag> <topic> <output_directory>
```

topic to .pcd
```
rosrun pcl_ros pointcloud_to_pcd input:=/point_cloud_topic _prefix:=./pcd_save_path/
```

## visualize in RVIZ

![](./doc/viz.jpg)


